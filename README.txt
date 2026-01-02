
================================================================================
                        CONFIGURATION GUIDE (config.lua)
================================================================================

--------------------------------------------------------------------------------
FRAMEWORK SELECTION (Line 3)
--------------------------------------------------------------------------------

Config.Framework = 'esx'

Change this to match your server's framework: 'standalone', 'esx', or 'qbcore'.

If you don't use ESX or QBCore, leave it as 'standalone' - the script will work for everyone on your server.



--------------------------------------------------------------------------------
UI KEYBIND (Line 7)
--------------------------------------------------------------------------------

Config.UIKeybind = 'E'

This is the key players press to open the monitoring station interface when standing at the marker.

You can change 'E' to any other key if needed.

--------------------------------------------------------------------------------
MONITORING STATION LOCATION (Lines 9-16)
--------------------------------------------------------------------------------

Config.MonitoringStation = {
    coords = vector3(441.05, -978.72, 30.69),
    markerType = 27,
    markerSize = { x = 1.5, y = 1.5, z = 1.0 },
    markerColor = { r = 0, g = 100, b = 255, a = 100 },
    drawDistance = 10.0,
    interactionDistance = 2.0
}

The "coords" line sets where the monitoring station marker appears (default is Mission Row Police Station).

To change the location, replace the coordinates with your desired location (use /getcoords or similar commands in-game).

The markerColor values are Red, Green, Blue, and Alpha (transparency) - adjust these to change the marker's appearance.

--------------------------------------------------------------------------------
POLICE JOBS (Lines 18-21)
--------------------------------------------------------------------------------

Config.PoliceJobs = {
    'police',
    'sheriff'
}

Add or remove job names here to control which jobs can access the camera system.

If using standalone mode, everyone can access cameras regardless of this setting.

For ESX/QBCore, only players with these job names will see the monitoring station marker and access cameras.

--------------------------------------------------------------------------------
VIEW CAMERA PERMISSIONS (Lines 23-26)
--------------------------------------------------------------------------------

Config.ViewCamerasGrades = {
    ['police'] = { 0, 1, 2, 3, 4, 5, 6, 7 },
    ['sheriff'] = { 0, 1, 2, 3, 4, 5, 6, 7 },
}

These numbers represent job grades that can VIEW cameras (but not manage them).

Example: If you only want officers grade 2 and above to view cameras, change it to { 2, 3, 4, 5, 6, 7 }.

In standalone mode, this setting is ignored and everyone can view cameras.

--------------------------------------------------------------------------------
MANAGE CAMERA PERMISSIONS (Lines 28-31)
--------------------------------------------------------------------------------

Config.ManageCamerasGrades = {
    ['police'] = { 3, 4, 5, 6, 7 },
    ['sheriff'] = { 3, 4, 5, 6, 7 },
}

These grades can place, rename, edit, and delete cameras (usually sergeants and above).

Example: Only allow captains (grade 5+) to manage cameras: { 5, 6, 7 }.

In standalone mode, everyone can manage cameras.

--------------------------------------------------------------------------------
CAMERA OBJECT MODEL (Line 33)
--------------------------------------------------------------------------------

Config.CameraObject = 'prop_cctv_cam_01a'

This is the 3D prop that appears in the world when you place a camera.

You can change this to any other CCTV camera prop if you prefer a different look (examples: 'prop_cctv_cam_02a', 'prop_cctv_cam_03a', etc).

--------------------------------------------------------------------------------
CAMERA CONTROLS (Lines 34-38)
--------------------------------------------------------------------------------

Config.CameraRotationSpeed = 0.0
Config.CameraRotationRange = 90
Config.ManualRotationSpeed = 0.5
Config.ManualTiltRange = { min = -30, max = 30 }
Config.ManualPanRange = { min = -45, max = 45 }

These control how cameras move when viewing them - you can adjust the speed and range limits for camera pan/tilt movements.

Most users can leave these at default values.

--------------------------------------------------------------------------------
PLACEMENT COMMAND (Lines 49-51)
--------------------------------------------------------------------------------

Config.PlacementCommand = 'nycm'
Config.PlacementHeight = 3.0
Config.MaxCameras = 50

The "PlacementCommand" is what players type to start placing a camera (default: /nycm).

"PlacementHeight" is how high above ground the camera starts when placing (3.0 meters default).

"MaxCameras" limits how many cameras can exist on your server (default 50, increase if needed).

--------------------------------------------------------------------------------
CAMERA SETTINGS (Lines 53-58)
--------------------------------------------------------------------------------

Config.CameraFOV = 50.0
Config.NightVisionKey = 78
Config.ThermalVisionKey = 84
Config.ZoomInKey = 96
Config.ZoomOutKey = 97
Config.ToggleCursorKey = 244

These are key codes for camera view controls - most users should leave these as default.

FOV controls the camera's field of view (lower = more zoomed in, higher = wider view).

--------------------------------------------------------------------------------
POSTAL CODES (Lines 76-79)
--------------------------------------------------------------------------------

Config.PostalCodes = {
    [1] = { coords = vector3(425.1, -979.5, 30.7), code = "3201" },
    [2] = { coords = vector3(1854.9, 3686.6, 34.3), code = "8072" },
}

This system auto-detects the nearest postal code when placing cameras just ignore them.

Add more postal codes here if your server uses a postal code system (format shown above).

If you don't use postal codes, you can leave this as is or empty the table.


================================================================================
                            DEPENDENCIES
================================================================================


This dependency is REQUIRED for camera screenshot functionality to work!

OPTIONAL DEPENDENCIES (only if using ESX/QBCore):

- oxmysql (for database functions)
- es_extended (if using ESX)
- qb-core (if using QBCore)


================================================================================
                            USAGE IN-GAME
================================================================================

TO ACCESS MONITORING STATION:
Walk up to the monitoring station marker (default: Mission Row PD) and press E.

TO PLACE A CAMERA:
Type the command /nycm (or your configured command), enter a camera name, then use WASD/Z/X to position and arrow keys to rotate the camera, press ENTER to confirm.

TO VIEW A CAMERA:
Open the monitoring station and click the eye icon on any camera card.

TO MANAGE CAMERAS:
Click the settings icon on a camera card to edit name/location/notes, or the trash icon to delete.


================================================================================
                            THANK YOU!
================================================================================

================================================================================