# Pixel Fixer 3d

## Description
`Pixel Fixer 3d` is a shaderless solution for pixelating 3d scenes with pixel creep reduction for orthographic camera.  
It gives smooth camera panning for non moving objects with optional transform snapping for moving objects.  

Play the [WebGL demo](https://radivarig.github.io/PixelFixer3d_URP_WebGL). Demo scene is included.  
Check the [Setup](https://github.com/Radivarig/PixelFixed3d_Docs-And-Issue-Tracker/blob/main/Setup.md) for fine tuning.  
Get the asset [here](https://assetstore.unity.com/packages/slug/243562).  

## Shaderless
Requires no special shaders so you can keep existing materials.  

## Render pipelines
- Built-in ✓
- URP ✓

## Pixel Creep
Image upscaling makes the pixels stand out but also makes a visual artifact of pixel flickering (pixel creep) more perceivable.  
For each pixel representing an object there are more parts of that object that ended up between the pixels and not visible, so slight movements of either the camera or transforms (position/rotation/scale) will render different color each frame which makes flickering.  

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
- [Built-in] Post-processing not applied to targetTexture
- [HDRP] targetTexture with lower resolution does not render full screen rect
- [Built-in] WebGL targetTexture goes black on fullscreen
- Skinned mesh hierarchy snapping after animation
- Automate setting global mipmaps, filtering etc.
- Ocassional pixel flicker on alpha clipped textures or geometry edges
- [URP] requires either depth or opaque textures enabled or it culls the scene

For any questions contact me at reslav.hollos@gmail.com.  
