# Notes on 3d printing parts for 2FP PUMA microscope

james
2024-07-11

Extra parts:
"I advise that you print yourself a spare monocular tube just in case that happens while you are out in the field - since you don't have much time to get used to using the scope and it would be a shame to be unable to use it if that happens. The model is: MN_Monocular_tube_c_adhesin as seen on page 189 of the 3D printing guide on GitHub - you will need to ensure the lumen is clear after you print it as I describe in my videos."


(base) jamesh@vidar:~/Desktop/PUMA_microscope$ 

    git clone https://github.com/TadPath/PUMA.git

    wget https://github.com/FreeCAD/FreeCAD/releases/download/0.21.2/FreeCAD-0.21.2-Linux-x86_64.AppImage
    chmod +x FreeCAD-0.21.2-Linux-x86_64.AppImage
    ./FreeCAD-0.21.2-Linux-x86_64.AppImage

See `3D_Printing/PUMA_3D_Printing_Guide.pdf`

Install https://wiki.freecadweb.org/Fasteners_Workbench

Follow instructions in "Generating the STL Mesh Files"
    1) Open in freecad 0.21: `/home/jamesh/Desktop/PUMA_microscope/PUMA/FreeCAD/Monocular.FCStd`
    2) mesh in menu selector
    3) select Monocular_tube_c_adhesin
    4) Go to 'Meshes' -> 'Create mesh from shape ...' 
    5) Select the 'Standard' meshing option set the 'surface deviation' to 0.001 mm and the 'Angular deviation' to 1 degree.
    6) OK
    7) right click on the mesh in the 'Model' tab of the combo view and select 'Export Mesh ...' 
    
Save as MN_Monocular_tube_c_adhesin.stl

From See `3D_Printing/PUMA_3D_Printing_Guide.pdf`

    Monocular Head
    These are the parts for the monocular viewing head of the microscope. Some of the
    parts here are also used for the binocular and trinocular head modules. The CAD
    source models for these STL files are found in the file Monocular.FCStd.
    For tubular structures (including the monocular tubes and projection cone) use the
    ‘Flats’ profile but modify it thus: use a 'Zig-Zag' infill pattern - it is quicker due to fewer
    stop-start retracts on the nozzle (16% of total time spent on retractions compared to
    40% for the default cubic infill pattern, for the monocular tube model). Also use the
    'concentric' 'Top/bottom' pattern.

defualt profile: /home/jamesh/Desktop/PUMA_microscope/PUMA/3D_Printing/CE3_Cura/Flats.curaprofile

open in Ultimaker CURA

    Layer height: 0.16mm
    Initial layer h: 0.12mm
    all Line w: 0.4mm

    Wall thickness 1.2mm
    Wall line count 3
    Top/bot thickness 1.08mm (7x 0.4 is 1.12?)
    Top/bot layers 7
    top/bot pattern lines (change to concentric) 

    20% infill
    cubic (change to 'Zig-Zag')

    no support
    no adhesion

Modified to a profile in snapmaker luban 4.1.3

Changed after 1st printing to retract at layer change and reduce outer layer speed from 30 to 20 to reduce bumps. OK print qual. 

saved: Flats.snapmakerprofile.json
