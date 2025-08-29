# AI Deck Generator

An intelligent PowerPoint presentation generator that uses AI agents to research topics, create content, and assemble professional presentations automatically.

## 🚀 Features

- **Multi-Agent Architecture**: Uses specialized AI agents for different tasks
- **Web Research**: Automatically searches the web for relevant information
- **AI-Powered Content**: Generates presentation content using Google's Gemini AI
- **Visual Assets**: Adds relevant images to slides
- **Professional Layout**: Creates well-structured 7-slide presentations
- **Multiple Search Engines**: Uses both DuckDuckGo and Google for comprehensive research

## 📋 Prerequisites

- Python 3.7 or higher
- Google Gemini API key
- Google Custom Search API key (optional, for enhanced image search)
- Internet connection for web research and image downloads

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd AI-Deck-Generator
```

### 2. Install Required Dependencies

```bash
pip install -r requirements.txt
```

If you don't have a `requirements.txt` file, install the dependencies manually:

```bash
pip install google-generativeai requests beautifulsoup4 python-pptx Pillow
```

### 3. Set Up API Keys

#### Required: Google Gemini API Key

1. Go to [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. Replace the placeholder in `deck-gen.py`:

```python
GOOGLE_API_KEY = "your-actual-gemini-api-key-here"
```

#### Optional: Google Custom Search API (for enhanced image search)

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Enable the Custom Search API
3. Create API credentials
4. Set up a Custom Search Engine at [Google Programmable Search Engine](https://programmablesearchengine.google.com/)
5. Update the keys in `deck-gen.py`:

```python
GOOGLE_SEARCH_API_KEY = "your-google-search-api-key"
CUSTOM_SEARCH_ENGINE_ID = "your-custom-search-engine-id"
```

## 🎯 How to Use

### Basic Usage

1. **Run the script**:
   ```bash
   python deck-gen.py
   ```

2. **Enter your topic** when prompted:
   ```
   Please enter the topic for your presentation: Artificial Intelligence
   ```

3. **Wait for generation** - The script will:
   - Research your topic on the web
   - Generate a 7-slide presentation structure
   - Create content for each slide
   - Add relevant images (if API keys are configured)
   - Save the presentation as a PowerPoint file

4. **Find your presentation** - It will be saved as `presentation-[topic].pptx` in the same directory

### Example Output

The generated presentation will have this structure:
- **Slide 1**: Title slide
- **Slide 2**: Overview with key talking points
- **Slides 3-6**: Key points with content and images
- **Slide 7**: Conclusion

## 🔧 Configuration Options

### API Key Configuration

The script uses these API keys (configured at the top of `deck-gen.py`):

```python
GOOGLE_API_KEY = "your-gemini-api-key"  # Required
GOOGLE_SEARCH_API_KEY = "your-search-api-key"  # Optional
CUSTOM_SEARCH_ENGINE_ID = "your-search-engine-id"  # Optional
```

### Search Engine Options

- **DuckDuckGo**: Always available (no API key required)
- **Google Custom Search**: Requires API keys for enhanced results and image search

## 📁 Project Structure

```
AI-Deck-Generator/
├── deck-gen.py              # Main script
├── README.md               # This file
├── requirements.txt        # Python dependencies
├── presentation-*.pptx     # Generated presentations
└── .git/                   # Git repository
```

## 🤖 How It Works

The AI Deck Generator uses a multi-agent architecture:

1. **ResearchAgent**: Searches the web for relevant information about your topic
2. **OrchestratorAgent**: Creates a fixed 7-slide presentation structure
3. **ContentStrategistAgent**: Generates content for each slide using AI
4. **VisualAssetAgent**: Determines appropriate images for slides
5. **PowerPointAssemblyAgent**: Assembles the final PowerPoint presentation

### Workflow

```
User Input → Web Research → Content Generation → Image Selection → PowerPoint Assembly → Output File
```

## 🎨 Customization

### Modifying Slide Structure

To change the presentation structure, modify the `create_presentation_plan` method in the `OrchestratorAgent` class:

```python
def create_presentation_plan(self, topic, web_context):
    plan = {
        "slides": [
            {"type": "title_slide", "purpose": "Your custom title slide purpose"},
            # Add more slides as needed
        ]
    }
    return plan
```

### Adjusting Content Generation

Modify the prompt in `ContentStrategistAgent.generate_presentation_content()` to change how content is generated.

### Image Search Configuration

Customize image search by modifying the `_get_image_for_slide` method in `PowerPointAssemblyAgent`.

## 🐛 Troubleshooting

### Common Issues

1. **API Key Errors**:
   - Ensure your Gemini API key is valid and has sufficient quota
   - Check that the API key is properly set in the script

2. **Import Errors**:
   - Make sure all dependencies are installed: `pip install -r requirements.txt`

3. **Image Download Failures**:
   - This is normal if Google Search API keys aren't configured
   - Presentations will still be generated without images

4. **Web Search Failures**:
   - Check your internet connection
   - Some search engines may temporarily block requests

### Error Messages

- `"ERROR: Please set your GOOGLE_API_KEY"`: Add your Gemini API key
- `"Google Search keys not provided"`: Normal if you haven't set up Google Search API
- `"Web search failed"`: Check internet connection or try again later

## 📝 Dependencies

- `google-generativeai`: Google's Gemini AI API client
- `requests`: HTTP library for web requests
- `beautifulsoup4`: HTML parsing for web scraping
- `python-pptx`: PowerPoint file creation and manipulation
- `Pillow`: Image processing and format conversion

## 🙏 Acknowledgments

- Google Gemini AI for content generation
- DuckDuckGo for web search capabilities
- Google Custom Search API for enhanced search features
- The python-pptx library for PowerPoint manipulation

---
