---
title: 取出段落及其樣式-LINQ to XML
description: 瞭解如何從 WordprocessingML 檔取出段落節點和其樣式。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: 43c6173441dda841236a4397e28d0bb2c7c8d003
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552716"
---
# <a name="retrieve-the-paragraphs-and-their-styles-linq-to-xml"></a><span data-ttu-id="54899-103">取出段落及其樣式 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="54899-103">Retrieve the paragraphs and their styles (LINQ to XML)</span></span>

<span data-ttu-id="54899-104">在此範例中，我們會撰寫一個從 WordprocessingML 文件擷取段落節點的查詢。</span><span class="sxs-lookup"><span data-stu-id="54899-104">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="54899-105">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="54899-105">It also identifies the style of each paragraph.</span></span>

<span data-ttu-id="54899-106">此查詢是以上述範例中的查詢為基礎，而是 [尋找預設段落樣式](find-default-paragraph-style.md)，此樣式會從樣式清單中抓取預設樣式。</span><span class="sxs-lookup"><span data-stu-id="54899-106">This query builds on the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="54899-107">這項資訊是必要的，因此查詢可以識別未明確設定樣式的段落樣式。</span><span class="sxs-lookup"><span data-stu-id="54899-107">This information is required so that the query can identify the style of paragraphs that don't have a style explicitly set.</span></span> <span data-ttu-id="54899-108">段落樣式是透過元素設定的 `w:pPr` ; 如果段落未包含此元素，則會使用預設樣式來格式化。</span><span class="sxs-lookup"><span data-stu-id="54899-108">Paragraph styles are set through the `w:pPr` element; if a paragraph doesn't contain this element, it's formatted with the default style.</span></span>

<span data-ttu-id="54899-109">本文說明一些查詢片段的重要性，然後將查詢顯示為完整的工作範例的一部分。</span><span class="sxs-lookup"><span data-stu-id="54899-109">This article explains the significance of some pieces of the query, then shows the query as part of a complete working example.</span></span>

## <a name="example-retrieve-all-the-paragraphs-in-a-document-and-the-paragraph-styles"></a><span data-ttu-id="54899-110">範例：取出檔中的所有段落，以及段落樣式</span><span class="sxs-lookup"><span data-stu-id="54899-110">Example: Retrieve all the paragraphs in a document, and the paragraph styles</span></span>

<span data-ttu-id="54899-111">下列程式碼是取得檔中所有段落及其樣式的查詢：</span><span class="sxs-lookup"><span data-stu-id="54899-111">The following code is a query to retrieve all the paragraphs in a document and their styles:</span></span>

```csharp
xDoc.Root.Element(w + "body").Descendants(w + "p")
```

```vb
xDoc.Root.<w:body>...<w:p>
```

<span data-ttu-id="54899-112">此運算式類似于上一個範例中的查詢來源，請 [尋找預設段落樣式](find-default-paragraph-style.md)。</span><span class="sxs-lookup"><span data-stu-id="54899-112">This expression is similar to the source of the query in the previous example, [Find the default paragraph style](find-default-paragraph-style.md).</span></span> <span data-ttu-id="54899-113">主要差異在於，這個運算式使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸而非 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="54899-113">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="54899-114">查詢會使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸，因為在具有章節的檔中，段落不會是本文專案的直接子系，而是在階層中的兩個層級。</span><span class="sxs-lookup"><span data-stu-id="54899-114">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs won't be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="54899-115">藉由使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸，無論檔是否使用區段，程式碼都會運作。</span><span class="sxs-lookup"><span data-stu-id="54899-115">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work whether or not the document uses sections.</span></span>

## <a name="example-use-a-let-clause-to-determine-the-element-that-contains-the-style-node"></a><span data-ttu-id="54899-116">範例：使用 `let` 子句來判斷包含樣式節點的元素</span><span class="sxs-lookup"><span data-stu-id="54899-116">Example: Use a `let` clause to determine the element that contains the style node</span></span>

<span data-ttu-id="54899-117">下列查詢 `let` 會使用子句來判斷包含樣式節點的元素：</span><span class="sxs-lookup"><span data-stu-id="54899-117">The following query uses a `let` clause to determine the element that contains the style node:</span></span>

```csharp
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()
```

 ```vb
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()
```

