---
title: WordprocessingML 檔的 XML 圖形-LINQ to XML
description: 瞭解 WordprocessingML 檔的 XML 圖形。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 0c6ed589556eb35a5741739c1f87e1e175476c89
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552201"
---
# <a name="the-xml-shape-of-wordprocessingml-documents-linq-to-xml"></a>WordprocessingML 檔的 XML 圖形 (LINQ to XML) 

本文介紹 WordprocessingML 檔的 XML 圖形。

## <a name="microsoft-office-formats"></a>Microsoft Office 格式

2007 Microsoft Office 系統的原始檔案格式為 Office Open XML (一般稱為 Open XML)。 Open XML 是一種以 XML 為基礎的格式，其為 Ecma 標準，目前正在進行 ISO-IEC 標準處理常式。 在 Open XML 中，字組處理檔案的標記語言稱為 WordprocessingML。 這個教學課程會使用 WordprocessingML 原始程式檔做為範例的輸入。

如果您使用 Microsoft Office 2003，如果您已安裝適用于 Word、Excel 和 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件，則可以使用 Office Open XML 格式來儲存檔。

## <a name="the-shape-of-wordprocessingml-documents"></a>WordprocessingML 檔的圖形

首先要瞭解的是 WordprocessingML 檔的 XML 圖形。 WordprocessingML 文件包含具有文件段落的本文項目 (稱為 `w:body`)。 每個段落都包含一或多個文字執行 (稱為 `w:r`)。 每個文字執行都包含一或多個文字片段 (稱為 `w:t`)。

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

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    Sub Main()
        Dim documentRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"

        Using wdPackage As Package = _
          Package.Open("SampleDoc.docx", _
                       FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage _
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _
                            New Uri("/", UriKind.Relative), _
                            docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                ' Get the officeDocument part from the package.
                ' Load the XML in the part into an XDocument instance.
                Dim xDoc As XDocument = _
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))
                Console.WriteLine(xDoc.Root)
            End If
        End Using
    End Sub
End Module
```

## <a name="see-also"></a>另請參閱

- [Introducing the Office (2007) Open XML File Formats](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205(v=office.12)) (Office (2007) Open XML 檔案格式簡介)
- [Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812(v=office.11)) (WordprocessingML 概觀)
- [WordProcessingML 檔案的結構](http://officeopenxml.com/anatomyofOOXML.php) \(英文\)
- [WordprocessingML 簡介](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/) \(英文\)
