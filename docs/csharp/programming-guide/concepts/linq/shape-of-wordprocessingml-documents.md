---
title: WordprocessingML 文件的組織結構 (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 0d8a80a8e7d33facd452e3b7fb31793c1ed55c58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="shape-of-wordprocessingml-documents-c"></a>WordprocessingML 文件的組織結構 (C#)
這個主題說明 WordprocessingML 文件的 XML 組織結構。  
  
## <a name="microsoft-office-formats"></a>Microsoft Office 格式  
 2007 Microsoft Office 系統的原始檔案格式為 Office Open XML (一般稱為 Open XML)。 Open XML 是一種 Ecma 標準，而且目前正在通過 ISO-IEC 標準程序的 XML 格式。 在 Open XML 中，字組處理檔案的標記語言稱為 WordprocessingML。 這個教學課程會使用 WordprocessingML 原始程式檔做為範例的輸入。  
  
 如果您是使用 Microsoft Office 2003 且有安裝 Word、Excel 與 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件，便可以將文件儲存為 Office Open XML 格式。  
  
## <a name="the-shape-of-wordprocessingml-documents"></a>WordprocessingML 文件的組織結構  
 第一件要了解的事情是 WordprocessingML 文件的組織結構。 WordprocessingML 文件包含具有文件段落的本文項目 (稱為 `w:body`)。 每個段落都包含一或多個文字執行 (稱為 `w:r`)。 每個文字執行都包含一或多個文字片段 (稱為 `w:t`)。  
  
 下列是非常簡單的 WordprocessingML 文件：  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 這份文件包含兩個段落。 這兩個段落都包含單一的文字執行，而且每個文字執行都包含單一的文字片段。  
  
 查看 XML 格式之 WordprocessingML 文件內容最簡單的方式是使用 Microsoft Word 建立一個這種文件、儲存起來，然後執行下列程式，將 XML 列印到主控台。  
  
 這個範例會使用在 WindowsBase 組件中找到的類別。 它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a>外部資源  
 [Introducing the Office (2007) Open XML File Formats](https://msdn.microsoft.com/library/ms406049.aspx) (Office (2007) Open XML 檔案格式簡介)  
 [Overview of WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx) (WordprocessingML 概觀)  
 [WordProcessingML 檔案的結構](http://officeopenxml.com/anatomyofOOXML.php) \(英文\)  
 [WordprocessingML 簡介](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/) \(英文\)  
 [Office 2003: XML Reference Schemas Download page](https://www.microsoft.com/en-us/download/details.aspx?id=101) (Office 2003：XML 參考結構描述下載頁面)  
  
## <a name="see-also"></a>請參閱  
 [教學課程：管理 WordprocessingML 文件中的內容 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