<span data-ttu-id="54899-118">`let` `Let` Visual Basic 版本中的子句 () 先使用 <xref:System.Xml.Linq.XContainer.Elements%2A> 軸來尋找名為的所有專案 `pPr` ，然後使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法來尋找所有名為的子項目， `pStyle` 最後使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準查詢運算子將集合轉換成 singleton。</span><span class="sxs-lookup"><span data-stu-id="54899-118">The `let` clause (`Let` in the Visual Basic version) first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="54899-119">如果集合是空的， `styleNode` 會 `null` `Nothing` 在 Visual Basic 版本) 中設定為 (。</span><span class="sxs-lookup"><span data-stu-id="54899-119">If the collection is empty, `styleNode` is set to `null` (`Nothing` in the Visual Basic version).</span></span> <span data-ttu-id="54899-120">若要尋找 `pStyle` 下階節點，這是相當實用的慣用句。</span><span class="sxs-lookup"><span data-stu-id="54899-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="54899-121">請注意，如果 `pPr` 子節點不存在，程式碼就不會擲回例外狀況，而是 `styleNode` 設定為 `null` (`Nothing`) ，這是此 `let` () 子句的所需行為 `Let` 。</span><span class="sxs-lookup"><span data-stu-id="54899-121">Note that if the `pPr` child node doesn't exist, the code doesn't fail by throwing an exception; instead, `styleNode` is set to `null` (`Nothing`), which is the desired behavior of this `let`(`Let`) clause.</span></span>

<span data-ttu-id="54899-122">如果沒有元素，則 `styleNode` 會設定為 `null` (`Nothing`) 。</span><span class="sxs-lookup"><span data-stu-id="54899-122">If there is no element, then `styleNode` is set to `null` (`Nothing`).</span></span>

<span data-ttu-id="54899-123">此查詢會使用兩個成員 (`StyleName` 和 `ParagraphNode`) 規劃一組匿名型別。</span><span class="sxs-lookup"><span data-stu-id="54899-123">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>

## <a name="example-retrieve-the-paragraph-nodes-from-a-wordprocessingml-document"></a><span data-ttu-id="54899-124">範例：從 WordprocessingML 檔取出段落節點</span><span class="sxs-lookup"><span data-stu-id="54899-124">Example: Retrieve the paragraph nodes from a WordprocessingML document</span></span>

<span data-ttu-id="54899-125">此範例會處理 WordprocessingML 檔，以抓取段落節點。</span><span class="sxs-lookup"><span data-stu-id="54899-125">This example processes a WordprocessingML document, retrieving the paragraph nodes.</span></span> <span data-ttu-id="54899-126">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="54899-126">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="54899-127">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="54899-127">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="54899-128">新的查詢會在以下程式碼的註解中叫出。</span><span class="sxs-lookup"><span data-stu-id="54899-128">The new query is called out in comments in the code below.</span></span>

<span data-ttu-id="54899-129">建立此範例之來源文件的指示，位於 [建立來源 Office OPEN XML 檔](create-source-office-open-xml-document.md)中。</span><span class="sxs-lookup"><span data-stu-id="54899-129">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="54899-130">這個範例會使用在 WindowsBase 組件中找到的類別。</span><span class="sxs-lookup"><span data-stu-id="54899-130">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="54899-131">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="54899-131">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

```csharp
const string fileName = "SampleDoc.docx";

const string documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";
const string stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";
const string wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main";
XNamespace w = wordmlNamespace;

XDocument xDoc = null;
XDocument styleDoc = null;

using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))
{
    PackageRelationship docPackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();
    if (docPackageRelationship != null)
    {
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative), docPackageRelationship.TargetUri);
        PackagePart documentPart = wdPackage.GetPart(documentUri);

        //  Load the document XML in the part into an XDocument instance.
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));

        //  Find the styles part. There will only be one.
        PackageRelationship styleRelation = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();
        if (styleRelation != null)
        {
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);
            PackagePart stylePart = wdPackage.GetPart(styleUri);

            //  Load the style XML in the part into an XDocument instance.
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));
        }
    }
}

string defaultStyle =
    (string)(
        from style in styleDoc.Root.Elements(w + "style")
        where (string)style.Attribute(w + "type") == "paragraph"&&
              (string)style.Attribute(w + "default") == "1"
              select style
    ).First().Attribute(w + "styleId");

// Following is the new query that finds all paragraphs in the
// document and their styles.
var paragraphs =
    from para in xDoc
                 .Root
                 .Element(w + "body")
                 .Descendants(w + "p")
    let styleNode = para
                    .Elements(w + "pPr")
                    .Elements(w + "pStyle")
                    .FirstOrDefault()
    select new
    {
        ParagraphNode = para,
        StyleName = styleNode != null ?
            (string)styleNode.Attribute(w + "val") :
            defaultStyle
    };

foreach (var p in paragraphs)
    Console.WriteLine("StyleName:{0}", p.StyleName);
```

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">

Module Module1
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String
        If (styleNode Is Nothing) Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"

        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If (styleRelation IsNot Nothing) Then
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    '  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        Dim defaultStyle As String = _
            ( _
                From style In styleDoc.Root.<w:style> _
                Where style.@w:type = "paragraph" And _
                      style.@w:default = "1" _
                Select style _
            ).First().@w:styleId

        ' Following is the new query that finds all paragraphs in the
        ' document and their styles.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        For Each p In paragraphs
            Console.WriteLine("StyleName:{0}", p.StyleName)
        Next

    End Sub
End Module
```

<span data-ttu-id="54899-132">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="54899-132">This example produces the following output:</span></span>

```output
StyleName:Heading1
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Code
StyleName:Normal
StyleName:Normal
StyleName:Normal
StyleName:Code
```

<span data-ttu-id="54899-133">本教學課程的下一篇文章會示範如何建立查詢來取出段落的文字：</span><span class="sxs-lookup"><span data-stu-id="54899-133">The next article in this tutorial shows how to create a query to retrieve the text of paragraphs:</span></span>

- [<span data-ttu-id="54899-134">取出段落的文字</span><span class="sxs-lookup"><span data-stu-id="54899-134">Retrieve the text of the paragraphs</span></span>](retrieve-text-paragraphs.md)

## <a name="see-also"></a><span data-ttu-id="54899-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54899-135">See also</span></span>

- [<span data-ttu-id="54899-136">教學課程：操作 WordprocessingML 檔中的內容</span><span class="sxs-lookup"><span data-stu-id="54899-136">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
