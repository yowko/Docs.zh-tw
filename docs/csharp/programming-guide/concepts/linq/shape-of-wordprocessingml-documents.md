---
title: WordprocessingML 文件的組織結構 (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: aeb047f23f60ba6951950a85a6e2ef57fcbd9dda
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277464"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="f3032-102">WordprocessingML 文件的組織結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3032-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="f3032-103">這個主題說明 WordprocessingML 文件的 XML 組織結構。</span><span class="sxs-lookup"><span data-stu-id="f3032-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="f3032-104">Microsoft Office 格式</span><span class="sxs-lookup"><span data-stu-id="f3032-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="f3032-105">2007 Microsoft Office 系統的原始檔案格式為 Office Open XML (一般稱為 Open XML)。</span><span class="sxs-lookup"><span data-stu-id="f3032-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="f3032-106">Open XML 是一種 Ecma 標準，而且目前正在通過 ISO-IEC 標準程序的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="f3032-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="f3032-107">在 Open XML 中，字組處理檔案的標記語言稱為 WordprocessingML。</span><span class="sxs-lookup"><span data-stu-id="f3032-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="f3032-108">這個教學課程會使用 WordprocessingML 原始程式檔做為範例的輸入。</span><span class="sxs-lookup"><span data-stu-id="f3032-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="f3032-109">如果您是使用 Microsoft Office 2003 且有安裝 Word、Excel 與 PowerPoint 2007 檔案格式的 Microsoft Office 相容性套件，便可以將文件儲存為 Office Open XML 格式。</span><span class="sxs-lookup"><span data-stu-id="f3032-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="f3032-110">WordprocessingML 文件的組織結構</span><span class="sxs-lookup"><span data-stu-id="f3032-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="f3032-111">第一件要了解的事情是 WordprocessingML 文件的組織結構。</span><span class="sxs-lookup"><span data-stu-id="f3032-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="f3032-112">WordprocessingML 文件包含具有文件段落的本文項目 (稱為 `w:body`)。</span><span class="sxs-lookup"><span data-stu-id="f3032-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="f3032-113">每個段落都包含一或多個文字執行 (稱為 `w:r`)。</span><span class="sxs-lookup"><span data-stu-id="f3032-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="f3032-114">每個文字執行都包含一或多個文字片段 (稱為 `w:t`)。</span><span class="sxs-lookup"><span data-stu-id="f3032-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="f3032-115">下列是非常簡單的 WordprocessingML 文件：</span><span class="sxs-lookup"><span data-stu-id="f3032-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="f3032-116">這份文件包含兩個段落。</span><span class="sxs-lookup"><span data-stu-id="f3032-116">This document contains two paragraphs.</span></span> <span data-ttu-id="f3032-117">這兩個段落都包含單一的文字執行，而且每個文字執行都包含單一的文字片段。</span><span class="sxs-lookup"><span data-stu-id="f3032-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="f3032-118">查看 XML 格式之 WordprocessingML 文件內容最簡單的方式是使用 Microsoft Word 建立一個這種文件、儲存起來，然後執行下列程式，將 XML 列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="f3032-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="f3032-119">這個範例會使用在 WindowsBase 組件中找到的類別。</span><span class="sxs-lookup"><span data-stu-id="f3032-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="f3032-120">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="f3032-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="f3032-121">外部資源</span><span class="sxs-lookup"><span data-stu-id="f3032-121">External Resources</span></span>  
 <span data-ttu-id="f3032-122">[Introducing the Office (2007) Open XML File Formats](https://msdn.microsoft.com/library/ms406049.aspx) (Office (2007) Open XML 檔案格式簡介)</span><span class="sxs-lookup"><span data-stu-id="f3032-122">[Introducing the Office (2007) Open XML File Formats](https://msdn.microsoft.com/library/ms406049.aspx)</span></span>  
 <span data-ttu-id="f3032-123">[Overview of WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx) (WordprocessingML 概觀)</span><span class="sxs-lookup"><span data-stu-id="f3032-123">[Overview of WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)</span></span>  
 <span data-ttu-id="f3032-124">[WordProcessingML 檔案的結構](http://officeopenxml.com/anatomyofOOXML.php) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f3032-124">[Anatomy of a WordProcessingML File](http://officeopenxml.com/anatomyofOOXML.php)</span></span>  
 <span data-ttu-id="f3032-125">[WordprocessingML 簡介](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="f3032-125">[Introduction to WordprocessingML](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)</span></span>  
 <span data-ttu-id="f3032-126">[Office 2003: XML Reference Schemas Download page](https://www.microsoft.com/en-us/download/details.aspx?id=101) (Office 2003：XML 參考結構描述下載頁面)</span><span class="sxs-lookup"><span data-stu-id="f3032-126">[Office 2003: XML Reference Schemas Download page](https://www.microsoft.com/en-us/download/details.aspx?id=101)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3032-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3032-127">See Also</span></span>

- [<span data-ttu-id="f3032-128">教學課程：管理 WordprocessingML 文件中的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3032-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
