# 🧠 ActivitySynth: Professional Synthetic HAR Data Station

ActivitySynth is a high-fidelity synthetic data generation platform designed for **Human Activity Recognition (HAR)** research and machine learning development. It allows researchers and engineers to create massive, labeled datasets of inertial sensor data (Accelerometer & Gyroscope) without the logistical overhead of physical data collection.

## 🚀 Key Features

- **14 Standard Activities**: Pre-configured with realistic biomechanical magnitudes for calling, clapping, cycling, dancing, drinking, eating, fighting, hugging, laughing, listening to music, running, sitting, sleeping, and texting.
- **AI-Powered Profiling**: Uses **Genkit** and Gemini to suggest realistic sensor patterns for new activities based on physical world physics.
- **Anomaly Injection**: Generate rare "edge case" events (like falls or medical emergencies) using AI to calculate realistic deviations in intensity and frequency.
- **Multi-Subject Simulation**: Model data for multiple subjects, each with unique biomechanical variations (speed, intensity, and noise floors).
- **Real-Time Visualization**: High-performance interactive charts for X/Y/Z axes using Recharts.
- **Data Explorer**: A professional-grade table view for inspecting individual samples, with filtering by subject and activity class.
- **Format-Ready Exports**: Instant export to CSV or JSON formats, ready for training pipelines in Python/TensorFlow/PyTorch.

## 🛠 How It Works

### 1. The Simulation Engine
The core engine (`src/lib/simulation-engine.ts`) utilizes periodic functions (sine waves) combined with:
- **Secondary Harmonics**: To simulate the complexity of human limb movement.
- **Gaussian Noise**: Representing sensor inaccuracies and environment jitter.
- **Low-Frequency Drift**: Simulating sensor bias over time.
- **Impulse Events**: Random high-G impacts for activities like "Fighting" or "Clapping".

### 2. AI Assisted Design
We leverage **Google Genkit** to bridge the gap between high-level activity names and low-level physics:
- **Pattern Suggestions**: "How fast does an arm move when texting?" – The AI provides these parameters.
- **Anomaly Scenarios**: The AI defines how a "Trip and Fall" affects the 3-axis accelerometer based on the starting activity (e.g., Running vs. Sitting).

### 3. Data Schema
The generated CSV follows a standard ML-ready format:
- `timestamp`: Relative time in seconds.
- `subject_id`: Unique identifier for the person.
- `activity`: Class label (e.g., `Running` or `Sitting_ANOMALY_FALL`).
- `is_anomaly`: Boolean flag for supervised learning.
- `accel_x/y/z`: Linear acceleration in $g$ units.
- `gyro_x/y/z`: Angular velocity in degrees per second.

## 📦 Included Activities
The system is pre-loaded with:
- **Stationary**: Sitting, Sleeping
- **Low Intensity**: Calling, Drinking, Eating, Hugging, Listening_to_music, Texting
- **High Intensity**: Clapping, Cycling, Dancing, Fighting, Laughing, Running

## 💻 Tech Stack
- **Framework**: Next.js 15 (App Router)
- **Styling**: Tailwind CSS + Shadcn UI
- **AI**: Google Genkit + Gemini 2.5 Flash
- **Charts**: Recharts
- **Icons**: Lucide React

---
*Created for the Firebase Studio Prototyping environment.*