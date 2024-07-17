# Customer Support System

This project implements a Customer Support System that handles user requests via text and audio inputs. It uses a combination of BERT for intent classification, OpenAI's GPT-3.5 for generating responses, and Google Text-to-Speech for generating audio responses.

## Features

- **Intent Classification**: Uses BERT to classify user intents into predefined categories.
- **Context Management**: Maintains conversation context for each user.
- **Text and Audio Input Handling**: Processes both text and audio inputs.
- **Response Generation**: Uses OpenAI's GPT-3.5 to generate context-aware responses.
- **Text-to-Speech Conversion**: Converts text responses to audio using Google Text-to-Speech and pydub.

## Installation

1. **Clone the Repository**:
    ```sh
    git clone https://github.com/your-username/customer-support-system.git
    cd customer-support-system
    ```

2. **Create and Activate Virtual Environment**:
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install Dependencies**:
    ```sh
    pip install -r requirements.txt
    ```

4. **Download and Install `ffmpeg`**:
    - Visit the [FFmpeg download page](https://ffmpeg.org/download.html).
    - Download the latest static build for Windows.
    - Extract the ZIP file to `C:\ffmpeg`.
    - Add `C:\ffmpeg\bin` to your system PATH.

5. **Set Up OpenAI API Key**:
    - Obtain your OpenAI API key from [OpenAI](https://beta.openai.com/).
    - Set the `OPENAI_API_KEY` environment variable:
      ```sh
      export OPENAI_API_KEY='your-openai-api-key'  # On Windows use `set OPENAI_API_KEY=your-openai-api-key`
      ```

## Usage

1. **Run the Script**:
    ```sh
    python customer_support_system.py
    ```

2. **Handle Text Input**:
    ```python
    support_system = CustomerSupportSystem()
    user_id = "user123"
    text_input = "I need help with my account"
    text_response = support_system.handle_request(user_id, 'text', text_input)
    print("Text response:", text_response)
    ```

3. **Handle Audio Input**:
    ```python
    audio_file_path = 'harvard.wav'  # Replace with your actual .wav file path
    audio_response_file = support_system.handle_request(user_id, 'audio', audio_file_path)
    if audio_response_file:
        print("Audio response saved as:", audio_response_file)
        # To play the audio response on your system, use the appropriate command
        os.system(f"start {audio_response_file}")  # Windows command to play audio
        # os.system(f"afplay {audio_response_file}")  # MacOS command to play audio
        # os.system(f"aplay {audio_response_file}")  # Linux command to play audio
    else:
        print("Error processing audio input.")
    ```

## File Structure
customer-support-system/
│
├── models/
│ └── intent_classifier.pt # Pretrained BERT model for intent classification
│
├── data/
│ └── sample_inputs/ # Sample input audio files
│
├── customer_support_system.py # Main script
├── requirements.txt # Python dependencies
├── README.md # Project documentation
└── .gitignore # Git ignore file


## Dependencies

- `torch`
- `transformers`
- `speechrecognition`
- `gtts`
- `pydub`
- `openai`

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [Hugging Face Transformers](https://huggingface.co/transformers/)
- [Google Text-to-Speech (gTTS)](https://pypi.org/project/gTTS/)
- [OpenAI GPT-3](https://beta.openai.com/)
- [pydub](https://pydub.com/)


