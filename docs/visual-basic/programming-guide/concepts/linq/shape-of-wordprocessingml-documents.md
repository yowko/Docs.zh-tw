---
title: "WordprocessingML 文件的 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5809e8148e7ac426b876ad11948878ee0bfcd016
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2017
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="03278-102">WordprocessingML 文件的 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03278-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="03278-103">這個主題說明 WordprocessingML 文件的 XML 組織結構。</span><span class="sxs-lookup"><span data-stu-id="03278-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="03278-104">Microsoft Office 格式</span><span class="sxs-lookup"><span data-stu-id="03278-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="03278-105">2007 Microsoft Office 系統的原始檔案格式為 Office Open XML (一般稱為 Open XML)。</span><span class="sxs-lookup"><span data-stu-id="03278-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="03278-106">Open XML 是一種 Ecma 標準，而且目前正在通過 ISO-IEC 標準程序的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="03278-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="03278-107">在 Open XML 中，字組處理檔案的標記語言稱為 WordprocessingML。</span><span class="sxs-lookup"><span data-stu-id="03278-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="03278-108">這個教學課程會使用 WordprocessingML 原始程式檔做為範例的輸入。</span><span class="sxs-lookup"><span data-stu-id="03278-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="03278-109">如果您使用 Microsoft Office 2003，您可以將儲存的文件中的 Office Open XML 格式如果您已經安裝 Microsoft Office Compatibility Pack for Word、 Excel 和 PowerPoint 2007 檔案格式。</span><span class="sxs-lookup"><span data-stu-id="03278-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="03278-110">WordprocessingML 文件的組織結構</span><span class="sxs-lookup"><span data-stu-id="03278-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="03278-111">第一件要了解的事情是 WordprocessingML 文件的組織結構。</span><span class="sxs-lookup"><span data-stu-id="03278-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="03278-112">WordprocessingML 文件包含具有文件段落的本文項目 (稱為 `w:body`)。</span><span class="sxs-lookup"><span data-stu-id="03278-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="03278-113">每個段落都包含一或多個文字執行 (稱為 `w:r`)。</span><span class="sxs-lookup"><span data-stu-id="03278-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="03278-114">每個文字執行都包含一或多個文字片段 (稱為 `w:t`)。</span><span class="sxs-lookup"><span data-stu-id="03278-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="03278-115">下列是非常簡單的 WordprocessingML 文件：</span><span class="sxs-lookup"><span data-stu-id="03278-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="03278-116">這份文件包含兩個段落。</span><span class="sxs-lookup"><span data-stu-id="03278-116">This document contains two paragraphs.</span></span> <span data-ttu-id="03278-117">這兩個段落都包含單一的文字執行，而且每個文字執行都包含單一的文字片段。</span><span class="sxs-lookup"><span data-stu-id="03278-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="03278-118">查看 XML 格式之 WordprocessingML 文件內容最簡單的方式是使用 Microsoft Word 建立一個這種文件、儲存起來，然後執行下列程式，將 XML 列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="03278-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="03278-119">這個範例會使用在 WindowsBase 組件中找到的類別。</span><span class="sxs-lookup"><span data-stu-id="03278-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="03278-120">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="03278-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
## <a name="external-resources"></a><span data-ttu-id="03278-121">外部資源</span><span class="sxs-lookup"><span data-stu-id="03278-121">External Resources</span></span>  
 <span data-ttu-id="03278-122">[Introducing the Office (2007) Open XML File Formats](http://go.microsoft.com/fwlink/?LinkId=98093) (Office (2007) Open XML 檔案格式簡介)</span><span class="sxs-lookup"><span data-stu-id="03278-122">[Introducing the Office (2007) Open XML File Formats](http://go.microsoft.com/fwlink/?LinkId=98093)</span></span>  
  
 <span data-ttu-id="03278-123">[Overview of WordprocessingML](http://go.microsoft.com/fwlink/?LinkId=98094) (WordprocessingML 概觀)</span><span class="sxs-lookup"><span data-stu-id="03278-123">[Overview of WordprocessingML](http://go.microsoft.com/fwlink/?LinkId=98094)</span></span>  
  
 <span data-ttu-id="03278-124">[Office 2003: XML Reference Schemas Download page](http://go.microsoft.com/fwlink/?LinkId=98095) (Office 2003：XML 參考結構描述下載頁面)</span><span class="sxs-lookup"><span data-stu-id="03278-124">[Office 2003: XML Reference Schemas Download page](http://go.microsoft.com/fwlink/?LinkId=98095)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03278-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03278-125">See Also</span></span>  
 [<span data-ttu-id="03278-126">教學課程： 操作 WordprocessingML 文件 (Visual Basic) 中的內容</span><span class="sxs-lookup"><span data-stu-id="03278-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
