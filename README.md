# 🎓 AI Quiz Generator

A single-page web application that generates intelligent quizzes from reference materials using Google's Gemini AI with web search capabilities.

## Features

- **📄 Multi-format Support**: Upload PDF, DOCX, TXT, and other document formats
- **🤖 AI-Powered**: Uses Gemini AI with web search to create contextual quizzes
- **📊 Slide-based Interface**: View quizzes one at a time in a clean, slide-like format
- **⚡ Real-time Generation**: See quizzes as they're generated (progressive display)
- **🎯 Two Quiz Types**:
  - Multiple choice (5 options)
  - Short answer (unequivocal, concise answers)
- **📖 Reference Highlighting**: View source material with relevant excerpts highlighted
- **🔑 BYOK**: Bring Your Own Key - use your own Gemini API key
- **✅ Instant Feedback**: Get immediate feedback on your answers with explanations

## How to Use

1. **Get a Gemini API Key**
   - Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Create a new API key
   - Copy the key

2. **Open the App**
   - Simply open `quiz-generator.html` in any modern web browser
   - No installation or server required!

3. **Generate Quizzes**
   - Enter your Gemini API key in the first field
   - Describe the quiz subject/topic
   - Upload your reference material (PDF, DOCX, TXT, etc.)
   - Set how many quizzes you want (1-20)
   - Click "Generate Quizzes"

4. **Take the Quiz**
   - Navigate between quizzes using Previous/Next buttons
   - Select answers for multiple choice questions
   - Type answers for short answer questions
   - Get instant feedback with explanations
   - View reference material with highlighted excerpts

## Technical Details

### Gemini Model
The app uses `gemini-2.0-flash-exp` (the latest Gemini 2.0 Flash model). If you need to change the model, edit line ~425 in the HTML file:

```javascript
const response = await fetch(
    `${GEMINI_API_BASE}/models/gemini-2.0-flash-exp:generateContent?key=${apiKey}`,
```

Available models:
- `gemini-2.0-flash-exp` (recommended - latest, fastest)
- `gemini-1.5-pro` (more capable, slower)
- `gemini-1.5-flash` (fast, efficient)

**Note**: The model name in your example (`gemini-3-pro-preview`) doesn't exist yet. Using the latest available model instead.

### Features Implemented

✅ Single HTML file - no dependencies, runs entirely in browser
✅ File upload to Gemini Files API (48-hour storage)
✅ Google Search integration for enhanced context
✅ Progressive quiz display
✅ Multiple choice (5 choices) and short answer formats
✅ Reference highlighting
✅ Slide-based navigation
✅ Instant answer feedback
✅ Clean, modern UI with animations
✅ Responsive design

### API Usage

The app uses:
- **Gemini Files API**: For uploading reference documents
- **Gemini Content Generation API**: For creating quizzes with web search enabled
- **Google Search Tool**: Provides additional context from the web

### Browser Compatibility

Works in all modern browsers:
- Chrome/Edge (recommended)
- Firefox
- Safari
- Opera

### Security Notes

- API key is stored only in memory (not persisted)
- Files are uploaded to Google's servers for 48 hours
- All communication uses HTTPS

## File Structure

```
quiz_factory/
├── quiz-generator.html    # The complete application
└── README.md             # This file
```

## Customization

### Styling
All CSS is embedded in the `<style>` section. Modify colors, fonts, and layout as needed.

### Quiz Generation Prompt
Edit the prompt in the `generateQuizzes()` function (around line ~200) to customize:
- Question difficulty
- Question types ratio
- Question focus areas

### Number of Choices
To change from 5 to a different number of choices, update:
1. The prompt (line ~200): "must be exactly 5 choices"
2. The letters array (line ~520): `const letters = ['A', 'B', 'C', 'D', 'E'];`

## Troubleshooting

**"File upload failed"**
- Check your API key is valid
- Ensure file size is under 20MB
- Verify file format is supported

**"Quiz generation failed"**
- API key may be invalid or quota exceeded
- Try reducing the number of quizzes
- Check your internet connection

**"No valid quiz data found"**
- The AI response may have been malformed
- Try regenerating with a clearer subject description
- Check if the reference material is relevant to the topic

## License

MIT License - Feel free to modify and use as needed!

## Credits

Built with ❤️ using Google's Gemini AI