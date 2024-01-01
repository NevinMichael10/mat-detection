# YOLOv5 Custom Dataset Training Guide

## 1. Collect Images for Custom Dataset:
   - 🐍 Install Python: [Python Download](https://www.python.org/downloads/)
   - 📦 Install lxml: `pip install lxml`
   - 📦 Install PyQt5: `pip install PyQt5` or `pip3 install PyQt5`
   - 💻 Open command prompt in the labelImg folder and run `python labelImg.py` for image annotation.

## 2. Annotate Images:
   - ✏️ Annotate images using the rectangle tool in labelImg and save annotations in PascalVOC format.
   - 📂 Copy XML files to the `xml_to_yolo_convert\convert` folder.

## 3. Convert Annotations to YOLO Format:
   - 🛠️ Edit `convert.py` and update class names.
   - 🚀 Run `python convert.py` in the `xml_to_yolo_convert\convert` folder.

## 4. Separate Dataset for Training and Validation:
   - 📊 Copy 80% of images to `dataset\images\train` and corresponding YOLO files to `dataset\labels\train`.
   - 📊 Copy the remaining 20% of images to `dataset\images\val` and corresponding YOLO files to `dataset\labels\val`.

## 5. YAML File Editing:
   - 📝 Open `yolov5\data\custom_dataset.yaml` in a text editor.
   - 📝 In our case `custom_dataset.yaml` with `mat.yaml`
   - 🔄 Update the `nc` value to the number of classes and replace class names.
   - 💾 Save the file.

## 6. Create Virtual Environment (Optional):
   - 🌐 Download and install Python.
   - 📁 Create a folder, open command prompt, and run:
     - `python -m venv virtual_environment_name`
     - `virtual_environment_name\Scripts\activate` (activate)
     - `deactivate` (deactivate)
     - 🚀 If pip is not showing, run `python -m ensurepip` and upgrade pip.

## 7. YOLOv5 Training and Detection:
   - 🚀 Install requirements: `pip install -r requirements.txt` in the `yolov5` folder.
   - 🚀 For training: `python train.py --img 640 --batch 16 --epochs 100 --data custom_dataset.yaml --weights yolov5s.pt --cache`
   - 📂 After training, find weights in `yolov5/runs/train/exp/weights/best.pt`.
   - 🚀 For detection: `python detect.py --source data/images/ --weights runs/train/exp/weights/best.pt`

## 8. YOLOv5 Commands:
   - 🚀 Training: `python train.py --img 415 --batch 16 --epochs 30 --data dataset.yaml --weights yolov5s.pt --cache`
   - 🚀 Detection: `python detect.py --source data/images/ --weights runs/train/exp/weights/best.pt`

## 9. Run the GUI:
   - 💻 Open terminal and run the command:
     - 🚀 Run `python RunGUI.py`

## 10. References:
   - 🐍 [Python](https://www.python.org/downloads/)
   - 🖌️ [labelImg](https://github.com/tzutalin/labelImg)
   - 🔄 [xml to yolo converter](https://github.com/bjornstenger/xml2yolo)
   - 🚀 [yolov5](https://github.com/ultralytics/yolov5)
   - 🎥 [labelImg Annotation Tutorial](https://youtu.be/Tlvy-eM8YO4)
   - 🎥 [Yolov5 Training Tutorial](https://youtu.be/80Q3HIBy7Qg)
