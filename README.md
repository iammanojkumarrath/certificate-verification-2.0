📜 Certificate Verification System
    
A modern Flask-based web application for uploading, storing, and verifying certificates using CSV files and QR codes. Upload certificate details, generate QR codes for verification, and download CSVs by scanning QR codes or using manual links—all wrapped in a sleek, responsive UI powered by Tailwind CSS. 🚀
✨ Features

📤 CSV Upload: Upload CSV files with certificate details (ID, name, course, date).
📷 QR Code Generation: Automatically create QR codes linking to certificate downloads.
✅ Verification: Enter a certificate ID to view its QR code and download the CSV.
🗄️ Database Storage: Securely store certificate data in MySQL.
📱 Responsive Design: Modern UI with a collapsible sidebar, styled with Tailwind CSS and Inter font.
🔒 Secure File Handling: Store uploaded CSVs and QR codes on the server.

🛠️ Technologies

Backend: Flask (Python) 🐍
Database: MySQL 🗃️
Frontend: HTML, Tailwind CSS 🎨, Heroicons 🖼️, Google Fonts (Inter) ✒️
Libraries: mysql-connector-python, pandas, qrcode, python-dotenv

📋 Prerequisites

Python 3.8+ 🐍
MySQL Server 🗄️
Git 🌳
Web browser (e.g., Chrome, Firefox) 🌐

🚀 Installation

Clone the Repository 🌐:
git clone https://github.com/your-username/certificate-verification-system.git
cd certificate-verification-system


Set Up a Virtual Environment 🛠️:
python -m venv venv
.\venv\Scripts\activate  # Windows
# or
source venv/bin/activate  # macOS/Linux


Install Dependencies 📦:
pip install flask mysql-connector-python pandas qrcode pillow python-dotenv


Configure MySQL Database 🗄️:

Create the database:CREATE DATABASE certificates_db;


Create the certificates table:USE certificates_db;
CREATE TABLE certificates (
    certificate_id VARCHAR(50) PRIMARY KEY,
    recipient_name VARCHAR(100),
    course_title VARCHAR(100),
    issue_date DATE,
    verification_url VARCHAR(255),
    csv_file_path VARCHAR(255)
);




Set Up Environment Variables 🔧:

Create a .env file in the project root:MYSQL_USER=your_mysql_username
MYSQL_PASSWORD=your_mysql_password
MYSQL_HOST=localhost
MYSQL_DB=certificates_db


Replace your_mysql_username and your_mysql_password with your MySQL credentials.


Create Directory Structure 📂:

Ensure these directories exist:D:\certificate-verification\uploads
D:\certificate-verification\static\qrcodes


Set permissions (Windows):icacls "D:\certificate-verification\uploads" /grant Everyone:F
icacls "D:\certificate-verification\static\qrcodes" /grant Everyone:F




Run the Application 🚀:
python app.py


Access at http://localhost:5001 or your server’s IP (e.g., http://192.168.29.236:5001).



📖 Usage

Home Page 🏠:

Visit http://<your-ip>:5001/ to see the homepage with navigation links.


Upload CSV 📤:

Navigate to http://<your-ip>:5001/upload.
Upload a CSV file with this format:certificate_id,recipient_name,course_title,issue_date
CERT123,John Doe,Python Programming,2025-07-07
CERT456,Jane Smith,Data Science,2025-07-08


On success, QR codes are saved in static/qrcodes, and data is stored in the database.


Verify Certificate ✅:

Go to http://<your-ip>:5001/verify.
Enter a certificate ID (e.g., CERT123) and click "Generate QR Code".
Scan the QR code with a mobile device to download the CSV, or click "Download CSV Manually".


Responsive Design 📱:

On mobile, click the hamburger icon (☰) in the header to toggle the sidebar.



📂 Project Structure
certificate-verification/
├── app.py                  # Flask application 🐍
├── .env                    # Environment variables 🔧 (not tracked)
├── templates/              # HTML templates 📄
│   ├── base.html           # Base template with header, sidebar, footer
│   ├── upload.html         # CSV upload page
│   ├── verify.html         # Verification page
├── static/                 # Static assets 🌐
│   ├── qrcodes/            # Generated QR code images 📷
├── uploads/                # Uploaded CSV files 📤
├── venv/                   # Virtual environment 🛠️
└── README.md               # Project documentation 📜

🔍 Notes

Server IP: Update app.py’s verification_url if your IP differs from 192.168.29.236:5001:verification_url = f'http://<your-ip>:5001/verify_download/{certificate_id}'


File Paths: Ensure uploads and static/qrcodes directories exist and are writable.
Dependencies: Use a virtual environment to avoid conflicts.
Security: For production, secure MySQL connections and file uploads (e.g., HTTPS, input validation).

🤝 Contributing

Fork the repository 🍴.
Create a feature branch (git checkout -b feature/your-feature) 🌿.
Commit changes (git commit -m 'Add your feature') 📝.
Push to the branch (git push origin feature/your-feature) 🚀.
Open a pull request 📬.

📄 License
This project is licensed under the MIT License. See the LICENSE file for details. 📜
📬 Contact
For issues or suggestions, open an issue on GitHub or contact  iammanojkumarrath@gmail.com. 💌
