# PDFForm

Client-side PDF form filler written in TypeScript.

Original source code by [ZenLiuCN](https://github.com/ZenLiuCN/PDFForm); a port of the [phihag/pdfform.js](https://github.com/phihag/pdfform.js) project.

## Limitations

* Does not support radio buttons.
* May fail with some PDF forms.
  * Original author suggests to try the "compress and reduce size function in Acrobat".
  * Converting the PDF to v1.5 may also help, as v1.6+ increased the complexity of form manipulation.

## Usage Example

```ts
import * as PDFForm from "module_path_for_pdfform";

// Read source PDF as buffer
const inputPDF = // pdf_as_arraybuffer

// Create blob from buffer
const blob = new Blob([inputPDF], {
  type: "application/pdf",
});

// Convert blob back into a buffer
const buffer = await PDFForm.blob2Buffer(blob);

// Output all detected form fields
console.log("PDF fields:", PDFForm.list_fields(buffer));

// Fill form using key/[value] pairs
const outputPDF = PDFForm.fillForm(buffer, {
  txt1: ["first name"],  // text field
  txt2: ["last name"],   // text field
  chk1: [true],          // checkbox field
  chk2: [true]           // checkbox field
});

// Open or download the modified PDF
PDFForm.openOrDownload(outputPDF, "file_name.pdf");
```
