BinhiScan — Updated Seed Classifier and UI Package
================================================

Included files
- index.html: application structure, interactions, seed inference, results view, soil questionnaire
- professional.css: responsive desktop/mobile styling
- model.tflite: the newly supplied Teachable Machine exported model
- labels.txt: eight model class labels
- manifest.webmanifest: installable web-app metadata
- sw.js: service-worker cache configuration

Expected model classes (8)
0. Mais (Corn)
1. Kamatis (Tomato)
2. Talong (Eggplant)
3. Kangkong (Water Spinach)
4. Sitaw (Yardlong Bean)
5. Labanos (Radish)
6. Okra (Okra)
7. Pechay (Pechay)

Updates in this package
- Replaced the previous four-class model and labels with the supplied eight-class export.
- Updated supported-seed list and planting information for all eight classes.
- Compact seed scanning card with Scan Camera and Upload Photo actions.
- Successful scans open a separate in-app results page with the seed photo, label, confidence estimate, class scores, and planting details.
- Soil assessment now supports an optional soil photo, a questionnaire, and optional user-entered actual soil-test values.
- Soil photos are NOT AI-classified. A photo cannot reliably measure pH or nutrient levels; the assessment uses the questionnaire and any values supplied by the user.
- Preserved scan history, planting guide, seasonal check, and PWA shell.

Run/deploy
1. Extract all files into the same folder; do not separate model.tflite and labels.txt from index.html.
2. Serve over HTTPS or localhost. Camera access and service workers generally do not work from a file:// URL.
3. The first launch needs internet to load TensorFlow.js and its TFLite runtime from the configured CDN.
4. Allow camera access or use Upload Photo.
5. Test at least one image for each of the eight classes before using this for a project demo.

Important compatibility notes
- The app checks that the number of labels matches the model output class count at load time.
- The current browser inference path resizes images to the input dimensions reported by the model and converts pixels to integer tensors, matching the prior BinhiScan inference approach. If predictions appear incorrect or inference throws a dtype/input error, the exact Teachable Machine export's input tensor details and preprocessing must be verified.
- Confidence is a model score, not a guarantee of correctness.
- Crop planting and seasonal guidance are general estimates. Confirm local conditions and seed packet instructions.
- Soil readiness is a preliminary checklist, not a lab diagnosis. Nutrient values need units and interpretation.
- Scan history is stored locally in the current browser/device.
- Offline AI use depends on browser caching of external TensorFlow libraries; first launch offline is not guaranteed.
