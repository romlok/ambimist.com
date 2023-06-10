## Procedural planets in Godot 3

(Note: The project was created in the time of Godot 3, but this writeup was written in a Godot 4 era, so Godot-specific terminology may be inconsistent between the versions)

After experiencing a craving to return to [Shores of Hazeron](https://hazeron.com) and finding that it was no longer active, my first instinct was of course to think about how I would go about making something similar, and what I would do differently.

Having lived for some time within the Arctic circle, one thing that bugged me about Hazeon was that its planetary terrain used a mesh based on meridians and parallels - lines of latitude and longitude.  This appears to be the most common way of representing spheres as meshes in 3D tools, but means that mesh faces get narrower and narrower toward the poles, resulting in procedural terrain becoming ever more sharp and jagged and, in the context of Hazeron, too narrow to build on.

<!-- TODO: Get screenshot of Hazeron poles here? -->

### Everyone's second favourite platonic solid

Thus I began thinking about how one could construct a procedural world of arbitrary size, with consistent level of detail across the entire surface.

The answer was fairly simple; start with a simple platonic solid, and subdivide it to whatever level of detail is desired.  The most obvious starting point for me was an icosahedron, aka a d20.  Its faces are all equilateral triangles, and can thus be subdivided into four similarly equilateral sub-faces, recursively, until the desired level of detail is achieved.

### Generating terrain

Going from a subdivided icosahedron to a more sperical [icosphere](https://en.wikipedia.org/wiki/Icosphere) is as simple as `normalize()`ing each vertex.  This then gives us a uniform base to apply a planet's heightmap.

<!-- TODO: Show us an icosphere -->

Not being a stranger to procedural generation, to create the heightmap I headed straight to Godot's [`OpenSimplexNoise`[(https://docs.godotengine.org/en/3.4/classes/class_opensimplexnoise.html) class to generate values at arbitrary points in 3D space.  These values were then used to offset the icosphere's vertices, which allowed an undulating and continuous terrain to an arbitrary level of detail.

### Chunky goodness

Because my objective was a procedural world with seamless transitions from standing on the surface to [a blue marble](https://en.wikipedia.org/wiki/The_Blue_Marble) and beyond, a single mesh for an entire planet
wouldn't cut it.  I instead broke the icosahedron into "chunks", each containing the mesh for a single primary face, subdivided however many times necessary.

<!-- TODO: Screenshot of a chunk pls -->

While suitable for rendering worlds at a distance, for surface-level exploration these chunks are clearly still far too large, and lacking detail.  Thus the chunks themselves would need to be subdivided even further as the player got close.

To implement this, I created spherical `Area3D` colliders around the player, each representing a level of detail (LOD) distance.  Each LOD sphere was also given a "face size" parameter which, when the sphere collided with a chunk, informed that chunk how much subdivision was required.

Thus, as the player approached a chunk, the outermost LOD sphere would trigger a subdivision of the primary chunk into somewhat smaller chunks.  As the player even gets closer, the next LOD sphere detects these smaller chunks, and triggers a further subdivision into even smaller chunks.  And so on until the player reaches the surface inside the smallest LOD sphere.

Conversely, as the player moves away from a chunk, an `area_exited` is triggered and the smallest chunks are destroyed, with the next larger LOD chunks making a reappearance in their wake.

<!-- TODO: Video of flying over terrain, holes and all -->

### Filling a hole

The most striking flaw in this arrangement was in the edges between chunk sizes.  The procedural generation ensured that vertices on adjacent chunks  would connect seamlessly, however at the edge of an LOD sphere, further chunks have fewer vertices than closer ones.  This means that there is a disconnect between LODs, especially in steep terrain, where there is a gap between the meshes through which the skybox is visible!

One could try to solve this with "border" chunks, where a chunk mesh can be a combination of a higher-LOD edges and lower-LOD edges, depending on its visible neighbour chunks.  However, that sounded complicated, so I chose to solve it in a far simpler manner - flanges.

I chose to add tall vertical faces to the outside edge of every chunk, so that they formed a skirt around the perimiter, turning each chunk effectively into a tall column that stretched deep into the planet.

To prevent these visible flanges looking like sheer cliffs, each surface face on the perimiter of a chunk had its own vertical section (two triangles) of the flange, which adopted the same normal as the surface face itself.  This meant that, for shading purposes, the flange would be rendered with the same lighting as the surface faces.

<!-- TODO: A picture of a chunk with flanges would help here -->

### A terrestrial twin

While a dynamically subdividing, undulating icosphere is technically impressive (at least to me), a solid green lump doesn't feel very planet-y.  So my next step was to add some variation in the surface.

Firstly, I added a sea.  This was merely an additional mesh layer for each chunk, which didn't have the procedural height map applied to it.  With an appropriate texture, this produces a global sea at the average terrain height.

With the water in place, the next step was to give any surface face which was partly or mostly underwater a yellow sand texture.

Then, since you can't have a terrestrial twin without snow-capped mountains, so any surface face above a particular (arbitrary) height was turned white.

Finally, for the heck of it, any surface face steeper than a certain (arbitrary) angle was textured as rock - on the basis that it's too steep for either soil, sand, or snow to settle.

<!-- TODO: Cool biome-y video here -->

I also started experimenting with texture shaders, to make water look a bit more watery.

<!-- TODO: Cool water video in here pls -->

Tinkering with the various values and algorithms which determined these biomes became something of a theme throughout development from this point, since I was never really able to get any of it looking quite to my satisfaction!

### To boldy go

When your inspiration is an intergalactic sandbox, and you have a single procedural planet, the most obvious next step is to reach further out into the solar system.

However, Godot uses 32-bit values for `Vector3`, which is fine for the scale of most games, but when wanting to simultaneously render both the ground at your feet, and planetary bodies millions of kilometers away, you start facing issues of floating point precision.  One can compile Godot with 64-bit float support, which can handle solar-system-scales with millimetre precision, but this only became fully implemented engine-wide in Godot 4, so alternative workarounds were required.

#### Distant impostors

<!-- TODO: Chunks get jiggy at a distance -->

#### Floating origin

<!-- TODO: *I* get jiggy at a distance -->

### I am the centre of the universe

<!-- TODO: Sun -->

### Not because it is easy

<!-- TODO: Moon! -->
