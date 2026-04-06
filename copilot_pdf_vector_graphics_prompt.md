# Extract vector graphics or embedded chart images from a PDF with Copilot

Sometimes, a simple prompt of showing the figures of a PDF file does not work well using Copilot, especially when the graphic is embedded inside a PDF stream.

A more reliable approach is to ask Copilot to follow a concrete extraction workflow. You can try the prompt below and then adjust the page number or output format as needed.

## Prompt

Can you extract the vector graphic or chart image from page 61 of this PDF by following these steps?

1. Open the PDF with PyPDF2  
2. Navigate to the correct page  
3. Extract the XObject dictionary  
4. Identify the /Image with /JPXDecode  
5. Get the raw JPX bytes  
6. Use Pillow to decode the JPEG-2000 stream  
7. Save as PNG/JPG  

Please tell me what you find and provide the extracted image if successful.

## Notes

- This works best when the target figure is stored as an embedded image object in the PDF.
- `/JPXDecode` usually indicates JPEG 2000 encoded image data.
- If the page contains true vector drawing commands rather than an embedded image, this method may not fully recover the figure as expected.
- If extraction fails, try asking Copilot to inspect all XObject entries on the page and report their subtype, filter, width, and height before exporting anything.


## Caution

This is a practical prompt pattern, not a guaranteed method, considering the fast version iteration of LLMs. PDF internals vary a lot, so results depend on how the original document was created.
