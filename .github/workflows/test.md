name: Build Windows Executable

on:
  push:
    branches: [ master, main ]
  pull_request:
    branches: [ master, main ]
  workflow_dispatch:

jobs:
  build-windows:
    runs-on: windows-latest
    
    steps:
    - name: Checkout code
      uses: actions/checkout@v4
      
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'
        
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
        pip install pyinstaller pillow
        
    - name: Create icon script
      run: |
        echo 'from PIL import Image, ImageDraw' > create_icon.py
        echo 'size = 256' >> create_icon.py
        echo 'img = Image.new("RGBA", (size, size), (0, 0, 0, 0))' >> create_icon.py
        echo 'draw = ImageDraw.Draw(img)' >> create_icon.py
        echo 'bg_color = (19, 185, 68, 255)' >> create_icon.py
        echo 'draw.ellipse([10, 10, size-10, size-10], fill=bg_color)' >> create_icon.py
        echo 'grid_color = (255, 255, 255, 180)' >> create_icon.py
        echo 'for i in range(50, size-50, 30):' >> create_icon.py
        echo '    draw.line([i, 50, i, size-50], fill=grid_color, width=2)' >> create_icon.py
        echo '    draw.line([50, i, size-50, i], fill=grid_color, width=2)' >> create_icon.py
        echo 'img.save("icon.png")' >> create_icon.py
        echo 'print("图标创建完成")' >> create_icon.py
        
    - name: Create icon
      run: python create_icon.py
        
    - name: Build executable
      run: |
        pyinstaller --onefile --windowed --icon=icon.png --name="微信爬虫工具" --add-data="utils;utils" main.py
        
    - name: Upload Windows executable
      uses: actions/upload-artifact@v3
      with:
        name: windows-executable
        path: dist/微信爬虫工具.exe
        
    - name: Create Release (if tagged)
      if: startsWith(github.ref, 'refs/tags/')
      uses: actions/create-release@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        tag_name: ${{ github.ref }}
        release_name: Release ${{ github.ref }}
        draft: false
        prerelease: false 
