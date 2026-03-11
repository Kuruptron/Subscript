# Browser-Based Audio Transcriber

This is a lightweight, client-side web application that allows users to transcribe audio files (MP3, WAV, etc.) directly in their browser. It generates subtitles that can be edited in real-time and exported as `.srt` or `.vtt` files.

The primary goal of this project is to provide a free transcription tool that respects user privacy. Since all processing happens locally on the user's machine, no audio data is ever uploaded to a server.

## Features

* **Local Processing:** Uses Transformers.js to run OpenAI's Whisper model (tiny.en) locally via WebAssembly.
* **Privacy-First:** Audio files never leave your computer.
* **Integrated Editor:** Edit the generated text and adjust timestamps immediately after transcription.
* **Standard Exports:** Download your results in SubRip (.srt) or WebVTT (.vtt) formats.
* **Zero Cost:** No API keys or backend subscriptions required.

## How it Works

The application utilizes the **Web Audio API** to decode uploaded audio files into a format the machine learning model can understand. It then uses **Transformers.js** to fetch a quantized version of the Whisper model from Hugging Face. Once the model is cached in the browser, it can process audio even without a fast internet connection.

## Installation and Deployment

### Running Locally
1. Clone this repository or download the `index.html` file.
2. Open `index.html` in any modern web browser (Chrome, Firefox, or Edge recommended).
3. Note: Some browsers may require you to run this through a local server (like Live Server in VS Code) to allow the Web Workers to load correctly.

### Hosting on GitHub Pages
This project is designed specifically for static hosting:
1. Push the `index.html` file to a GitHub repository.
2. Navigate to **Settings > Pages**.
3. Select the **main** branch as the source and click **Save**.
4. Your tool will be live at `https://<your-username>.github.io/<repository-name>/`.

## Technical Limitations

* **Initial Load:** The first time you use the tool, it will download approximately 40MB of model data. This is stored in your browser's cache for future use.
* **Performance:** Transcription speed depends entirely on your local hardware (CPU/GPU).
* **Accuracy:** This version uses the `whisper-tiny.en` model to ensure it runs smoothly on most laptops. While fast, it may not be as accurate as the larger Whisper models.

## License

This project is open-source and available under the MIT License. Feel free to fork it, modify the UI, or swap out the model for a multi-language version.
