!pip install pypng
import pyqrcode
from PIL import Image
from IPython.display import Image as DisplayImage, display
import io

# Define the links and PDF file
linkedin_url = "https://www.linkedin.com/in//"
github_url = "https://github.com/"

# Create a QR code for each link
linkedin_qr = pyqrcode.create(linkedin_url)
github_qr = pyqrcode.create(github_url)

# Save the QR codes as images in memory with smaller scale
linkedin_buffer = io.BytesIO()
linkedin_qr.png(linkedin_buffer, scale=3) # Reduced scale for smaller QR code
github_buffer = io.BytesIO()
github_qr.png(github_buffer, scale=4) # Reduced scale for smaller QR code

# Display the QR codes for download
display(DisplayImage(data=linkedin_buffer.getvalue(), format='png'), 
        DisplayImage(data=github_buffer.getvalue(), format='png'))
