---
title: "WordprocessingML 文件的組織結構 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 29c8555df695f9e1a93256ea3a25ed22d441fd6d
ms.lasthandoff: 03/13/2017


---
# <a name="shape-of-wordprocessingml-documents-c"></a>WordprocessingML 文件的組織結構 (C#)
這個主題說明 WordprocessingML 文件的 XML 組織結構。  
  
## <a name="microsoft-office-formats"></a>Microsoft Office 格式  
 2007 Microsoft Office 系統的原始檔案格式為 Office Open XML (一般稱為 Open XML)。 Open XML 是一種 Ecma 標準，而且目前正在通過 ISO-IEC 標準程序的 XML 格式。 在 Open XML 中，字組處理檔案的標記語言稱為 WordprocessingML。 這個教學課程會使用 WordprocessingML 原始程式檔做為範例的輸入。  
  
 使用 Microsoft Office 2003 時，如果您有安裝 Microsoft Office Compatibility Pack for Word、Excel 和 PowerPoint 2007 檔案格式，您可以將文件儲存為 Office Open XML 格式。  
  
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
  
 這個範例會使用在 WindowsBase 組件中找到的類別。 它會使用 <xref:System.IO.Packaging?displayProperty=fullName> 命名空間中的類型。  
  
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
 [Introducing the Office (2007) Open XML File Formats](http://go.microsoft.com/fwlink/?LinkId=98093) (Office (2007) Open XML 檔案格式簡介)  
  
 [Overview of WordprocessingML](http://go.microsoft.com/fwlink/?LinkId=98094) (WordprocessingML 概觀)  
  
 [Office 2003: XML Reference Schemas Download page](http://go.microsoft.com/fwlink/?LinkId=98095) (Office 2003：XML 參考結構描述下載頁面)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程：管理 WordprocessingML 文件中的內容 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
