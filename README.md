

### 📄 `AjustFigma`

# 📦 HTML/CSS Adjustment Figma Pipeline for Landing Page

This script automates the processing of HTML and CSS files exported from Figma. It watches for changes and modifies content to fit a Flask-compatible landing page setup with responsive design support (desktop, mobile, tablet).

## 🚀 Features

- Automatically replaces static paths in HTML files.
- Injects custom stylesheets and JavaScript blocks for each device type.
- Updates CSS files in the correct static directory.
- Watches for changes in specified folders and processes files in real time.

## 📁 Expected Directory Structure

```
project/
├── pipelineajustfigma/
│   ├── Desktop.html
│   ├── Mobile.html
│   └── Tablet.html
│   ├── Desktop_style.css
│   ├── Desktop_vars.css
│   ├── Mobile_style.css
├── static/
│   └── css/
│       └── ...
├── templates/
│   └── (Processed HTML files will be saved here)
└── pipeline.py
```

## 🧠 How It Works

### 1. HTML Processing

- Replaces image paths:  
  From: `src="image.png"`  
  To: `src="{{ static_url }}img/Landingpagev2/image.png"`

- Removes:  
  ```html
  <link rel="stylesheet" href="./vars.css">
  ```

- Replaces:  
  ```html
  <link rel="stylesheet" href="./style.css">
  ```
  with a device-specific stylesheet block (desktop, mobile, tablet).

- Inserts scripts before the `</body>` tag:
  ```html
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  ...
  ```

- Replaces page title "Document" with the app name (`Media Cuts Studio`).

### 2. File Watching

The script uses `watchdog` to monitor changes in:

- `pipelineajustfigma/` — HTML files exported from Figma.
- `static/css/` — CSS files.

Modified files are auto-processed and updated accordingly.

## ⚙️ Usage

1. Install dependencies:

```bash
pip install -r requirements.txt
```

2. Run the script:

```bash
python pipeline.py
```

3. Update or replace your HTML/CSS files in the watched folders. Processed HTML will be saved in `templates/`, and updated CSS files will be copied to `static/css/`.

## ✏️ Customization

- **App Name**: Change the `name_app` variable to adjust the page title.
- **Scripts**: Modify the `scripts` variable to control which JavaScript files are injected.

## 🛠 Requirements

- Python 3.6+
- `watchdog` package

## 🧯 To Stop

Press `Ctrl + C` to stop watching the files.

---

Se quiser, também posso gerar um script `setup.sh` ou `start.sh` para automatizar a instalação e execução. Deseja isso também?
