# 🌐 Cloud Storage and CDN Mini‑Project

This project demonstrates how to host static web content using **GitHub Pages** as a free CDN and integrate basic **file encryption** for secure cloud storage.

## 🚀 Features
- Static website hosted on GitHub Pages  
- Free CDN delivery with HTTPS  
- Simple encryption demo using Python  
- Organized folder structure (`index.html`, `style.css`, `assets/`)  

## 🧠 Technologies Used
- HTML, CSS for frontend  
- Python (cryptography library) for encryption  
- GitHub Pages for hosting  
- Cloudflare (optional) for caching and performance  

## 🧩 How It Works
1. Upload your site files (`index.html`, `style.css`, `assets/`) to your GitHub repository.  
2. Enable GitHub Pages under **Settings → Pages**.  
3. Access your live site at:  
   **https://vaishnavi-t-s.github.io/portfolio-site/**  
4. Use the Python script to encrypt and segment files before uploading to cloud storage.

## 🔐 Encryption Script Example
```python
from cryptography.fernet import Fernet

def encrypt_and_split(file_path, chunk_size=1024*1024):
    key = Fernet.generate_key()
    cipher = Fernet(key)
    with open(file_path, 'rb') as f:
        i = 0
        while chunk := f.read(chunk_size):
            encrypted = cipher.encrypt(chunk)
            with open(f"{file_path}_part{i}.enc", 'wb') as part:
                part.write(encrypted)
            i += 1
    print("Encryption complete. Keep your key safe:", key.decode())
