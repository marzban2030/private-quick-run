# private-quick-run
private quick run https://github.com/marzban2030/Multi-Camera-Person-Tracking-and-Re-Identification

Run below commands in Colab:
```
!git clone https://github.com/marzban2030/Multi-Camera-Person-Tracking-and-Re-Identification
pip install -r Multi-Camera-Person-Tracking-and-Re-Identification/requirements.txt
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
