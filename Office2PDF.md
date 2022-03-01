# Conversione di file Office in PDF in batch

Crea la seguente sub in VB, cambia il valore di `base`, esegui:

```Visual Basic
Sub CreatePDF()

    Dim pres As PowerPoint.Presentation
    Dim filename As String
    Dim base As String
    Dim pdf As String
    
    base = "C:\Users\Davide\Downloads\downthemall\"
    
    filename = Dir(base + "*.ppt*")
    
    Do While filename > ""
        Set pres = Nothing
    
        If Right(filename, 1) = "x" Then
            Set pres = PowerPoint.Presentations.Open2007(base + filename)
        Else
            Set pres = PowerPoint.Presentations.Open(base + filename)
        End If
        
        pdf = Replace(filename, "pptx", "pdf")
        pdf = Replace(pdf, "ppt", "pdf")
        
        Call pres.ExportAsFixedFormat(base + pdf, ppFixedFormatTypePDF, ppFixedFormatIntentPrint)
    
        filename = Dir()
    Loop
End Sub
```
