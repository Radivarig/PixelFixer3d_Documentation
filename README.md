# Pixel Fixer 3d

## Description
`Pixel Fixer 3d` is a shaderless solution for pixelating 3d scenes with pixel creep reduction for orthographic camera.  
It provides the base for creating Pixel Art style games with 3d models.  

[WebGL Demo](https://radivarig.github.io/PixelFixer3d_URP_WebGL)  
[Asset Store](https://assetstore.unity.com/packages/slug/243562)  
[Discord Server](https://discord.com/invite/Y9SFDvf6)  
[Setup](https://github.com/Radivarig/PixelFixed3d_Docs-And-Issue-Tracker/blob/main/Setup.md)

Render pipelines
- Built-in ✓
- URP ✓
- HDRP ✗ (on the roadmap)

## Shaderless
Requires no special shaders so you can keep your existing materials.

## Pixelization
Achieved by rendering to a lower resolution render texture and upscaling to fit the screen.

## Pixel Creep reduction
Camera and tagged objects are snapped to a grid of world space pixel size resulting in the same pixel colors being rendered while moving.

## Stabilization
Snapping to pixel size grid makes the camera shake so subpixel offset is applied in the game resolution based on the snap position difference.

## UI
Includes scripts for making canvas elements follow a world transform.
Includes examples for having a higher resolution text than the pixelized texture.
Includes an option to fully pixelate a world space canvas (update soon to be published).

## How the asset works
1. Camera gets snapped to a grid of size of a pixel in world space which makes pixel colors consistent but shows a zig-zag movement.  
1. Zig-zag is smoothed out with offseting the upscaled image for the difference from the original camera position.  
1. This makes the scene stable for non moving objects so for moving objects a Snappable script is provided.  

## Performance
Performance difference is rendering to screen vs. rendering to a texture and a second camera rendering that texture.  
If your original render is heavy you might even get a performance gain since only a part (25% or less) of the pixels are rendered.  

Finding Snappables is cached and not executed every frame.  

## UI
- Canvas will use original resolution so fonts need texture change to Point filtering (instructions provided)
- Contains scripts to:
  - Make canvas elements follow world positions
  - Auto set a font and its size in the scene

## Tested versions
- Unity 2021.3.x, URP 12.x

## To be noted
- Rotation will always have some pixel creep but it's less noticeable with higher rotation speed.  
- Zig-zag will occur for all snapped moving objects, but is less noticeable with higher movement speed.  
- Resolution must be set and be divisible with pixelMultiplier.  

## In progress/research
- [HDRP] targetTexture with lower resolution does not render full screen rect
- [Built-in] WebGL targetTexture goes black on fullscreen
- Skinned mesh hierarchy snapping after animation
- Ocassional pixel flicker on alpha clipped textures or geometry edges

For any questions contact me at reslav.hollos@gmail.com.  
