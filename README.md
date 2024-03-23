## ORB-SLAM2 API Documentation

- Documentation of API used in tele-meeting application

------------------------------------------------------------------------------------------

#### Documentation
##### SLAM Shared Library API

<details>
 <summary>
    <code>Boolean</code> <code><b>/</b></code> <code>init</code> <code>([Initialize] Initialize SLAM tracking.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | str       |  required | byte[]                  | Byte local path to ORB-SLAM2 vocabulary (ORBvoc.txt).  |
> | fx        |  optional | float                   | Camera focal length in x-direction. Default is `640.0f`. We used `492.283793f`   |
> | fy        |  optional | float                   | Camera focal length in y-direction. Default is `640.0f`. We used `493.500742f`   |
> | cx        |  optional | float                   | Camera principal point x-coordinate. Default is `240.0f`. We used `310.163170f`   |
> | cy        |  optional | float                   | Camera principal point y-coordinate. Default is `320.0f`. We used `234.538534f`   |
> | k1        |  optional | float                   | Radial distortion coefficient k1. Default is `0.0f`. We used `0.097875f`   |
> | k2        |  optional | float                   | Radial distortion coefficient k2. Default is `0.0f`. We used `-0.385917f`   |
> | p1        |  optional | float                   | Tangential distortion coefficient p1. Default is `0.0f`. We used `0.0f`   |
> | p2        |  optional | float                   | Tangential distortion coefficient p2. Default is `0.0f`. We used `0.0f`   |
> | k3        |  optional | float                   | Radial distortion coefficient k3. Default is `0.0f`. We used `0.510286ff`   |
> | fps       |  optional | float                   | Camera frames per second. Default is `30.0f`.     |
> | RGB       |  optional | int                     | Flag indicating whether the input images are in RGB format. Default is `1`.     |
> | nFeatures |  optional | int                     | Maximum number of features to track. Default is `1000`. |
> | scaleFactor |  optional | float                 | Pyramid scale factor. Default is `1.2f`. |
> | nLevels   |  optional | int                     | Number of pyramid levels. Default is `8`. |
> | iniThFAST |  optional | int                     | Initial threshold for FAST feature detection. Default is `20`. |
> | minThFAST |  optional | int                     | Minimum threshold for FAST feature detection. Default is `7`. |


##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | success   |  bool                    | True if initialization was successful, false otherwise.  |

</details>

<details>
 <summary>
    <code>IntPtr</code> <code><b>/</b></code> <code>choose_Plane</code> <code>([ChoosePlane] Choose plane from feature points.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | Position  |  required | float[]                 | Float array that holds the position (x, y, z) of the plane.  |
> | EulerAngles |  required | float[]               | Float array that holds the orientation (x, y, z) of the plane in degrees.   |
> | size      |  required | out int                 | Variable that will hold the size of detected plane. |

##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | dataPtr   |  IntPtr                  | Chosen plane.     |

</details>

<details>
 <summary>
    <code>int</code> <code><b>/</b></code> <code>process_Image</code> <code>([UpdateNewFrame] Find feature points in image.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | ImageData |  required | byte[]                  | Image data of the new frame.  |
> | T         |  required | float[]                 | Float array placeholder to save translation matrix.   |
> | wxyz      |  required | float[]                 | Float array placeholder to save rotation matrix.   |
> | isFeature |  required | bool                    | Flag indicating whether to show feature points or not.   |
> | rawdata   |  required | ref Color32[]           | Reference to an array to store the processed image data. |


##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | status    |  int                     | Tracking status code.   |
> | -         |  -                       | `-1` = `SYSTEM_NOT_READY`   |
> | -         |  -                       | `0` = `NO_IMAGES_YET`   |
> | -         |  -                       | `1` = `NOT_INITIALIZED`   |
> | -         |  -                       | `2` = `OK`   |
> | -         |  -                       | `3` = `LOST`   |

</details>

<details>
 <summary>
    <code>void</code> <code><b>/</b></code> <code>reset</code> <code>([Restart] Reset SLAM tracking.)</code>
 </summary>

##### Parameters

> None

##### Returns

> None

</details>

<details>
 <summary>
    <code>void</code> <code><b>/</b></code> <code>save_map_and_quit</code> <code>([SaveMap] Save SLAM map and quit.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | str       |  required | byte[]                  | Byte save path.   |
> | length    |  required | int                     | Length of byte save path.   |

##### Returns

> None

</details>

<details>
 <summary>
    <code>void</code> <code><b>/</b></code> <code>load_map</code> <code>([LoadMap] Load SLAM map.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | str       |  required | byte[]                  | Byte load path.   |
> | length    |  required | int                     | Length of byte load path.   |

##### Returns

> None

</details>

<details>
 <summary>
    <code>Double</code> <code><b>/</b></code> <code>calculate_scale</code> <code>([Calculate_Scale] Find map scale with marker.)</code>
 </summary>

##### Parameters

> None

##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | scale     |  Double                  | Map scale.   |

</details>

------------------------------------------------------------------------------------------

##### Main API

<details>
 <summary>
    <code>GET</code> <code><b>/</b></code> <code>Get_Translation</code> <code>(Get camera translation.)</code>
 </summary>

##### Parameters

> None

##### Responses

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | posc      |  Vector3                 | Camera translation.   |

</details>

<details>
 <summary>
    <code>GET</code> <code><b>/</b></code> <code>Get_Rotation</code> <code>(Get camera rotation.)</code>
 </summary>

##### Parameters

> None

##### Responses

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | new_qc    |  Quaternion              | Camera rotation.   |

</details>

<details>
 <summary>
    <code>GET</code> <code><b>/</b></code> <code>Get_Plane_Position</code> <code>(Get plane position.)</code>
 </summary>

##### Parameters

> None

##### Responses

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | posp      |  Vector3                 | Plane position.   |

</details>

<details>
 <summary>
    <code>GET</code> <code><b>/</b></code> <code>Get_Plane_Normal</code> <code>(Get plane normal.)</code>
 </summary>

##### Parameters

> None

##### Responses

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | new_qp    |  Quaternion              | Plane normal.   |

</details>

<details>
 <summary>
    <code>GET</code> <code><b>/</b></code> <code>Get_Obj_Position</code> <code>(Get object position.)</code>
 </summary>

##### Parameters

> None

##### Responses

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | obj_t     |  Vector3                 | Object position.   |

</details>

<details>
 <summary>
    <code>GET</code> <code><b>/</b></code> <code>Get_Obj_Normal</code> <code>(Get object normal.)</code>
 </summary>

##### Parameters

> None

##### Responses

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | obj_r     |  Quaternion              | Object normal.   |

</details>

<details>
 <summary>
    <code>GET</code> <code><b>/</b></code> <code>Transform Plane</code> <code>(Get convex hull points.)</code>
 </summary>

##### Parameters

> None

##### Responses

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | convex_points     |  Vector3[]              | Array of convex hull points.   |

</details>

------------------------------------------------------------------------------------------

<details>
 <summary>
    <code>POST</code> <code><b>/</b></code> <code>Initialize</code> <code>(Initialize ORB-SLAM2 system.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | PathToVoc |  required | string                  | Local path to ORB-SLAM2 vocabulary (ORBvoc.txt).  |
> | fx        |  optional | float                   | Camera focal length in x-direction. Default is `640.0f`. We used `492.283793f`   |
> | fy        |  optional | float                   | Camera focal length in y-direction. Default is `640.0f`. We used `493.500742f`   |
> | cx        |  optional | float                   | Camera principal point x-coordinate. Default is `240.0f`. We used `310.163170f`   |
> | cy        |  optional | float                   | Camera principal point y-coordinate. Default is `320.0f`. We used `234.538534f`   |
> | k1        |  optional | float                   | Radial distortion coefficient k1. Default is `0.0f`. We used `0.097875f`   |
> | k2        |  optional | float                   | Radial distortion coefficient k2. Default is `0.0f`. We used `-0.385917f`   |
> | p1        |  optional | float                   | Tangential distortion coefficient p1. Default is `0.0f`. We used `0.0f`   |
> | p2        |  optional | float                   | Tangential distortion coefficient p2. Default is `0.0f`. We used `0.0f`   |
> | k3        |  optional | float                   | Radial distortion coefficient k3. Default is `0.0f`. We used `0.510286ff`   |
> | fps       |  optional | float                   | Camera frames per second. Default is `30.0f`.     |
> | RGB       |  optional | int                     | Flag indicating whether the input images are in RGB format. Default is `1`.     |
> | nFeatures |  optional | int                     | Maximum number of features to track. Default is `1000`. |
> | scaleFactor |  optional | float                 | Pyramid scale factor. Default is `1.2f`. |
> | nLevels   |  optional | int                     | Number of pyramid levels. Default is `8`. |
> | iniThFAST |  optional | int                     | Initial threshold for FAST feature detection. Default is `20`. |
> | minThFAST |  optional | int                     | Minimum threshold for FAST feature detection. Default is `7`. |


##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | success   |  bool                    | True if initialization was successful, false otherwise.  |

##### Example
```
string PathToVoc = Application.persistentDataPath;;
bool success = Initialize(
    PathToVoc, 640.0f, 640.0f, 240.0f, 320.0f, 0.0f, 0.0f, 0.0f, 0.0f, 0.0f, 30.0f, 1, 1000, 1.2f, 8, 20, 7
);
if (success)
{
    Console.WriteLine("Initialization successful!");
}
else
{
    Console.WriteLine("Initialization failed.");
}
```

</details>

<details>
 <summary>
    <code>POST</code> <code><b>/</b></code> <code>UpdateNewFrame</code> <code>(Updates system with new frame and returns tracking status.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | imgData   |  required | byte[]                  | Image data of the new frame.  |
> | isFeature |  required | bool                    | Flag indicating whether to show feature points or not.   |
> | data      |  required | ref Color32[]           | Reference to an array to store the processed image data. |


##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | status    |  int                     | Tracking status code.   |
> | -         |  -                       | `-1` = `SYSTEM_NOT_READY`   |
> | -         |  -                       | `0` = `NO_IMAGES_YET`   |
> | -         |  -                       | `1` = `NOT_INITIALIZED`   |
> | -         |  -                       | `2` = `OK`   |
> | -         |  -                       | `3` = `LOST`   |

</details>

<details>
 <summary>
    <code>POST</code> <code><b>/</b></code> <code>Calculate_Scale</code> <code>(Calculate map scale with a marker.)</code>
 </summary>

##### Parameters

> None


##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | measure_scale    |  float                     | Scale of map based on a known marker.   |

</details>

<details>
 <summary>
    <code>POST</code> <code><b>/</b></code> <code>get_transform</code> <code>(Get matrix transformation and set object transformation.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | pos       |  required | Vector3                 | Position.         |
> | rot       |  required | Quaternion              | Rotation.         |
> | scale     |  required | Vector3                 | Map scale.        |


##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | m         |  Matrix4x4               | Matrix based on known position, rotation, and scale.   |

</details>

<details>
 <summary>
    <code>POST</code> <code><b>/</b></code> <code>set_mr</code> <code>(Rotate matrix.)</code>
 </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | angle     |  required | float                   | Angle in degrees. |


##### Returns

> | name      |  data type               | description       |
> |-----------|--------------------------|-------------------|
> | mr        |  Matrix4x4               | Rotated matrix.   |

</details>

------------------------------------------------------------------------------------------

<details>
  <summary>
    <code>PUT</code> <code><b>/</b></code> <code>SaveMap</code> <code>(Save SLAM map.)</code>
  </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | SavePath  |  required | string                  | Location to save SLAM map.  |

</details>

<details>
  <summary>
    <code>PUT</code> <code><b>/</b></code> <code>LoadMap</code> <code>(Load SLAM map.)</code>
  </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | LoadPath  |  required | string                  | Location to load SLAM map.  |

</details>

<details>
  <summary>
    <code>PUT</code> <code><b>/</b></code> <code>Restart</code> <code>(Restart SLAM tracking and reinitialize.)</code>
  </summary>

##### Parameters

> None

</details>

<details>
  <summary>
    <code>PUT</code> <code><b>/</b></code> <code>ChoosePlane</code> <code>(Find plane using RANSAC method and set plane position & normal.)</code>
  </summary>

##### Parameters

> None

</details>

<details>
  <summary>
    <code>PUT</code> <code><b>/</b></code> <code>SetTransform(pos, rot, scale)</code> <code>(Set matrix transformation.)</code>
  </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | pos       |  required | Vector3                 | Position.         |
> | rot       |  required | Quaternion              | Rotation.         |
> | scale     |  required | Vector3                 | Map scale.        |

</details>

<details>
  <summary>
    <code>PUT</code> <code><b>/</b></code> <code>SetTransform(temp)</code> <code>(Set matrix through assignment.)</code>
  </summary>

##### Parameters

> | name      |  type     | data type               | description       |
> |-----------|-----------|-------------------------|-------------------|
> | temp      |  required | Matrix4x4               | Complete matrix.  |

</details>

------------------------------------------------------------------------------------------
