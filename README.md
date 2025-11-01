Oracle of Images

A dual-component steganography project designed to secretly embed short text messages within the Alpha channel of PNG image files. This project is split into a simple, web-based tool for embedding and a robust Python command-line utility for extraction.

🌟 Features

The Magic Quill (Web App): A user-friendly, single-file HTML/JavaScript interface for selecting an image and writing a secret message.

Steganography via Alpha Channel: Messages are hidden by modifying the Least Significant Bit (LSB) of the Alpha (transparency) channel in PNG files. This is a highly resilient method, as LSB changes are imperceptible, and the Alpha channel is often overlooked.

Maximum Capacity Indication: The web app calculates and displays the maximum message size available based on the dimensions of the uploaded PNG image.

Security Hint: A small, unique, and hardcoded hint (AI42) is prefixed to every embedded message, allowing the extractor to quickly verify the presence of a hidden message and ignore false positives.

🛠️ Technology Stack

Component

Technology

Description

Embedder

HTML5, JavaScript, Tailwind CSS

Front-end for file upload, message input, embedding logic, and image export.

Extractor

Python (with PIL/Pillow)

Command-Line Interface (CLI) for extracting the hidden payload from a stego-image.

🚀 How to Use the Embedder (The Magic Quill)

The embedding tool is contained entirely within the secret_inscriber.html file.

Open the Tool: Open secret_inscriber.html in any modern web browser.

Upload Image: Drag and drop or click to upload a PNG image. (Only PNG supports the necessary Alpha channel manipulation).

Write Secret: Type the message you wish to hide. The capacity indicator will update dynamically.

Embed: Click the "Cast the Secret-Writing Spell!" button.

Save: Once the success message appears, right-click (or long-press on mobile) the resulting image preview and select "Save Image As..." to download the new stego-image.

🐍 How to Use the Extractor (Python CLI)

The accompanying Python script, stego_tool.py (assumed to contain the necessary LSB extraction logic), is used to retrieve the secret message.

Prerequisites

You must have Python and the Pillow library installed:

pip install Pillow


Extraction Command

To extract a message from an image created by The Magic Quill, you would run the extractor script, specifying the LSB method and the input file.

# Example command (assuming your extraction function supports LSB or EOI/Alpha method)
python stego_tool.py extract --method lsb_alpha --input path/to/your/secret_image.png 


The script will scan the Alpha channel for the prefixed hint and, if found, decode the full message and print it to the console.
