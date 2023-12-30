# Google 3D Tiles Collection
Use Google Tile API to download models in [3D tiles](https://developers.google.com/maps/documentation/tile/3d-tiles) to Blender and export as an OBJ file with texture.

By using Google 3D Tiles you are bound by
- [Google’s Terms of Service](http://www.google.com/intl/en/policies/terms)
- [Google Maps Platform Terms of Service](https://cloud.google.com/maps-platform/terms)
- [Google Privacy Policy](http://www.google.com/policies/privacy)


<!--## Table of Contents-->

## References
We refer to the instructions and scripts from and acknowledge the contribution of:
- Import Google 3D tiles to Blender: https://github.com/vvoovv/blosm/wiki/Import-of-Google-3D-Cities.
- Merge many texture files into one for an OBJ file: https://github.com/theFroh/imagepacker.

## Requirements
- Python, Pillow
- [Blender](https://www.blender.org/) (latest version)
- Blender Addon [Blosm](https://prochitecture.gumroad.com/l/blender-osm)  (base version)
- Google 3D Tiles API Key

## Instructions
- [Import Tiles to Blender](#import-tiles-to-blender)
- [Merge Multi-Texture into One](#merge-multi-texture-into-one)
### Import Tiles to Blender
For detailed instructions, you can follow https://github.com/vvoovv/blosm/wiki/Import-of-Google-3D-Cities.

#### STEP 1 - Preparation
1. Install [Blender](https://www.blender.org/) 
2. Install [Blosm Addon (base version)](https://prochitecture.gumroad.com/l/blender-osm)  
3. Get Google 3D Tiles Key [[link]](https://developers.google.com/maps/documentation/tile/get-api-key).
    1. Do not apply any restrictions to your 3D Tiles Key.
    2. Enter key to "Google 3D Tiles Key" Blosm addon preference.
4. Enable the Maps Tiles API [[link]](https://developers.google.com/maps/documentation/tile/cloud-setup#enabling-apis).

#### STEP 2 - Import and Export Model
1. Create a new empty Blender project, enable Blosm addon, and restart Blender (if first time enable addon).
2. Enter "Directory to store downloaded OpenStreetMap and terrain file" in Blosm addon preference.
3. (Refer to [Basic Usage](https://github.com/vvoovv/blosm/wiki/Import-of-Google-3D-Cities#basic-usage))
In project "Layout" tab, open "Blosm" menu UI on the right side panel of the Blender (or toggle by click ``N`` key).
4. Click `Select`, and open web-based UI to select area by bounding box, I use 0.3km x 0.3km to 1.0km x 1.0km area for quicker download.
5. Click `copy` from Web and `paste` on Blosm UI panel to paste longitudes and latitudes.
6. Settings:
    - Import: `Google 3D Tiles`
    - Level of details: `buildings with more details`
    - [ ] Join 3D Tiles objects
    - [x] Relative to initial import
   <br>Disable "Join 3D Tiles objects" for later mesh editing.
7. Click `import` and wait, we can open terminal to monitor the downloading progress.
8. Repeat sub-steps 3-7 to get other aligned tiles.
9. To better view the model online, on the right View panel, set _View > (Clip) End to 10000m_.

#### STEP 3 - Export OBJ Model
1. Usually downloaded tiles cover larger/unexpected area then selected area, please feel free to delete useless tiles.
2. Change materials: select imported meshes, in Blosm *Tools >Replace materials with* `export-ready`, click `Replace Materials`.
3. Export and save textures: _Main Menu > File > External Data > Unpack Resources_, in the popup-window
   - Select "Write files to current directory (overwrite existing files)"; OR
   - For Windows, select "Use files in current directory (create when necessary)"
   - For Linux/Ubuntu, select "Use files in original location (create when necessary)"
       - There appears duplicate naming in unpacking issue in some Linux Blender.
5. Select necessary tile meshes.
6. [OPTIONAL] Recommended for some renderer that supports only one mesh, or small-scale model.
   - Press "Ctrl+J" to merge tile meshes into one.
   - Rescale the mesh with 0.1 ratio to scale down model size.
7. _Main Menu > File > Export > Waterfront (.obj)_, in popup-window check _Limit to Selected Only_.
8. Click `Export Waterfront OBJ` to export textured obj file.
 
### Merge Multi-Texture into One
#### STEP 4 - Pack Textures into One
Merge texture images into one and use only one material, please run: <br>
``python objuvpacker.py [path\_to\_obj\_file.obj] -m [path\_to\_material\_file.mtl] -o [output\_path\_name]
``
<br>
For example,
``
python imagepacker/objuvpacker.py XXX.obj
``

To preserve original multiple materials in obj file by running: <br>
``
python imagepacker/objuvpacker.py XXX.obj --multi-mtl
``

Code was adapted from https://github.com/theFroh/imagepacker.
