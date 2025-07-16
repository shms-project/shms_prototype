# Structural Health Monitoring System (SHMS)
## 1. Problem Statement: 
Modern civil infrastructure such as buildings, bridges, and tunnels are susceptible to the formation of cracks over time due to environmental stress, material fatigue, and poor construction. Early detection and accurate assessment of these cracks is crucial to prevent structural failures and reduce repair costs.
Traditional inspection methods rely heavily on manual observation, physical tools, and markers, which are time-consuming, imprecise, and often unsafe. There is a clear need for a more efficient, accurate, and technology-driven approach to structural monitoring.
This project aims to develop a markerless AR-based Structural Health Monitoring System (SHMS) that uses SLAM (Simultaneous Localization and Mapping) to precisely track the location of cracks and measure their real-world dimensions, even when the camera moves. The system eliminates the need for physical markers or tags and provides inspectors with a mobile, real-time tool for detecting and recording structural damage.
While the current focus is on civil infrastructure, the system is designed to scale into aviation applications in the future, enabling similar crack tracking and dimensioning capabilities for aircraft maintenance.

## 2. Target Users:
This system is designed for multiple types of users who interact with structural health data at different stages of the inspection and repair process. The initial version of the system will support the following user roles:
1. Inspector (Phase 1 – Included)
   > Primary user of the mobile AR application <br>
   > Uses the app to scan walls, detect cracks, and measure their dimensions in real-world units <br>
   > Uploads crack data, severity level, and geolocation to the central database <br>
   > Does not need physical markers or targets for scanning 

2. Manager (Phase 1 – Included)
   > Uses the web dashboard to review crack reports submitted by inspectors <br>
   > Filters cracks by severity, location, structure, and inspection time <br>
   > Prioritizes which cracks need immediate attention and assigns repair tasks <br>
   > Generates reports and tracks inspection history

3. Admin (Future Phase – Not Included in MVP)
   > Manages user roles, permissions, and system-wide settings <br>
   > Controls access to sensitive data and oversees large-scale deployments <br>
   > Optional for MVP; can be added once the system is stable and multi-user control is needed

4. Repair Technician (Future Phase – Optional)
   > Receives assignments from managers based on crack severity and location <br>
   > Updates the system after repairs are complete, including photos and notes <br>
   > May use a lightweight mobile interface or web portal

## 3. Goals & Use-Cases:
The core objective of this system is to provide a seamless, real-time platform for structural damage assessment that is scalable, reliable, and field-ready. The system leverages markerless AR and SLAM (Simultaneous Localization and Mapping) to deliver accurate crack detection and measurement under real-world conditions.

Primary Goals
1. Real-Time Crack Detection and Tracking -
   > Enable inspectors to identify and detect cracks instantly using a mobile device's camera with AR functionality, powered by SLAM for markerless tracking.
2. Dynamic Measurement with Camera Movement - 
   > Accurately measure the length and width of cracks in real-world units, even when the inspector moves closer, farther, or changes angle — without relying on physical markers or tags.
3. Reliable Data Capture and Storage -
   > Capture and sync crack images, measurements, severity levels, timestamps, and location data to a cloud-based backend system in real time.
4. Centralized Crack Reporting and Monitoring -
   > Allow managers to access a web dashboard where they can: <br>
     > View incoming crack reports <br>
     > Filter by severity, date, or location <br>
     > Monitor the structural health of buildings over time <br>

Key Use Cases
<br>
Use Case 1: Real-Time On-Site Inspection
   > An inspector visits a construction site or infrastructure location. <br>
   > They open the AR app and scan a damaged surface. <br>
   > The app detects a crack, measures its dimensions automatically, and logs the severity. <br>
   > Data is synced to the cloud with timestamps and location metadata.

Use Case 2: Backend Storage and Report Generation
   > The backend API receives crack data and stores it securely in the database. <br>
   > Crack images and measurement metadata are linked to specific structures for future access.

