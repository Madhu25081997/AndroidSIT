
#Certainly, I'd be happy to explain each part of the provided Python code in detail.

```python
from openpyxl import Workbook 
from openpyxl.styles import Font
```
Here, the code starts by importing necessary modules from the `openpyxl` library. This library is used for working with Excel files, allowing you to create, modify, and manipulate Excel spreadsheets. The `Workbook` class is used to create a new Excel workbook, and the `Font` class is used to apply formatting, such as bold text, to cells.

```python
wb = Workbook() 
sheet = wb.active
sheet.title = "Language"
wb.create_sheet(title = "Capital")
```
Here, a new Excel workbook is created using the `Workbook` class. The `.active` attribute gives you access to the active (default) sheet in the workbook. The active sheet is then given the title "Language". Another sheet titled "Capital" is created using the `create_sheet` method of the workbook.

```python
lang = ["Kannada", "Telugu", "Tamil"]
state = ["Karnataka", "Telangana", "Tamil Nadu"]
capital = ["Bengaluru", "Hyderabad", "Chennai"]
code = ['KA', 'TS', 'TN']
```
These lists contain the data that will be added to the Excel spreadsheet. `lang` contains the languages, `state` contains the state names, `capital` contains the capital cities, and `code` contains the corresponding state codes.

```python
sheet.cell(row=1, column=1).value = "State"
sheet.cell(row=1, column=2).value = "Language"
sheet.cell(row=1, column=3).value = "Code"
```
These lines set the headers for the columns in the "Language" sheet of the Excel workbook. The `.cell(row, column)` method is used to access specific cells in the spreadsheet.

```python
ft = Font(bold=True)
for row in sheet["A1:C1"]:
    for cell in row:
        cell.font = ft
```
Here, a `Font` object is created with the `bold` attribute set to `True`, creating a bold font style. The nested loops iterate through each cell in the range "A1:C1" and apply the bold font style to each cell.

```python
for i in range(2, 5):
    sheet.cell(row=i, column=1).value = state[i-2]
    sheet.cell(row=i, column=2).value = lang[i-2]
    sheet.cell(row=i, column=3).value = code[i-2]
```
These lines populate rows 2 to 4 of the "Language" sheet with data from the `state`, `lang`, and `code` lists using a loop. The loop iterates from 2 to 4, and the `i-2` index is used to access the correct values from the lists.

```python
wb.save("demo.xlsx")
```
This line saves the Excel workbook with the filename "demo.xlsx".

```python
sheet = wb["Capital"]

sheet.cell(row=1, column=1).value = "State"
sheet.cell(row=1, column=2).value = "Capital"
sheet.cell(row=1, column=3).value = "Code"
```
Similar to earlier, these lines set the headers for the columns in the "Capital" sheet of the Excel workbook.

```python
for i in range(2, 5):
    sheet.cell(row=i, column=1).value = state[i-2]
    sheet.cell(row=i, column=2).value = capital[i-2]
    sheet.cell(row=i, column=3).value = code[i-2]
```
These lines populate rows 2 to 4 of the "Capital" sheet with data from the `state`, `capital`, and `code` lists using a loop, just like in the "Language" sheet.

```python
srchCode = input("Enter state code for finding capital ")
for i in range(2, 5):
    data = sheet.cell(row=i, column=3).value
    if data == srchCode:
        print("Corresponding capital for code", srchCode, "is", sheet.cell(row=i, column=2).value)
```
Here, the code prompts the user to enter a state code. It then loops through rows 2 to 4 in the "Capital" sheet, comparing the entered code with the values in the third column. If a match is found, it prints the corresponding capital city.

```python
sheet = wb["Language"]

srchCode = input("Enter state code for finding language ")
for i in range(2, 5):
    data = sheet.cell(row=i, column=3).value
    if data == srchCode:
        print("Corresponding language for code", srchCode, "is", sheet.cell(row=i, column=2).value)
```
Similarly, this part of the code switches to the "Language" sheet and prompts the user to enter a state code. It then loops through rows 2 to 4, comparing the entered code with the values in the third column. If a match is found, it prints the corresponding language.

```python
wb.close()
```
Finally, this line closes the Excel workbook.

Overall, the code creates an Excel workbook with two sheets ("Language" and "Capital"), populates them with data, allows the user to search for capital cities and languages based on state codes, and then closes the workbook.
