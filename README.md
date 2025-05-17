# 🤖 AI Debate Platform

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Q0Uq8Er0PKPviUNT7HKqyekXqTzA-UhU?usp=sharing)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/release/python-380/)

A platform that allows you to pit different language models against each other in a structured debate format. Watch as AI models argue different sides of a topic and judge each other's performance!

![image](https://github.com/user-attachments/assets/a12a7113-a244-4fea-8a9a-96900eaad1ba)



## 🌟 Features

- **Model vs Model Debates**: Select different language models to argue for and against a topic
- **Neutral AI Judge**: Have a third model evaluate the debate and declare a winner
- **Custom Topics**: Enter any debate topic you want to explore
- **Configurable Rounds**: Set how many back-and-forth exchanges you want to see
- **Works in Google Colab**: Run directly in your browser without any local setup
- **Memory Optimized**: Designed to work within Colab's free tier GPU constraints

## 📋 Requirements

- Google Colab account (free)
- Internet connection
- No additional authentication required!

## 🚀 Quick Start

### Option 1: Run in Colab (Recommended)

1. Click the "Open in Colab" badge at the top of this README
2. Run the notebook (Runtime > Run all)
3. Click the public URL that appears to access the interface
4. Configure your debate and click "Start Debate"

![image](https://github.com/user-attachments/assets/f41949e3-5c69-4232-9534-e87bf508b430)



### Option 2: Run Locally

```bash
# Clone the repository
git clone https://github.com/USERNAME/AI-Debate-Platform.git
cd AI-Debate-Platform

# Install dependencies
pip install -r requirements.txt

# Run the application
python debate_app.py
```

## 🎮 Usage Guide

### Setting Up a Debate

1. **Select your models**:
   - **Debater A (FOR)**: Model that will argue in favor of the topic
   - **Debater B (AGAINST)**: Model that will argue against the topic
   - **Judge**: Model that will evaluate arguments and declare a winner

2. **Enter a debate topic**:
   - Keep it clear and concise
   - Example: "Is artificial intelligence beneficial for humanity?"

3. **Configure debate parameters**:
   - **Number of Rounds**: How many back-and-forth exchanges (1-2 recommended)
   - **Max Words**: Maximum response length for each debater (30-100 recommended)

4. **Click "Start Debate"** and wait for results!

### Recommended Model Combinations

For best results on Colab's free tier GPU:

| Role | Recommended Models |
|------|-------------------|
| Debater A | GPT-2-small, DistilGPT-2 |
| Debater B | OPT-125M, DistilGPT-2 |
| Judge | OPT-125M, GPT-2-small |

### Troubleshooting

If you encounter CUDA errors or memory issues:

1. **Reduce complexity**:
   - Use smaller models (GPT-2-small, DistilGPT-2, OPT-125M)
   - Set debate rounds to 1
   - Lower max words to 50 or less

2. **Restart the runtime**:
   - In Colab: Runtime > Restart runtime
   - Then run all cells again

3. **Check GPU availability**:
   - In Colab: Runtime > Change runtime type > Hardware accelerator > GPU

## 🔧 How It Works

The platform uses the Hugging Face Transformers library to:

1. **Load models**: Efficiently loads language models with memory optimization
2. **Format prompts**: Creates debate-specific prompts for each model
3. **Generate responses**: Has models generate arguments for their assigned positions
4. **Evaluate debates**: Uses a judge model to assess arguments and determine a winner

The entire process happens in sequence to conserve GPU memory:

```
┌───────────┐     ┌───────────┐     ┌───────────┐
│  Debater A├────►│  Debater B├────►│  Debater A│ ... 
└───────────┘     └───────────┘     └───────────┘
                                                 ┌───────────┐
                                             ┌──►│   Judge   │
                                             │   └───────────┘
                                       Transcript
```

## 🧠 Supported Models

The platform currently supports these open-source models:

- **GPT-2-small** (124M parameters)
- **DistilGPT-2** (82M parameters)
- **TinyLlama** (1.1B parameters)
- **Pythia-410M** (410M parameters)
- **OPT-125M** (125M parameters)

These models are specifically chosen to work within Colab's free tier GPU limitations.

## 🔄 Advanced Usage

### Adding Custom Models

To add your own models, modify the `model_map` dictionary:

```python
model_map = {
    "My-Custom-Model": "path/to/model/on/huggingface",
    # Add more models here
}
```

### Local Deployment with Gradio

For persistent deployment, you can install Gradio and host locally:

```bash
pip install gradio
python debate_app.py
```

This will provide a local URL that you can access in your browser.

## 📈 Future Improvements

- [ ] Support for larger models with better debate capabilities
- [ ] Fact-checking component to verify claims
- [ ] Topic suggestion feature
- [ ] Save and share debate transcripts
- [ ] Multi-round tournament mode
- [ ] Custom judging criteria

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgements

- [Hugging Face Transformers](https://github.com/huggingface/transformers) for providing the models and infrastructure
- [Gradio](https://github.com/gradio-app/gradio) for the web interface
- Google Colab for the free GPU resources

---

Created with ❤️ by [Spandan Mukherjee]

*If you find this project useful, please consider giving it a star on GitHub!*
