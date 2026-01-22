# 🤖 MIT College Chatbot

An intelligent chatbot application built with Flask and Deep Learning to provide information about Maharashtra Institute of Technology (MIT) College, Aurangabad. The chatbot uses Natural Language Processing (NLP) and Neural Networks to understand user queries and provide relevant responses.

## 📋 Table of Contents
- [Features](#features)
- [Screenshots](#screenshots)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Training the Model](#training-the-model)
- [Contributing](#contributing)

## ✨ Features

- 💬 Interactive web-based chat interface
- 🧠 Deep Learning powered responses using Neural Networks
- 🎯 Intent recognition and classification
- 📚 Information about MIT College courses, facilities, and general queries
- 🎨 Modern and responsive UI with animated background
- 🚀 Real-time message processing
- 🔄 Conversation history display

## 📸 Screenshots

### Chat Interface
![Chat Interface](assets/Screenshot%20From%202026-01-23%2001-15-13.png)
*Main chat interface with welcome message*

### Chatbot Conversation
![Chatbot Response 1](assets/Screenshot%20From%202026-01-23%2001-17-06.png)
*Example conversation with the chatbot*

![Chatbot Response 2](assets/Screenshot%20From%202026-01-23%2001-17-26.png)
*Chatbot providing information about MIT College*

## 🛠️ Technology Stack

### Backend
- **Flask** - Web framework for Python
- **TensorFlow/Keras** - Deep Learning framework for building the neural network model
- **NLTK** - Natural Language Toolkit for text processing
- **NumPy** - Numerical computing library

### Frontend
- **HTML5** - Structure
- **CSS3** - Styling with modern animations
- **jQuery** - DOM manipulation and AJAX requests
- **Bootstrap 3** - Responsive design framework

### Machine Learning
- **Sequential Neural Network** - For intent classification
- **Word Embeddings** - Bag of Words model
- **Lemmatization** - Text normalization using WordNet

## 📁 Project Structure

```
chatbot/
├── app.py                 # Flask application main file
├── processor.py           # NLP processing and model prediction logic
├── chatbot.py            # Model training script
├── chatbot_model.h5      # Trained neural network model
├── job_intents.json      # Training data with intents, patterns, and responses
├── words.pkl             # Pickled vocabulary list
├── classes.pkl           # Pickled intent classes
├── static/               # Static files
│   ├── jquery.min.js     # jQuery library
│   └── avatar/           # Avatar images and icons
├── templates/            # HTML templates
│   └── index.html        # Main chat interface
├── assets/               # Screenshots and documentation images
└── README.md             # Project documentation
```

## 🚀 Installation

### Prerequisites
- Python 3.8 or higher
- Virtual environment (recommended)
- Git (for cloning the repository)

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd chatbot
```

### Step 2: Create and Activate Virtual Environment
```bash
# Create virtual environment
python -m venv .venv

# Activate virtual environment
# On Linux/Mac:
source .venv/bin/activate

# On Windows:
.venv\Scripts\activate
```

### Step 3: Install Dependencies
```bash
pip install flask tensorflow keras nltk numpy
```

### Step 4: Download NLTK Data
The application will automatically download required NLTK data on first run, but you can also download manually:
```python
import nltk
nltk.download('punkt_tab')
nltk.download('wordnet')
nltk.download('omw-1.4')
```

## 💻 Usage

### Running the Application

1. Make sure your virtual environment is activated
2. Run the Flask application:
   ```bash
   python app.py
   ```
3. Open your web browser and navigate to:
   - Local: `http://127.0.0.1:8888`
   - Network: `http://192.168.1.31:8888` (accessible from other devices on the same network)

4. Start chatting with the bot!

### Sample Queries

Try asking the chatbot questions like:
- "Hi" or "Hello" - Greetings
- "What is MIT?" - Information about MIT College
- "Tell me about MIT College" - Detailed college information
- "What courses are available?" - Course information
- "Thanks" - Express gratitude
- "Bye" - End conversation

## 🧪 How It Works

### 1. **Natural Language Processing**
   - User input is tokenized using NLTK's word tokenizer
   - Words are lemmatized to their base form using WordNet Lemmatizer
   - Text is converted to lowercase for consistency

### 2. **Bag of Words Model**
   - Input sentence is converted to a numerical vector (bag of words)
   - Each position represents a word from the vocabulary
   - Binary values (0/1) indicate word presence in the sentence

### 3. **Neural Network Prediction**
   - The bag of words vector is fed into the trained neural network
   - Network predicts the intent class with confidence scores
   - Intent with highest probability (>25% threshold) is selected

### 4. **Response Generation**
   - Based on predicted intent, a random response is selected
   - Response is sent back to the user interface via JSON
   - Chat interface displays the response with animations

### Architecture
```
Input Text → Tokenization → Lemmatization → Bag of Words → 
Neural Network → Intent Classification → Response Selection → Output
```

## 🎓 Training the Model

If you want to retrain the model with new intents or patterns:

### 1. Update `job_intents.json`
Add or modify intents in the following format:
```json
{
  "tag": "intent_name",
  "patterns": ["user input example 1", "user input example 2"],
  "responses": ["bot response 1", "bot response 2"]
}
```

### 2. Run Training Script
```bash
python chatbot.py
```

This will:
- Process the intents file
- Create vocabulary and classes
- Train the neural network
- Save the model as `chatbot_model.h5`
- Save vocabulary as `words.pkl`
- Save classes as `classes.pkl`

### Neural Network Architecture
- **Input Layer**: Size matches vocabulary length
- **Hidden Layers**: Dense layers with dropout for regularization
- **Output Layer**: Softmax activation for multi-class classification
- **Optimizer**: Stochastic Gradient Descent (SGD)
- **Loss Function**: Categorical Crossentropy

## 🔧 Configuration

### Changing Server Port
Edit `app.py`:
```python
if __name__ == '__main__':
    app.run(host='0.0.0.0', port='8888', debug=True)
```
Change `port='8888'` to your desired port number.

### Adding New Intents
1. Open `job_intents.json`
2. Add new intent with patterns and responses
3. Retrain the model using `chatbot.py`
4. Restart the Flask application

## 📝 API Endpoints

- `GET /` - Main chat interface
- `POST /chatbot` - Chatbot response endpoint
  - Request: `{"question": "user message"}`
  - Response: `{"response": "bot message"}`

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/improvement`)
3. Make your changes
4. Commit your changes (`git commit -am 'Add new feature'`)
5. Push to the branch (`git push origin feature/improvement`)
6. Create a Pull Request

## 📄 License

This project is open source and available for educational purposes.

## 👤 Author

Chinmay

## 🙏 Acknowledgments

- Maharashtra Institute of Technology (MIT), Aurangabad for the use case
- Flask framework for the web application
- TensorFlow/Keras for deep learning capabilities
- NLTK for natural language processing tools

## 🐛 Known Issues

- Model warnings about CUDA drivers (GPU) - Can be ignored if running on CPU
- Deprecated `decay` parameter warning - Does not affect functionality

## 📞 Support

For issues, questions, or suggestions, please open an issue in the repository.

---

**Note**: This chatbot is designed for educational purposes and to provide information about MIT College, Aurangabad.