Use Case 3: Manager Review and Monitoring
   > A manager logs in to the web dashboard and reviews all recent inspections. <br>
   > They sort cracks by severity and identify high-risk areas. <br>
   > Based on the reports, they schedule repairs and export a PDF report.

Notes for Development
   > Focus on precision and persistence of tracking using SLAM <br>
   > Ensure data integrity with consistent syncing to the backend <br>
   > Design UI/UX for quick, intuitive inspection workflows

## 4. MVP (Minimum Viable Product) features:
The MVP for the SHMS will focus on enabling field-ready AR-based crack detection, measurement, and centralized monitoring, while ensuring real-time cloud sync and web-based review. The goal is to have a fully functioning end-to-end pipeline with real data flow across mobile, backend, and web layers.

Mobile App (Inspector) - 
1. Markerless Crack Detection using AR
   > Detect cracks in real time using the mobile camera and a deep learning model <br>
   > Powered by SLAM for markerless positional tracking
2. Real-World Measurement Calculation
   > Dynamically calculate crack length and width in meters/cm <br>
   > Measurement adapts as the camera moves closer, farther, or shifts angle
3. On-Device Inference
   > Run the crack segmentation model offline on the mobile device using TensorFlow Lite
4. Capture & Submit Report
   > Uploads image, measurement data, severity score, timestamp, and structure ID to backend

Backend API - 
1. REST API for Crack Reports
   > Endpoints for: <br>
     > Uploading crack data <br>
     > Retrieving cracks per structure <br>
     > Authenticating users (JWT or token-based)
2. Database Integration
   > Tables/collections for Users, Structures, Cracks <br>
   > Stores crack metadata, image URLs, dimensions, severity, etc.
3. Cloud Storage
   > Save uploaded crack images and segmentation masks (Firebase or AWS S3)

Web Dashboard (Manager) - 
1. Login Interface
   > Basic authentication for Inspectors and Managers
2. Crack Report List View
   > Display all cracks submitted with filter/search options: <br>
     > Severity <br>
     > Structure <br>
     > Date/time
3. Crack Detail View
   > View image, dimensions, severity, and location for any report
4. PDF Report Export
   > Export crack report as a PDF (single or bulk)

## 5. Future Features
As the SHMS evolves, the following advanced features will enhance its functionality, usability, and scalability across industries including civil infrastructure and aviation.

1. Expanded User Roles & Permissions
   > Admin Role: <br>
    > Full control over user management (adding, removing, editing Inspector and Manager accounts) <br>
    > System configuration settings (e.g., notification rules, data retention policies) <br>
    > Audit logs for data changes and system usage <br>
   > Repair Technician Module: <br>
    > A dedicated interface (mobile or web) for technicians to receive work orders <br>
    > Ability to update repair status, attach before/after photos, and add inspection notes <br>
    > Integration with a scheduling system to streamline maintenance operations

2. Enhanced Data Analytics and Reporting
   > Historical Data Analysis: <br>
    > Track crack progression over time with repeat scans <br>
    > Visualize changes using trend graphs and statistical reports <br>
    > Incorporate machine learning to predict potential failure points or future growth <br>
   > Advanced Dashboard Features: <br>
    > Integration with GIS platforms (e.g., Mapbox or Leaflet.js) for mapping and spatial analysis <br>
    > Customizable dashboards for different user roles (inspectors, managers, admins) <br>
    > Drill-down capabilities to view crack history by structure, date range, or severity level <br>
   > Automated Alerts & Notifications: <br>
    > Real-time email, SMS, or push notifications for cracks exceeding a risk threshold <br>
    > Notification settings configurable per structure or user role <br>
    > Integration with third-party alert systems for rapid response 

