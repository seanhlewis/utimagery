# Austin 3D Photogrammetry

<img width="4800" height="1200" alt="utimageryheader" src="https://github.com/user-attachments/assets/3d8ef9e9-fd47-4c13-a2a8-a9feabde44b4" />

Austin 3D Photogrammetry captures parts of the University of Texas at Austin campus as detailed 3D models. With a modest grant, a DJI drone, and a stack of flight permits, we set out to scan a few iconic landmarks and drop them into an interactive Cesium globe so anyone can explore UT Austin from afar.

This project sits somewhere between fieldwork, mapping, and digital storytelling: fly the drone, stitch the images, geolocate the result, and then let people wander through the 3D campus in their browser.

---

## Overview

Our goal was simple but surprisingly time-consuming: capturing high-resolution drone imagery of UT Austin landmarks and turn it into accurate, navigable 3D models that live on the web.

Armed with a small grant, we purchased a DJI drone to capture high-resolution images of iconic Austin landmarks. With proper UT Austin permits in hand, we flew above structures like the UT Tower and William Darrell Stadium to produce detailed, geolocated 3D models, now viewable on an interactive Cesium map. Admittedly, scanning even a small area can take hours, so we’re working with a handful of highlights rather than a full digital twin of campus.

Our drone’s high-resolution camera captures overlapping imagery that is essential for photogrammetry. Once the flights are done, we process these images with specialized software to generate accurate 3D meshes and textures. Manual geolocation and scaling ensure precise placements within the Cesium environment, bridging the gap between raw footage and an immersive digital experience.

---

## Data Collection

Most of the interesting work happens before we ever open a photogrammetry tool. We had to secure official permissions from UT Austin to fly over specific parts of campus, schedule flights at times that minimized pedestrian traffic, and work within no-fly zones and height limits. Once we were in the air, the goal was to fly careful, repeatable paths: looping orbits around towers, slow grid passes over the stadium, and enough overlap between images that the reconstruction software could see the same points from many angles.

It is surprisingly easy to spend an entire afternoon on just one building. Between battery swaps, re-flying missed corridors, and double-checking coverage, the set of images that survives into the pipeline is much more curated than the raw dump from the drone’s SD card.

---

## Photogrammetry Pipeline

Once the drone batteries were drained, the second half of the project began. We ingested the images, cleaned out blurry or redundant frames, and fed the remaining set into a structure-from-motion pipeline that estimates camera poses and builds a sparse point cloud. From there, dense reconstruction and meshing turned those points into surfaces; texturing projected the original photos back onto the mesh to recover the look of windows, seating, brick patterns, and field markings.

The models on their own are still floating in space, so we manually aligned them with real-world coordinates and scale using known reference points on campus. This georeferencing step is what lets the models drop seamlessly into Cesium. The final stage was exporting the meshes and textures into a Cesium-friendly format such as 3D Tiles or glTF and wiring them into a simple web viewer.

The whole process is iterative and a bit finicky. Small changes in overlap, altitude, or solver parameters can make the difference between a crisp reconstruction and a warped one. But once everything lines up, flying around the resulting model feels uncannily close to being back on campus.

---

## 3D Models

### UT Tower

<p align="center">
  <img width="600" src="https://github.com/user-attachments/assets/d8924b9c-0700-464e-a882-ab882241de5c" alt="UT Tower 3D model">
</p>

The UT Tower stands as a historic beacon for the University of Texas at Austin, and it naturally became our first major target. We flew a series of tight orbits around the tower, staying within campus restrictions but still capturing enough perspective change for a detailed reconstruction. The resulting 3D model offers an immersive perspective for virtual tours, architecture study, or just plain sightseeing from the comfort of a web browser. Details such as the tower’s vertical lines and roof elements hold up surprisingly well when you zoom in.

### William Darrell Stadium

<p align="center">
  <img width="600" src="https://github.com/user-attachments/assets/0ddde914-7012-4c5c-962e-b93a328dd1ae" alt="William Darrell Stadium 3D model">
</p>

William Darrell Stadium (home to countless sports events) posed a different challenge. Instead of a tall central structure, we had to cover a wide bowl with stands wrapping around a field. Our drone capture ironically covered just half the stadium before time and battery limits kicked in, but even that partial scan is rich enough to explore online. From the reconstructed seating to the surrounding superstructure, the photogrammetry reveals a remarkable level of structural detail.

Taken together, these models prove that even with limited flights and a single drone, we can capture campus landmarks at a level of detail that is useful for exploration, education, and planning.

---

## Interactive Exploration

Seeing the models inside Cesium was the moment when the project really felt real. Instead of staring at meshes in a standalone viewer, we could fly around UT Tower and the stadium in a proper map context: zooming from a city-scale view down to individual architectural details, tilting the camera to match real-world photos we had taken on the ground, and toggling between different captured sites.

We have a small Cesium demo (`index.html`). The viewer streams the tower and stadium tilesets, and users can pan, zoom, and tilt as if they were holding a tiny virtual drone in their browser. Even with just a couple of landmarks, that experience feels like a hint of what a fully scanned campus could become.

---

## Results

Through these 3D models, and the permit process that made them possible, we’re starting to sketch a template for future drone-based captures of Austin’s ever-changing landscape. Even at this early stage, the models are already useful in a few ways. Urban planners and researchers can imagine dropping proposed changes into a realistic 3D base instead of abstract maps. Prospective students and visitors can explore the campus remotely and get a sense of the physical space before they arrive. Researchers interested in digital twins can treat this as a small but concrete example of how low-cost drones fit into a larger ecosystem of city-scale modeling.

Looking ahead, we would like to expand our 3D inventory beyond a couple of landmarks, add more buildings, integrate real-time or near-real-time data where it makes sense, and refine the way people interact with the map. The long-term dream is that scanning a building and dropping it into a living 3D map could be as routine for labs and cities as taking a panorama is for phone users today.

Here is a video of the result inside Cesium:

https://github.com/user-attachments/assets/68b7caa2-837e-4f1d-b439-7e00e7364337

---

## Acknowledgments

Thanks to Shashank Kota for his expertise in flying the drone. Our heartfelt thanks go to the University of Texas at Austin for permitting the drone flights and to the Urban Information Lab for funding this endeavor. We are also grateful to the CesiumJS team for their open-source platform, which makes it straightforward to host and share these models on the web. 

And finally, thanks to everyone on campus who tolerated the sight and sound of a small drone looping around the UT Tower.
