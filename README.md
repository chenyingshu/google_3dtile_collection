# Google 3D Tiles Collection
Use Google Tile API to download models in [3D tiles]() to Blender and export as obj file with texture.

By using Google 3D Tiles you are bound by
- [Google’s Terms of Service](http://www.google.com/intl/en/policies/terms)
- [Google Maps Platform Terms of Service](https://cloud.google.com/maps-platform/terms)
- [Google Privacy Policy](http://www.google.com/policies/privacy)


<!--## Table of Contents-->

## References
We refer to the instructions and scripts from and acknowledge the contribution of:
- Import Google 3D tiles to Blender: https://github.com/vvoovv/blosm/wiki/Import-of-Google-3D-Cities.
- Merge many texture files into one for an obj file: https://github.com/theFroh/imagepacker.

## Requirements
- Python
- [Blender](https://www.blender.org/) (latest version)
- Blender Addon [Blosm](https://prochitecture.gumroad.com/l/blender-osm)  (base version)
- Google 3D Tiles API Key

## Instructions
- [Import Tiles to Blender](#import-tiles-to-blender)
- [Merge Multi-Texture into One](#merge-multi-texture-into-one)
### Import Tiles to Blender
For detailed instructions, you can follow https://github.com/vvoovv/blosm/wiki/Import-of-Google-3D-Cities.

Steps:
#### Preparation
1. Install [Blender](https://www.blender.org/) 
2. Install [Blosm Addon (base version)](https://prochitecture.gumroad.com/l/blender-osm)  
3. Get Google 3D Tiles Key [[link]](https://developers.google.com/maps/documentation/tile/get-api-key).
    1. Do not apply any restrictions to your 3D Tiles Key.
    2. Enter key to "Google 3D Tiles Key" Blosm addon preference.
4. Enable the Maps Tiles API [[link]](https://developers.google.com/maps/documentation/tile/cloud-setup#enabling-apis).

#### Import and Export Model
We refer to 
1. Create a new empty Blender project, enable Blosm addon, and restart Blender (if first time enable addon).
2. Enter "Directory to store downloaded OpenStreetMap and terrain file" in Blosm addon preference.
3. (Refer to [Basic Usage](https://github.com/vvoovv/blosm/wiki/Import-of-Google-3D-Cities#basic-usage))
In project "Layout" tab, open "Blosm" menu UI on the right side panel of the Blender (or toggle by click ``N`` key).
5. Click `Select`, and open web-based UI to select area by bounding box, I use no more than 0.3km x 0.3km area for quicker download.
6. Copy on Web and paste on Blosm UI panel longitudes and latitudes.
   
### Merge Multi-Texture into One
Merge texture images into one, please follow https://github.com/theFroh/imagepacker.
For example, run: <br>
``
python
``

To use one sole material in obj file, we need to edit obj file by running: <br>
``
python
``
