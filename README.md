# JSON to H5P Converter

A Python tool that converts educational JSON content to H5P interactive format.

## Overview

This converter transforms structured JSON quiz and branching scenario files into H5P packages that can be used on any H5P-compatible platform (Moodle, WordPress, Canvas, etc.).

## Features

- **Quiz Conversion**: Converts multiple choice, multi-select, and short answer questions to H5P Question Set format
- **Branching Scenarios**: Converts interactive story/decision trees to H5P Branching Scenario format  
- **Multiple Question Types**: Supports various question formats with feedback
- **H5P Package Creation**: Generates proper .h5p ZIP files with correct structure
- **Educational Content**: Designed for academic and training content

## Supported JSON Formats

### Quiz Format
```json
{
  "title": "Quiz Title",
  "introduction": "Quiz description",
  "questions": [
    {
      "type": "multichoice",
      "question": "Question text",
      "options": [
        {
          "text": "Option A",
          "correct": true,
          "feedback": "Explanation"
        }
      ]
    }
  ],
  "passPercentage": 80,
  "allowRetry": true,
  "randomizeQuestions": false
}
```

### Branching Scenario Format
```json
{
  "title": "Scenario Title", 
  "introduction": "Scenario description",
  "nodes": [
    {
      "id": "start",
      "type": "content",
      "content": "Story text",
      "choices": [
        {
          "text": "Choice A",
          "next": "node_id"
        }
      ]
    }
  ]
}
```

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/json2h5p.git
cd json2h5p
```

2. Run the converter:
```bash
python json_to_h5p.py
```

## Usage

Place your JSON files in the same directory as the converter and run:

```bash
python json_to_h5p.py
```

The script will automatically detect and convert:
- `*.json` files matching quiz format → `*.h5p` Question Set packages
- `*.json` files matching branching scenario format → `*.h5p` Branching Scenario packages

### Manual Conversion

```python
from json_to_h5p import H5PConverter

converter = H5PConverter()

# Convert quiz
converter.convert_quiz_to_h5p('quiz.json', 'quiz.h5p')

# Convert branching scenario  
converter.convert_branching_scenario_to_h5p('scenario.json', 'scenario.h5p')
```

## Question Types Supported

- **Multiple Choice**: Single correct answer with feedback
- **Multi-Select**: Multiple correct answers required
- **Short Answer**: Text input with keyword matching
- **Branching Content**: Interactive decision trees with quiz elements

## Output

The converter generates `.h5p` files that can be:
- Uploaded to H5P-compatible Learning Management Systems
- Embedded in websites using H5P players
- Shared as standalone interactive content

## Example Files

This repository includes sample educational content:
- `Week1_Foundations_MasteryQuiz.json` - Comprehensive civics quiz
- `Week1_CivicLab_Philadelphia1787.json` - Interactive historical simulation

## Requirements

- Python 3.6+
- Standard library only (no external dependencies)

## License

MIT License - Feel free to use for educational purposes.

## Contributing

Contributions welcome! Please feel free to submit pull requests or open issues for:
- Additional question types
- Enhanced H5P features  
- Bug fixes
- Documentation improvements