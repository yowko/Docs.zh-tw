---
title: WordprocessingML 檔的 XML 圖形-LINQ to XML
description: 瞭解 WordprocessingML 檔的 XML 圖形。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 1f5b8098923a56b638598516ed9640a28a90198a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551882"
---
# <a name="the-xml-shape-of-wordprocessingml-documents-linq-to-xml"></a><span data-ttu-id="d6259-103">WordprocessingML 檔的 XML 圖形 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="d6259-103">The XML shape of WordprocessingML documents (LINQ to XML)</span></span>

<span data-ttu-id="d6259-104">本文介紹 WordprocessingML 檔的 XML 圖形。</span><span class="sxs-lookup"><span data-stu-id="d6259-104">This article introduces the XML shape of a WordprocessingML document.</span></span>

## <a name="microsoft-office-formats"></a><span data-ttu-id="d6259-105">Microsoft Office 格式</span><span class="sxs-lookup"><span data-stu-id="d6259-105">Microsoft Office formats</span></span>

<span data-ttu-id="d6259-106">2007 Microsoft Office 系統的原始檔案格式為 Office Open XML (一般稱為 Open XML)。</span><span class="sxs-lookup"><span data-stu-id="d6259-106">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="d6259-107">Open XML 是一種以 XML 為基礎的格式，其為 Ecma 標準，目前正在進行 ISO-IEC 標準處理常式。</span><span class="sxs-lookup"><span data-stu-id="d6259-107">Open XML is an XML-based format that's an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="d6259-108">在 Open XML 中，字組處理檔案的標記語言稱為 WordprocessingML。</span><span class="sxs-lookup"><span data-stu-id="d6259-108">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="d6259-109">這個教學課程會使用 WordprocessingML 原始程式檔做為範例的輸入。</span><span class="sxs-lookup"><span data-stu-id="d6259-109">This tutorial uses WordprocessingML source files as input for the examples.</span></span>

<span data-ttu-id="d6259-110">如果您使用 Microsoft Office 2003，如果您已安裝適用于 Word、Excel 和 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件，則可以使用 Office Open XML 格式來儲存檔。</span><span class="sxs-lookup"><span data-stu-id="d6259-110">If you're using Microsoft Office 2003, you can save documents in the Office Open XML format if you've installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="d6259-111">WordprocessingML 檔的圖形</span><span class="sxs-lookup"><span data-stu-id="d6259-111">The shape of WordprocessingML documents</span></span>

<span data-ttu-id="d6259-112">首先要瞭解的是 WordprocessingML 檔的 XML 圖形。</span><span class="sxs-lookup"><span data-stu-id="d6259-112">The first thing to understand is the XML shape of WordprocessingML documents.</span></span> <span data-ttu-id="d6259-113">WordprocessingML 文件包含具有文件段落的本文項目 (稱為 `w:body`)。</span><span class="sxs-lookup"><span data-stu-id="d6259-113">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="d6259-114">每個段落都包含一或多個文字執行 (稱為 `w:r`)。</span><span class="sxs-lookup"><span data-stu-id="d6259-114">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="d6259-115">每個文字執行都包含一或多個文字片段 (稱為 `w:t`)。</span><span class="sxs-lookup"><span data-stu-id="d6259-115">Each text run contains one or more text pieces (named `w:t`).</span></span>

<span data-ttu-id="d6259-116">下列是非常簡單的 WordprocessingML 文件：</span><span class="sxs-lookup"><span data-stu-id="d6259-116">The following is a very simple WordprocessingML document:</span></span>

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

<span data-ttu-id="d6259-117">這份文件包含兩個段落。</span><span class="sxs-lookup"><span data-stu-id="d6259-117">This document contains two paragraphs.</span></span> <span data-ttu-id="d6259-118">這兩個段落都包含單一的文字執行，而且每個文字執行都包含單一的文字片段。</span><span class="sxs-lookup"><span data-stu-id="d6259-118">They both contain a single text run, and each text run contains a single text piece.</span></span>

<span data-ttu-id="d6259-119">查看 XML 格式之 WordprocessingML 文件內容最簡單的方式是使用 Microsoft Word 建立一個這種文件、儲存起來，然後執行下列程式，將 XML 列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="d6259-119">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>

<span data-ttu-id="d6259-120">這個範例會使用在 WindowsBase 組件中找到的類別。</span><span class="sxs-lookup"><span data-stu-id="d6259-120">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="d6259-121">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="d6259-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d6259-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6259-122">See also</span></span>

- <span data-ttu-id="d6259-123">[Introducing the Office (2007) Open XML File Formats](/previous-versions/office/developer/office-2007/aa338205(v=office.12)) (Office (2007) Open XML 檔案格式簡介)</span><span class="sxs-lookup"><span data-stu-id="d6259-123">[Introducing the Office (2007) Open XML File Formats](/previous-versions/office/developer/office-2007/aa338205(v=office.12))</span></span>
- <span data-ttu-id="d6259-124">[Overview of WordprocessingML](/previous-versions/office/developer/office-2003/aa212812(v=office.11)) (WordprocessingML 概觀)</span><span class="sxs-lookup"><span data-stu-id="d6259-124">[Overview of WordprocessingML](/previous-versions/office/developer/office-2003/aa212812(v=office.11))</span></span>
- <span data-ttu-id="d6259-125">[WordProcessingML 檔案的結構](http://officeopenxml.com/anatomyofOOXML.php) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="d6259-125">[Anatomy of a WordProcessingML File](http://officeopenxml.com/anatomyofOOXML.php)</span></span>
- <span data-ttu-id="d6259-126">[WordprocessingML 簡介](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="d6259-126">[Introduction to WordprocessingML](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)</span></span>
