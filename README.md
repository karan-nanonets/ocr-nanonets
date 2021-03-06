# Nanonets OCR Wrapper
_The best intelligent OCR and table extraction tool to read and process images and PDFs_

[![N|Solid](https://i.postimg.cc/59ZZmyrt/Screenshot-2022-07-12-at-11-37-27-PM.png)](https://nanonets.com/?&utm_source=wrapper)


ocr-nanonets is an intelligent OCR and table extraction tool which reads plain text and tables from images / PDFs and gives multiple post-OCR formatting and file conversion options to fine-tune based on requirements.

- accurate OCR Engine
- great table extraction capabilities
- get results as bounding boxes / line items / csv / searchable pdfs / strings.

You can also check out our free online tools - 
- [Image/PDF to Text Online](https://nanonets.com/image-to-text)     
- [Image/PDF to CSV Online](https://nanonets.com/convert-pdf-to-csv) 

## Installation
ocr-nanonets requires [Python 3](https://www.python.org/downloads/) to run.
You can use pip to download the wrapper from terminal:
```pip install ocr-nanonets-wrapper``` or ```pip3 install ocr-nanonets-wrapper```

## Authentication and Usage
****
Nanonets OCR Class Instance
```
from nanonets import NANONETSOCR
nanonets = NANONETSOCR()
```
****
The next step is to get your free API Key for authentication.
- Go to [nanonets.com](https://app.nanonets.com/#/signup?&utm_source=wrapper)
- On your Nanonets Account, Go to My Account -> API Keys
- Copy your API Key 

Authenticate your class instance
```
nanonets.set_token('API_KEY')
```
****
## Methods
### 1.Raw OCR Prediction
File - Local File Path / URL
```
nanonets.convert_to_prediction('FILE')
```
### 2.Convert to String
File - Local File Path / URL
```
nanonets.image_to_string(file, formatting = 'none', space_size = 11, line_height = 60, line_threshold = 'low')
nanonets.pdf_to_string(file, formatting = 'none', space_size = 11, line_height = 50, line_threshold = 'low')
```
**formatting** can be - 
- ```none``` (DEFAULT) : single space separated text with all formatting removed
- ```lines and spaces``` : all formatting enabled
- ```lines``` : single space separated text with different lines separated with newline character 
- ```pages``` (ONLY FOR pdf_to_string) : list of page wise single space separated text with all formatting removed

**line_threshold** (OPTIONAL): works in ```lines``` and ```lines and spaces``` formatting mode, can be - 
- ```low``` (DEFAULT) : low senstivity for line separation. works for most cases.
- ```high``` : high senstivity for line separation. this works better with diagrams and flowcharts.

**space_size** (OPTIONAL): works for ```lines and spaces``` formatting mode. it helps to manually specify your definition of space character. a smaller value means that smaller and smaller horizontal gaps / empty spaces between text in your file will be detected as space characters and vice versa. default value is 11.

**line_height** (OPTIONAL): works for ```lines and spaces``` formatting mode. it helps to manually specify your definition of new line (line change). a smaller value means that smaller and smaller vertical gaps / empty spaces between text in your file will be detected as newline characters and vice versa. default value is 60.

### 2.Convert to Bounding Boxes
You can get words and their bounding boxes detected by the OCR Engine.
File - Local File Path / URL
```
nanonets.image_to_boxes(file)
nanonets.pdf_to_boxes(file)
```

### 3.Convert to CSV
File - Local File Path (URL Not Supported as of yet)
Multiple Table Extraction in one image / PDF is supported.
```
nanonets.image_to_csv(file, filename = , cell_width = 250, cell_height = 50, is_table=True)
nanonets.pdf_to_csv(file, filename = , cell_width = 750, cell_height = 150, is_table = True)
```
- **filename** is the name you want the output csv file to have. If not specified, csv file created will have ".csv" appended to "original file name" as file name.
- **is_table** (OPTIONAL): This is ```True``` by default. Keep ```is_table=True``` in all cases to get best results. ```is_table=False``` should only be used if result required is a mix of unstructured text and tabular data.
- **cell_width** (OPTIONAL): only applies if ```is_table=False```. it helps to manually specify your definition of how much horizontal space in your file equals one cell width. default values in code snippets above.
- **cell_height** (OPTIONAL): only applies if ```is_table=False```. it helps to manually specify your definition of how much vertical space in your file equals one cell height. default values in code snippets above.

### 4.Convert to Searchable PDF
File - Local File Path / URL
```
nanonets.image_to_searchablepdf(file, filename = 'did not give a filename', formatting = 'lines and spaces',space_size = 11, line_height = 60, line_threshold = 'low')
nanonets.pdf_to_searchablepdf(file, filename = 'did not give a filename', formatting = 'lines and spaces',space_size = 11, line_height = 50, line_threshold = 'low')
```
- **filename** is the name you want the output pdf file to have. If not specified, pdf file created will have ".csv" appended to "original file name" as file name.

**formatting** can be - 
- ```none``` (DEFAULT) : single space separated text with all formatting removed
- ```lines and spaces``` : all formatting enabled
- ```lines``` : single space separated text with different lines separated with newline character 
- ```pages``` (ONLY FOR pdf_to_string) : list of page wise single space separated text with all formatting removed

**line_threshold** (OPTIONAL): works in ```lines``` and ```lines and spaces``` formatting mode, can be - 
- ```low``` (DEFAULT) : low senstivity for line separation. works for most cases.
- ```high``` : high senstivity for line separation. this works better with diagrams and flowcharts.

**space_size** (OPTIONAL): works for ```lines and spaces``` formatting mode. it helps to manually specify your definition of space character. a smaller value means that smaller and smaller horizontal gaps / empty spaces between text in your file will be detected as space characters and vice versa. default value is 11.

**line_height** (OPTIONAL): works for ```lines and spaces``` formatting mode. it helps to manually specify your definition of new line (line change). a smaller value means that smaller and smaller vertical gaps / empty spaces between text in your file will be detected as newline characters and vice versa. default value is 60.

## Have More Advanced Intelligent Document Processing Needs ? Want to Automate Manual Data Entry Using AI ?
We provide OCR and IDP solutions customised for various use cases - invoice automation, purchase order automation, accounts payable automation, Receipt / ID Card OCR and many more.
- Visit [nanonets.com](https://nanonets.com/?&utm_source=wrapper) for enterprise OCR and IDP solutions.
- Sign up on [app.nanonets.com/#/signup](https://app.nanonets.com/#/signup?&utm_source=wrapper) to start a free trial.


## License

MIT

**This software is perpetually free :)**
