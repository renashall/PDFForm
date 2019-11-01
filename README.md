# PDFForm
PDF form fill in brower for typescript

this is port from [phihag/pdfform.js](https://github.com/phihag/pdfform.js)
# limit
* not support PDF with radio button
* not use pdfjs
* in some case, it wouldn't parse PDF FORM template **try to use compress and reduce size function in Acrobat**
# changes
 1. change into typescript,old repo is realy old javascript(even not a ES style)
 2. make some codes more easy to read
 3. remove pdfjs dependency
 4. fix for muilt Tx field
 5. fix for checkbox field
 5. add help function for convert blob into arraybuffer (so you donot need to GOOGLE it)
 7. add help function for download blob or show in window (so you donot need to GOOGLE it)
 8. tested with browser (chrome ,not in IE or edege)

# by zen.liu 2019-11-01, only help are welcome; thanks for phihag/pdfform.js, if you want to put this work into you repo as Typescript support are always be welcome
