# WildTech-Visioneers

Problem

Wildlife Watcher
Wildlife.ai, a charity using AI to accelerate wildlife conservation, wants to build an open-source wildlife camera that gets triggered based on the movement of target animals, identifies the species on the device and reports the observation in near real-time to biologists, enabling more efficient species conservation efforts worldwide.

Users
Users: biologists and nature enthusiasts (hundreds).

Requirements
- Users should be able to communicate with the camera using a mobile app (to set the cameras on/off and adjust settings without opening the cameras)
- Users should be able to analyze the videos using common camera trap labelling platforms (Wildlife Insights https://wildlifeinsights.org/, TrapTagger https://wildeyeconservation.org/traptagger or Trapper https://gitlab.com/trapper-project/trapper)
Users should be able to publish frames from the videos to iNaturalist for experts to help with the identification of the speciesUsers should be able to easily train edge models. using their own labelled videos, and upload the models to the cameras (maybe using third party services like Roboflow https://roboflow.com/, Edge Impulse https://edgeimpulse.com/ or TensorFlow Lite https://www.tensorflow.org/lite)
Users should be able to publish the species occurrences to GBIF https://www.gbif.org/ using the Camtrap DP https://tdwg.github.io/camtrap-dp/, data exchange format https://tdwg.github.io/camtrap-dp/
Cameras should be able to process the footage on the device and send a small alert message to the users via LoraWan, 3G or satellite

Additional Context
The camera hardware will be a combination of ultra-low-power microcontrollers (up to 512KB Flash) and interchangeable modules (e.g. optical sensor, IR lights, transceiver module, batteries) enclosed in a watertight and 3D printed enclosure.
The API for the specific camera hasn’t been selected, allowing teams to specify what behavior they might need from the hardware, helping the team choose appropriate hardware.

Architecture Chjaracteristics
Using https://www.developertoarchitect.com/downloads/architecture-characteristics-worksheet.pdf
Since requeriments state 
communicate with camera
analyze video using third party platforms
Publish to iNaturalist
Train model
Publish
then integrations

