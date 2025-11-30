YouTube Storage
A web-based tool that encodes files into video format for storage on YouTube, and decodes them back to the original file format. This is a proof-of-concept experiment in creative data serialization and error correction.
🚀 Live Demo
Visit: https://nkontopoul.github.io/youtubestorage
Or download and run locally - it's just a single HTML file!
📋 How It Works
The system converts any file into a video by:

Encoding: File → Binary Data → Error Correction (3x repetition) → Video Frames → WebM Video
Manual Upload: Upload the generated video to YouTube
Manual Download: Download the video back from YouTube
Decoding: Video → Extract Frames → Error Correction → Original File

Technical Details

Resolution: 1080p (1920x1080)
Frame Rate: 30 fps
Data Encoding: 3 bytes per pixel (RGB channels)
Error Correction: Triple repetition with majority voting
Capacity: ~6.2 MB per second of video (after error correction overhead)
Metadata: First 256 bytes contain filename and size information

🎯 Features

✅ Zero Dependencies - Single HTML file, runs entirely in browser
✅ Error Correction - 3x repetition encoding survives YouTube's compression
✅ Metadata Preservation - Original filename automatically recovered
✅ No Server Required - All processing happens client-side
✅ Universal Compatibility - Works with any file type

📦 Installation
Option 1: Use Online (Recommended)
Just visit the live demo link above.
Option 2: Download and Run Locally
bash# Clone the repository
git clone https://github.com/nkontopoul/youtubestorage.git

# Navigate to the directory
cd youtubestorage

# Open the HTML file in your browser
# On Windows:
start youtube.html

# On Mac:
open youtube.html

# On Linux:
xdg-open youtube.html
Or simply download youtube.html and double-click it!
🔧 Usage
Encoding a File

Click "Choose File" under "Encode File to Video"
Select any file from your computer
Click "Create Video"
Wait for processing (larger files take longer)
Click "Download Video" when ready
Manually upload the .webm file to YouTube

Decoding a File

Download your video from YouTube
Click "Choose File" under "Decode Video to File"
Select the downloaded video
Click "Extract File"
Your original file will be automatically downloaded

⚙️ Browser Requirements

Modern Browser: Chrome 90+, Edge 90+, Firefox 88+, Safari 14+
JavaScript: Must be enabled
MediaRecorder API: For video encoding
Canvas API: For pixel manipulation

📊 Storage Efficiency
Original File SizeError-Corrected SizeVideo Duration (approx)Video File Size (approx)1 MB3 MB0.5 seconds3-5 MB10 MB30 MB5 seconds30-50 MB100 MB300 MB50 seconds300-500 MB
Note: Video file sizes depend on WebM compression. YouTube's recompression may increase file sizes.
🛡️ Error Correction
The system uses triple repetition encoding:

Each byte is stored 3 times
During decoding, majority voting recovers corrupted bytes
Survives YouTube's lossy compression in most cases
~67% storage overhead, but significantly improves reliability

⚠️ Limitations
Technical Limitations

YouTube Upload/Download: Must be done manually (browser security restrictions)
File Size: Larger files create longer videos (YouTube max: 12 hours for verified accounts, 15 minutes otherwise)
Compression Artifacts: Heavily compressed videos may lose data
Processing Time: Large files take time to encode/decode

Practical Limitations

Not for Production Use: This is an experimental proof-of-concept
YouTube ToS: May violate YouTube's Terms of Service (use at your own risk)
Inefficient Storage: 3x overhead + video container overhead
No Privacy: Videos uploaded to YouTube are subject to their privacy policies

🔬 The Science Behind It
Why This Works
YouTube uses lossy compression (H.264/VP9) that targets imperceptible quality loss for human viewing. By using:

High bitrate encoding (50 Mbps)
Error correction (3x repetition)
Simple pixel patterns (solid RGB values)

The data survives YouTube's recompression with high fidelity.
Why This Is Impractical

Storage Overhead: 3x data + video container = ~400% size increase
Processing Time: Encoding/decoding is CPU-intensive
Manual Steps: YouTube API restrictions require manual upload/download
Reliability: Not 100% guaranteed to survive all compression scenarios

🤔 FAQ
Q: Is this actually useful?
A: Not really! It's a fascinating experiment in data serialization, but impractical for real-world storage.
Q: Will my data survive YouTube's compression?
A: Usually yes, thanks to error correction. But it's not 100% guaranteed.
Q: Can I automate the YouTube upload/download?
A: Not from a browser due to security restrictions. You'd need a backend server with YouTube API authentication.
Q: What's the maximum file size?
A: Theoretically unlimited, but YouTube limits videos to 128 GB or 12 hours for verified accounts.
Q: Does this violate YouTube's Terms of Service?
A: Possibly. YouTube is intended for video content, not arbitrary data storage. Use at your own risk.
Q: Can I use this for cloud backup?
A: Technically yes, but please don't. Use proper cloud storage services instead.
🧪 Experiment Ideas

Try different error correction schemes (Reed-Solomon, Hamming codes)
Test audio channel encoding (see original discussion about Fourier transforms)
Implement QR code-based encoding for visual verification
Add encryption before encoding
Benchmark different compression codecs

📝 License
MIT License
🙏 Acknowledgments
Inspired by discussions on creative data storage methods and the theoretical limits of using video platforms as storage mediums.
⚠️ Disclaimer
This project is for educational and experimental purposes only. The author is not responsible for:

Violations of YouTube's Terms of Service
Data loss due to failed encoding/decoding
Any misuse of this technology
Account suspensions or legal issues

Use responsibly and at your own risk.
🔗 Links

Repository: github.com/nkontopoul/youtubestorage
Issues: Report bugs or request features
Discussions: Join the conversation


Made with curiosity and experimentation 🎬✨
