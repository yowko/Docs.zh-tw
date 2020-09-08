---
title: 具有樣式的 WordprocessingML 檔-LINQ to XML
description: 深入瞭解使用樣式格式化段落的 WordprocessingML 檔。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 40e35de6-ac93-4bba-88ab-a018cbe93873
ms.openlocfilehash: 7864ce5163d9dfb316c8288850210becdf55dc2d
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552207"
---
# <a name="wordprocessingml-document-with-styles-linq-to-xml"></a><span data-ttu-id="407a6-103"> (LINQ to XML 的樣式 WordprocessingML 檔) </span><span class="sxs-lookup"><span data-stu-id="407a6-103">WordprocessingML document with styles (LINQ to XML)</span></span>

<span data-ttu-id="407a6-104">本文所提供的 WordprocessingML 檔，比 [WordprocessingML 檔的 XML 圖形](xml-shape-wordprocessingml-documents.md)中的檔更為複雜;具體來說，它會提供一份檔，其中的段落是以樣式來格式化。</span><span class="sxs-lookup"><span data-stu-id="407a6-104">This article presents a WordprocessingML document that is more complicated than the one in [The XML shape of WordprocessingML documents](xml-shape-wordprocessingml-documents.md); specifically, it presents a document whose paragraphs are formatted with styles.</span></span>

<span data-ttu-id="407a6-105">若要瞭解樣式，瞭解檔結構的相關事項很有説明。</span><span class="sxs-lookup"><span data-stu-id="407a6-105">To understand styles, it's helpful to know something about document structure.</span></span> <span data-ttu-id="407a6-106">WordprocessingML 檔會儲存在包含*元件*的*封裝*中。</span><span class="sxs-lookup"><span data-stu-id="407a6-106">A WordprocessingML document is stored in a *package* that comprises *parts*.</span></span> <span data-ttu-id="407a6-107">具體而言，此詞彙 *封裝* 會對應到 zip 封存，而字詞 *部分* 則會對應到儲存在 zip 內的檔案。</span><span class="sxs-lookup"><span data-stu-id="407a6-107">Specifically, the term *package* corresponds to a ZIP archive and the term *part* corresponds to a file stored within the ZIP.</span></span> <span data-ttu-id="407a6-108">如果檔包含以樣式格式化的段落，則會有一個檔元件包含套用樣式的段落，以及定義檔元件中所參考之樣式的樣式元件。</span><span class="sxs-lookup"><span data-stu-id="407a6-108">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them, and a style part that defines the styles referenced in the document part.</span></span>

<span data-ttu-id="407a6-109">若要查看組成 Office Open XML 檔的 XML，最簡單的方式就是執行範例中的範例 [，輸出 Office OPEN xml 檔部分](example-outputs-office-open-xml-document-parts.md)。</span><span class="sxs-lookup"><span data-stu-id="407a6-109">The easiest way to see the XML that makes up an Office Open XML document is to run the example in [Example that outputs Office Open XML document parts](example-outputs-office-open-xml-document-parts.md).</span></span>

<span data-ttu-id="407a6-110">當您存取封裝時，您應該透過元件之間的關聯性來進行，而不是透過任意路徑。</span><span class="sxs-lookup"><span data-stu-id="407a6-110">When you access a package, you should do so through the relationships among parts, not through an arbitrary path.</span></span> <span data-ttu-id="407a6-111">此問題已超出目前教學課程的範圍，但本教學課程和其他教學課程文章中的程式範例會示範正確的方法。</span><span class="sxs-lookup"><span data-stu-id="407a6-111">This issue is beyond the scope of the current tutorial, but the example programs in this and other tutorial articles demonstrate the correct approach.</span></span>

## <a name="example-a-document-that-uses-styles"></a><span data-ttu-id="407a6-112">範例：使用樣式的檔</span><span class="sxs-lookup"><span data-stu-id="407a6-112">Example: A document that uses styles</span></span>

<span data-ttu-id="407a6-113">下列檔包含使用樣式格式化的段落。</span><span class="sxs-lookup"><span data-stu-id="407a6-113">The following document has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="407a6-114">第一個段落的樣式 `Heading1` 和其他段落具有 `Code` 樣式或預設樣式。</span><span class="sxs-lookup"><span data-stu-id="407a6-114">The first paragraph has the style `Heading1` and other paragraphs have the `Code` style or the default style.</span></span> <span data-ttu-id="407a6-115">若為具有非預設樣式的段落，段落專案會有一個名為的子專案 `w:pPr` ，而該專案會有一個子項目 `w:pStyle` 。</span><span class="sxs-lookup"><span data-stu-id="407a6-115">For paragraphs with non-default styles the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="407a6-116">該項目所擁有的屬性 `w:val` 包含樣式名稱。</span><span class="sxs-lookup"><span data-stu-id="407a6-116">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="407a6-117">針對具有預設樣式的段落，段落專案沒有 `w:p.Pr` 子項目。</span><span class="sxs-lookup"><span data-stu-id="407a6-117">For paragraphs with the default style, the paragraph element doesn't have a `w:p.Pr` child element.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
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
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Heading1" />
      </w:pPr>
      <w:r>
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>The following example prints to the console.</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>using System;</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>class Program {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    public static void </w:t>
      </w:r>
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">
        <w:r w:rsidRPr="00876F34">
          <w:t>Main</w:t>
        </w:r>
      </w:smartTag>
      <w:r w:rsidRPr="00876F34">
        <w:t>(string[] args) {</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t xml:space="preserve">    }</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r w:rsidRPr="00876F34">
        <w:t>}</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">
      <w:r>
        <w:t>This example produces the following output:</w:t>
      </w:r>
    </w:p>
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">
      <w:pPr>
        <w:pStyle w:val="Code" />
      </w:pPr>
      <w:r>
        <w:t>Hello World</w:t>
      </w:r>
    </w:p>
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">
      <w:pgSz w:w="12240" w:h="15840" />
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />
      <w:cols w:space="720" />
      <w:docGrid w:linePitch="360" />
    </w:sectPr>
  </w:body>
</w:document>
```
