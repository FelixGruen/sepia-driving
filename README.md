> [!NOTE]
> The SEPIA Driving dataset will be released in May 2026. Below you'll find some information and the highlights of what is to come.

# SEPIA Driving

![Top Banner](/assets/hero_image.jpg)

The *Static Environment Perception for Infrastructure-Aware (Automated) Driving* (**SEPIA** Driving) dataset is a large-scale, multi-modal dataset for lane detection and road-surface comprehension. It provides a wealth of semantic information from the vehicle’s environment to enable an understanding of the road infrastructure and allowed driving behaviors. Each camera image and corresponding LiDAR scan are annotated with pixel-precise labels for road-surface categories, lane instances, driving directions, lane-boundary locations, lane-boundary types, drivable area, distance to the road surface, as well as occlusion and visibility. Annotations are based on a high-precision 3D world model, ensuring accurate annotations with unlimited viewing distance even behind dynamic objects and in challenging light conditions.

Watch the trailer now:

[![Click here to watch the trailer](/assets/video_first_frame.jpg)](https://www.youtube.com/watch?v=ThkwTLyey9k?autoplay=1)

## Data Recording & Geography

The SEPIA Driving dataset features recordings from 80 kilometers of inner-city and suburban driving in and around the northern German city of Braunschweig. The data spans different times of day and night, multiple weather conditions, and six different routes, capturing a diverse set of real-world driving scenarios.

Recordings were collected at 10 Hz using:

- A 64-layer spinning LiDAR sensor and
- A high-definition, trigger-synchronized roof-mounted camera aligned with the LiDAR’s viewing direction

A high-precision GNSS sensor along with a high-precision IMU, vehicle odometry, and LiDAR scan registration allow for the precise modeling of vehicle position, orientation, and motion.

## Annotations

We provide various types of annotations with the goal of allowing Machine Learning models to learn an accurate representation of their environment containing all necessary information for the automated driving task in complex environments and map creation.

All annotations are based on a 3D model of the world, which enables accurate annotation of non-flat surfaces at unlimited viewing distances, even behind occlusions and under challenging viewing conditions.

### Occlusions

Large static structures such as buildings hide all cues about possible road topology. However, this is not true for other road users, such as cars, buses, and trucks, which often provide valuable cues about the location and semantics of the road surface they occlude.

Our explicit occlusion model therefore distinguishes between dynamic occlusions caused by traffic participants and static occlusions caused by buildings, hedges, and other permanent structures. It provides annotations even behind occlusions from dynamic objects to support learning these cues. To nevertheless allow distinguishing visible from occluded annotations when training models for specific tasks, we additionally provide pixel-wise binary labels outlining the visible ground area up to the first (static or dynamic) obstacle.

### Pixel-wise Semantic Segmentation

We provide detailed pixel-wise labels for:

- Eight semantic road-surface categories like *lane*, *intersection*, *bus stop*, or *parking area*
- Nine lane-boundary and marking types, including *solid*, *broken*, and *unmarked* lane boundaries; *yield* and *stop* lines; and *pedestrian crossings*
- Lane instance segmentation
- *Drivable area*, defined as the unobstructed ego lane, and *alternatively drivable area*, defined as directly neighboring lanes in the same direction not separated by solid boundaries
- Driving direction for all lanes with multiple annotation layers handling crossing lanes at intersections
- Ground-occlusion masks
- Distance to the road surface and relative 3D ground coordinates in the world reference frame

### 2D & 3D Coordinates

For all lane boundaries, annotated road markings, and areas, we provide coordinate representations in:

- the 2D image frame
- the 3D sensor frame
- the 3D world frame

Each coordinate is tagged as visible, behind a dynamic obstacle, or behind a static obstacle.

### Meta-Data

We provide detailed metadata for each drive, including:

- Vehicle and sensor poses at 50 Hz, fused from multiple sensor sources for accurate ego-motion estimation
- Camera and LiDAR intrinsic and extrinsic calibration data
- High-definition maps
