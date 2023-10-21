# WildTech-Visioneers
This is the GitHub repo for the solution created by team WildTech-Visioneerss for the 2023 O'Reilly Architectural Kata. It contains a proposed architecture for Wildlife.ai.

Team contact: NEED GROUP ADDRESS

Team members:

Add names with links to linkedin profiles

## Overview

Wildlife Watcher

[Wildlife.ai](https://wildlife.ai/), a charity using AI to accelerate wildlife conservation, wants to build an open-source wildlife camera that gets triggered based on the movement of target animals, identifies the species on the device and reports the observation in near real-time to biologists, enabling more efficient species conservation efforts worldwide.

### Users
Biologists and nature enthusiasts (hundreds).

### Requirements
- Users should be able to communicate with the camera using a mobile app (to set the cameras on/off and adjust settings without opening the cameras)
- Users should be able to analyze the videos using common camera trap labelling platforms [(Wildlife Insights](https://wildlifeinsights.org/), [TrapTagger](https://wildeyeconservation.org/traptagger) or [Trapper](https://gitlab.com/trapper-project/trapper))
- Users should be able to publish frames from the videos to iNaturalist for experts to help with the identification of the species
- Users should be able to easily train edge models, using their own labelled videos, and upload the models to the cameras (maybe using third party services like [Roboflow](https://roboflow.com/), [Edge Impulse](https://edgeimpulse.com/) or [TensorFlow Lite](https://www.tensorflow.org/lite))
- Users should be able to publish the species occurrences to [GBIF](https://www.gbif.org/) using the [Camtrap DP](https://tdwg.github.io/camtrap-dp/), [data exchange format](https://tdwg.github.io/camtrap-dp/)
- Cameras should be able to process the footage on the device and send a small alert message to the users via LoraWan, 3G or satellite

### Additional Context
The camera hardware will be a combination of ultra-low-power microcontrollers (up to 512KB Flash) and interchangeable modules (e.g. optical sensor, IR lights, transceiver module, batteries) enclosed in a watertight and 3D printed enclosure.

The API for the specific camera hasn’t been selected, allowing teams to specify what behavior they might need from the hardware, helping the team choose appropriate hardware.

## Architecture Characteristics
Using https://www.developertoarchitect.com/downloads/architecture-characteristics-worksheet.pdf


- Scalabitliy: to support hundreds of users
- Availability, reliabilty, performance: to support near real time communication
- Interoperability: The architecture should support integration with various third-party services and platforms, such as Wildlife Insights, TrapTagger, iNaturalist, and GBIF. Interoperability enables users to work with their preferred tools and extends the project's reach by connecting it to established conservation and research networks. Since requeriments state 
  - communicate with camera
  - analyze video using third party platforms
  - Publish to iNaturalist
  - Train model
  - Publish
 - Security: To protect the data and prevent unauthorized access

## Identify Components
- User
  - Control camera
    - Turn on and off
    - Change settings
    - Upload models
  - Receive small alert from camera
  - Analyze videos using third parties
  - Train edge models. using their own labelled videos
  - Publish frames to iNaturalist
  - Publish species occurrances
- System: Mobile App
- Wildlife Camera
  - Hardware
    - physical devices
    - ultra-low-power microcontrollers (up to 512KB Flash)
    - watertight 3D Printed Enclosure
    - interchangeable modules including
      - optical sensors
      - IR lights
      - transceiver modules
      - batteries
  - Software
    - triggered based on the movement of target animals
    - send a small alert message to the users via LoraWan, 3G or satellite
    - capture video footage
    - process video
    - identifies the species
    - An API or interface that allows Mobile app to communicate with the cameras.
- Third party services (AI, etc)


ADRs
The linked ADRs below record the main architecture decisions regarding the proposed design, including their context and rationale.

ADR 001 - xxxx

## Preliminary phase
Before proposing an architecture, one must better understand the organization, its context and its capabilities.

Wildlife.ai (from website)

- charitable trust that uses artificial intelligence to accelerate wildlife conservation.
- works with grassroots wildlife conservation projects and develop open-source solutions using machine learning.
- organises community events, seminars and educational activities to build and maintain machine learning solutions to reduce the current rate of species extinction.
### Our purpose
To ensure artificial intelligence is widely applied to protect biodiversity.
### Other projects
[Wildlife Watcher](https://wildlife.ai/projects/wildlife-watcher/) A wildlife camera that records animals and uses AI to identify them
[Spyfish Aotearoa](https://wildlife.ai/projects/spyfish-aotearoa/) A citizen science and machine learning approach to identify fish in baited underwater videos
[Pepeketua ID](https://wildlife.ai/projects/pepeketua-id/) A pattern recognition software that facilitates the individual identification of Pepeketua, New Zealand endemic frogs.
[Nesher Bari](https://wildlife.ai/projects/nesher-bari/) Using data analytics to boost the protection of griffon vultures.
[Koster Observatory](https://wildlife.ai/projects/koster-observatory/) A machine learning and citizen science approach to analyse underwater footage from Sweden’s first marine national park.

Most of the project above include open source system that rely on cameras to capture wildlife and the use of machine learning and AI to aid in tracking, identifying, or studying wildlife. The first project is the wildlife camera that will be use on this solution.

The sucess of the current open source project using cameras and AI makes indicates that Wildlife.ai is ready to embark on initiative that leverages its current capabilities and expands them with the introuction of multiple integrations.

## Overall Solution
