# Document Standardizer

A web-based tool that standardizes Word document formatting using a template document. Upload a template with the desired formatting standards and a document to be standardized, and the system will automatically apply the template's formatting while showing you exactly what changes were made.

## Features

- **Template-Based Standardization**: Uses a reference document to define formatting standards
- **Automatic Formatting Analysis**: Extracts font styles, sizes, spacing, alignment, and more from templates
- **Document Processing**: Applies template formatting to target documents automatically
- **Change Tracking**: Shows redline differences between original and standardized documents
- **Local Processing**: All processing happens locally - no external APIs or cloud services required
- **Modern Web Interface**: Clean, responsive design with drag-and-drop file upload
- **Secure File Handling**: Temporary file storage with automatic cleanup

## What Gets Standardized

The system analyzes and standardizes the following document elements:

### Text Formatting
- Font family and size
- Text alignment (left, center, right, justified)
- Line spacing and paragraph spacing
- Text styles (bold, italic, underline)

### Document Structure
- Header styles (H1, H2, H3, etc.)
- Paragraph formatting
- Bullet point and numbering styles
- Table of Contents formatting

### Layout Elements
- Margins and indentation
- Space before and after paragraphs
- Consistent styling across similar elements

## Installation

### Prerequisites
- Python 3.7 or higher
- pip (Python package installer)

### Setup Instructions

1. **Clone or download the project**
   ```bash
   # Navigate to the doc_processor directory
   cd doc_processor
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment**
   ```bash
   # On Linux/Mac:
   source venv/bin/activate
   
   # On Windows:
   venv\Scripts\activate
   ```

4. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

### Starting the Application

1. **Start the Flask server**
   ```bash
   export FLASK_APP=main.py
   flask run --port=5000
   ```

2. **Open your web browser** and navigate to:
   ```
   http://localhost:5000
   ```

### Using the Document Standardizer

1. **Prepare Your Files**
   - **Template Document**: A .docx file with the correct formatting you want to apply
   - **Target Document**: The .docx file you want to standardize

2. **Upload Documents**
   - Click on the "Template Document" area and select your template file
   - Click on the "Document to Standardize" area and select your target file
   - Both areas support drag-and-drop functionality

3. **Process Documents**
   - Click the "Process Documents" button
   - Wait for processing to complete (usually takes a few seconds)

4. **Review Results**
   - Download the standardized document
   - Review the list of changes made
   - View the redline diff showing exactly what was modified

### File Requirements

- **File Format**: Only .docx files are supported (Microsoft Word 2007+)
- **File Size**: Maximum 16MB per file
- **Template Quality**: Better templates with consistent formatting produce better results

## API Testing

You can also test the application using curl commands:

```bash
# Test the processing endpoint
curl -X POST http://localhost:5000/process \
  -F "template=@path/to/your/template.docx" \
  -F "document=@path/to/your/document.docx"

# Download processed files
curl -O http://localhost:5000/download/updated_filename.docx
```

## Technical Details

### Architecture
- **Backend**: Flask (Python web framework)
- **Document Processing**: python-docx library
- **Diff Generation**: diff-match-patch library
- **Frontend**: HTML5, CSS3, JavaScript (no external frameworks)

### File Processing Workflow
1. **Upload Validation**: Checks file types and sizes
2. **Template Analysis**: Extracts formatting rules from template document
3. **Document Processing**: Applies template formatting to target document
4. **Change Tracking**: Generates diff between original and updated versions
5. **File Generation**: Creates standardized document and diff report

### Security Features
- File type validation (only .docx allowed)
- Secure filename generation to prevent conflicts
- Temporary file storage with cleanup
- No external network requests during processing

## Troubleshooting

### Common Issues

**"File not found" errors**
- Ensure both template and document files are selected
- Check that files are in .docx format
- Verify file sizes are under 16MB

**"Processing failed" errors**
- Check that documents are not corrupted
- Ensure documents are not password-protected
- Try with simpler documents first

**Formatting not applied correctly**
- Ensure template document has consistent formatting
- Check that template uses standard Word styles
- Complex formatting may require manual adjustment

### Logs and Debugging

The application logs processing information to the console. To see detailed logs:

```bash
# Run with debug mode enabled
export FLASK_ENV=development
flask run --debug --port=5000
```

## Limitations

- Only supports .docx format (not .doc or other formats)
- Complex formatting (embedded objects, advanced tables) may not transfer perfectly
- Custom styles not present in the template won't be standardized
- Large documents (>50 pages) may take longer to process

## Contributing

To contribute to this project:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly with various document types
5. Submit a pull request

## License

This project is open source and available under the MIT License.

## Support

For issues or questions:
1. Check the troubleshooting section above
2. Review the console logs for error details
3. Test with simpler documents to isolate issues
4. Ensure all dependencies are properly installed

---

**Document Standardizer** - Making document formatting consistent, one template at a time.
