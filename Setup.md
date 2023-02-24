# Pixel Fixer 3d
Thank you for purchasing PixelFixer3d!  

# Setup
- Drag the `PixelFixer3d.prefab` into the scene and you should immediatelly see the pixelated effect
- Set a resolution (ex. 1920x1080) that is a multiple of a chosen `PixelFixer3d.pixelMultiplier` number
- [Built-in] Move `PostProcessLayer` and `PostProcessVolume` from MainCamera to the PixelFixer3d gameObject

# Fine tuning
- Set texture's filtering to Point
- Set texture's MipMaps to Off
- Lower texture's resolution
- Increase shadow resolution
- Disable anti-aliasing on main camera
- [Built-in] Set `Quality > Shadow Projection: Stable Fit`

# UI
- To have Canvas elements follow a transform, parent them under that transform and attach `WorldPositionUI.cs`
  - They will automatically be placed under Canvas in Play-Mode

# Legacy text font resolution:
  - Set font rendering mode to `Hinted Raster` and character to `ASCII default set`
  - Click `Tripple dot icon (upper right) > Create Editable Copy`
  - Set copied font's texture filtering to Point and lower the resolution
  - Use `GlobalSetFont.cs` with the copied font to update all Text components in the scene

# Demo scene
- Demo scene is included under examples
- To update materials for URP:
  - Convert by standard `Window > Rendering > Render Pipeline Converter`
  - Go into prefabs for `RobotFace` and `Fence` and update to '_URP' postfixed material
- If you are interested in the assets better download directly from package manager
- Assets contained:
  - 'Unity Technologies > 3d Game Kit' character with modified scripts
  - 'Unity Technologies > AR Face Assets' texture and modified mesh

# Contact
If you have any questions or feedback, please contact me at reslav.hollos@gmail.com.  
If you like the asset, I would appreciate it if you'd rate it!  
