# Sign Language Interpreter

A computer-vision prototype that recognizes hand signs from a live camera feed and turns predictions into text. The repository includes a Flask interface and a separate Tkinter desktop application.

## Features

- Live hand tracking with OpenCV and cvzone
- Keras model inference from a webcam
- Character accumulation into a sentence with word suggestions
- Optional text-to-speech in the desktop application
- Flask pages for the web interface and recognition flow

This project recognizes the classes represented by its included model; it should not be described as full sign-language translation without a broader trained vocabulary and evaluation.

## Tech stack

Python, Flask, OpenCV, TensorFlow/Keras, cvzone, NumPy, pyspellchecker, pyttsx3, Firebase Admin.

## Run locally

Use Python compatible with the pinned TensorFlow/Keras versions available in your environment. Install dependencies and start the Flask app:

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

The app loads `cnn8grps_rad1_model.h5` at startup and requires a working webcam. The separate desktop UI can be launched with `python desktop_app.py`; it also loads the model and opens the default camera.

## Firebase configuration

The Flask app attempts to load an Admin SDK service account from `firebase/serviceAccountKey.json`. Obtain a service account from your Firebase project, keep it out of version control, and configure Firebase before using registration or login. Never commit service-account credentials. Set a strong, unique Flask session secret through environment configuration before deployment; the current source contains a placeholder secret and is not production-ready.

## Repository layout

- `app.py`: Flask routes, authentication integration, webcam/model processing
- `desktop_app.py`, `final_pred.py`: Tkinter camera recognition implementation
- `cnn8grps_rad1_model.h5`: trained Keras model artifact
- `templates/`, `static/`: web UI assets

## Limitations

The repository does not document the training dataset, class mapping, or evaluation metrics. Webcam permissions, model/runtime compatibility, Firebase configuration, and local audio support affect operation. Treat predictions as a prototype, not an accessibility-grade translation system.

## Security

Do not deploy as-is. Use environment-managed session credentials, secure Firebase configuration, production cookie settings, request validation, and a production WSGI server. Review tracked session artifacts and remove user/session data from the repository history if any was committed.


