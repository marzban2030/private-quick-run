# private-quick-run
private quick run https://github.com/marzban2030/Multi-Camera-Person-Tracking-and-Re-Identification

Run below commands in Colab:
```
!git clone https://github.com/marzban2030/Multi-Camera-Person-Tracking-and-Re-Identification
!pip install -r Multi-Camera-Person-Tracking-and-Re-Identification/requirements.txt
from google.colab import drive
drive.mount('/content/drive')
!cp /content/drive/MyDrive/File.rar .
!cp /content/drive/MyDrive/File.py .
!python File.py | unrar e File.rar
!cp model.pth Multi-Camera-Person-Tracking-and-Re-Identification/model_data/models
!cp yolov3.h5 Multi-Camera-Person-Tracking-and-Re-Identification/model_data/models
!cp yolov4.h5 Multi-Camera-Person-Tracking-and-Re-Identification/model_data/models
!cd Multi-Camera-Person-Tracking-and-Re-Identification && python demo.py --videos videos/init/Double1.mp4 videos/init/Single1.mp4 --version v3
!ls -s Multi-Camera-Person-Tracking-and-Re-Identification/videos/output/
```

To debugging at each commit run:
```
!rm -r -f Multi-Camera-Person-Tracking-and-Re-Identification
!git clone https://github.com/marzban2030/Multi-Camera-Person-Tracking-and-Re-Identification
!cp model.pth Multi-Camera-Person-Tracking-and-Re-Identification/model_data/models
!cp yolov3.h5 Multi-Camera-Person-Tracking-and-Re-Identification/model_data/models
!cp yolov4.h5 Multi-Camera-Person-Tracking-and-Re-Identification/model_data/models
!cd Multi-Camera-Person-Tracking-and-Re-Identification && python demo.py --videos videos/init/Double1.mp4 videos/init/Single1.mp4 --version v3
!ls -s Multi-Camera-Person-Tracking-and-Re-Identification/videos/output/
```

Finally run:
```
from google.colab import files
files.download('Multi-Camera-Person-Tracking-and-Re-Identification/videos/output/Complete.avi')
```

If you want to building single executable file run:
```
%%writefile Multi-Camera-Person-Tracking-and-Re-Identification/my.spec
# -*- mode: python ; coding: utf-8 -*-

import sys ; sys.setrecursionlimit(sys.getrecursionlimit() * 5)

block_cipher = None


a = Analysis(
    ['demo.py'],
    pathex=[],
    binaries=[],
    datas=[],
    hiddenimports=[],
    hookspath=[],
    hooksconfig={},
    runtime_hooks=[],
    excludes=[],
    win_no_prefer_redirects=False,
    win_private_assemblies=False,
    cipher=block_cipher,
    noarchive=False,
)
pyz = PYZ(a.pure, a.zipped_data, cipher=block_cipher)

exe = EXE(
    pyz,
    a.scripts,
    a.binaries,
    a.zipfiles,
    a.datas,
    [],
    name='demo',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    upx_exclude=[],
    runtime_tmpdir=None,
    console=True,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
)
```

Then run:
```
!pip install pyinstaller
!cd Multi-Camera-Person-Tracking-and-Re-Identification && pyinstaller my.spec
```

Create work dir by running:
```
!mkdir work
!cp Multi-Camera-Person-Tracking-and-Re-Identification/dist/demo work/
!cp -r Multi-Camera-Person-Tracking-and-Re-Identification/model_data work/
!cd work && mkdir videos
!cd work/videos && mkdir output
!chmod -c 755 work/demo
```

To executing run:
```
!cd work && ./demo --videos video1.mp4  video2.mp4 video3.mp4 ... videoN.mp4 --version v3
```

Or run:
```
!cd work && ./demo --videos video1.mp4  video2.mp4 video3.mp4 ... videoN.mp4
```
