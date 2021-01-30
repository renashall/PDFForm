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
import * as PDFForm from "pdfform";

function async generate(): Promise<void> {
  // Fetch PDF as arraybuffer
  const response = await fetch("path/to/input.pdf");
  const inputPDF = await response.arrayBuffer();

  // Create blob from PDF buffer with appropriate type
  const blob = new Blob([inputPDF], {
    type: "application/pdf",
  });

  // Convert blob back into a buffer
  const buffer = await PDFForm.blob2Buffer(blob);

  // Output all detected form fields
  console.log("PDF fields:", PDFForm.listFields(buffer));

  // Fill form using key/[value] pairs
  const outputPDF = PDFForm.fillForm(buffer, {
    txt1: ["first name"],  // text field
    txt2: ["last name"],   // text field
    chk1: [true],          // checkbox field
    chk2: [true]           // checkbox field
  });

  // Open or download the modified PDF
  PDFForm.openOrDownload(outputPDF, "output_file_name.pdf");
}
```
