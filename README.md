# Ringo WorldStarr

A looping, walkable level where everything around you is a math function running on the GPU. You walk inside a giant torus that pulses, twists and shifts hues in a psychedelic loop, built from up to half a million cubes animated in real time with HLSL compute shaders.

Video: https://www.youtube.com/watch?v=rCbEeZmJZns
Portfolio write-up: https://ergosoom.com/game-dev#ringo

## What's in it

- **GPU-driven points:** point positions are calculated in a compute shader and stored in a compute buffer, then drawn procedurally, so hundreds of thousands of cubes animate at high framerates on modest hardware.
- **Original math functions:** 6 parametric functions (5 torus variations and a sphere), animated with time and morphing into each other.
- **Walkable scale:** a custom scale parameter takes the graph from a -1 to 1 domain up to a level you walk through in first person.
- **Animated world-space color:** each cube is colored by its position in the world, with the rainbow shifting over time.

## Running it

1. Open the project in **Unity 2020.3.49f1** (Universal Render Pipeline).
2. Open the scene `Assets/Ringo.unity` and press Play.
3. Walk with WASD and look around with the mouse.

## Key files

| File | What it does |
| --- | --- |
| `Assets/Scripts/FunctionLibrary.compute` | Compute shader kernels with the math functions and the transitions between them |
| `Assets/Scripts/GPUGraph.cs` | Sets up the compute buffer, dispatches the kernels, and cycles through functions |
| `Assets/Scripts/FunctionLibrary.cs` | Function list used by the graph |
| `Assets/Point/PointGPU.hlsl` | Reads positions from the buffer when drawing each cube |
| `Assets/Point/Point URP GPU.shadergraph` | Shader graph for the cubes, including the animated world-space color |

## Credits

- Built on top of Jasper Flick's [Catlike Coding](https://catlikecoding.com/unity/tutorials/basics/) Basics tutorials (Mathematical Surfaces, Compute Shaders), extended with original functions, scale and animated color.
- First-person movement uses the Modular First Person Controller asset.

Made by Somar Jaafar as part of an independent study in visual shader authoring at Concordia University (Winter 2026).