3. Improved AR and Measurement Capabilities
   > Time-Based Tracking: <br>
    > Use periodic scans to compute the growth rate of cracks <br>
    > Visual overlays showing temporal changes (e.g., heat maps indicating critical areas) <br>
   > Enhanced SLAM and Multi-Sensor Fusion: <br>
    > Refine SLAM integration for even greater accuracy under varying field conditions <br>
    > Incorporate additional sensor data (e.g., LiDAR on supported devices) to improve measurement precision <br>
    > Experiment with additional modalities like thermal imaging or ultrasound for composite damage assessment <br>
   > Drone Integration (Advanced Use Cases): <br>
    > Develop a companion module to allow drones equipped with cameras and sensors to perform scans in hard-to-reach areas <br>
    > Integrate drone data with the SHMS for a comprehensive structural overview

4. Integration with External Systems and Services
   > Interoperability with Enterprise Systems: <br>
    > APIs for integration with existing maintenance, safety, or asset management platforms <br>
    > Data sharing with municipal or governmental agencies for compliance and regulatory reporting <br>
   > Cloud-Based AI/ML Enhancements: <br>
    > Offload heavy post-processing tasks to the cloud to refine crack detection and severity classification <br>
    > Utilize cloud compute for training continual improvement models using field data from all users <br>
    > Explore real-time distributed analytics to identify emerging risk patterns across multiple structures <br>

5. User Experience Enhancements
   > Offline Mode: <br>
    > Allow data capture offline with automatic sync when connectivity is restored <br>
    > Cache previous scans and measurement history for uninterrupted field usage <br>
   > Multilingual and Accessibility Support: <br>
    > Ensure the UI supports multiple languages for global deployments <br>
    > Enhance accessibility features for diverse user groups (e.g., voice commands, high-contrast modes) <br>
   > Mobile UI Upgrades: <br>
    > Refine AR visualizations to provide more context (e.g., AR overlays showing recommended repair actions) <br>
    > Provide in-app tutorials and help resources to ease onboarding and usage <br>

## 6. Assumptions & Constraints
This section outlines the technical assumptions, environmental limitations, and system boundaries that influence how the MVP will be developed and deployed.

1. Technical Assumptions
   > The mobile app will run on modern devices that support ARKit (iOS) or ARCore (Android). <br>
   > The crack detection model will be trained separately and integrated into the app using TensorFlow Lite for real-time inference. <br>
   > Markerless SLAM tracking (Simultaneous Localization and Mapping) will be sufficient for maintaining spatial accuracy in most environments. <br>
   > Users (inspectors) will have access to internet or mobile data for syncing scans to the cloud — however, offline mode may be considered later. <br>
   > Measurements will be calculated from segmentation masks using camera pose, field of view, and AR plane anchors. <br>

2. Environmental Assumptions
   > Structures inspected will be relatively stable (e.g., no moving walls or shaking surfaces).
   > The lighting will be moderately sufficient for the camera to detect crack textures and patterns.
   > The system is intended for civil infrastructure in MVP (buildings, bridges, tunnels), not aircraft interiors (aviation support will be considered in later phases).
   > Surfaces may include concrete, plaster, painted walls, or metal (as long as texture is distinguishable).

3. Scope Constraints
   > No physical markers (QR codes, AprilTags, etc.) will be used to aid measurement or localization.
   > No external sensors (e.g., thermal cameras, LiDAR, ultrasonic devices) are included in the MVP.
   > The mobile app will only be used by field inspectors for now — not repair teams or admins.
   > GPS will be used only when available, and structures will be tagged manually or semi-automatically if GPS is inaccurate indoors.
   > Crack growth over time is not tracked in MVP, but can be added through repeated scan comparisons in later phases.

4. Resource Constraints
   > The team consists of two developers, so feature scope is intentionally limited to ensure completion and depth in key areas.
   > Project duration and submission deadlines may limit the use of more complex components like drone mapping or real-time notifications.
   > Deployment targets are likely limited to one or two field-tested structures for demo purposes during the initial release.



