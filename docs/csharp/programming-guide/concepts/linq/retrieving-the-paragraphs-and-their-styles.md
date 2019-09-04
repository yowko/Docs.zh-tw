---
title: 擷取段落及其樣式 (C#)
ms.date: 07/20/2015
ms.assetid: c2f767f8-57b1-4b4b-af04-89ffb1f7067d
ms.openlocfilehash: ec59ef0ac36f8691ca93a4c21c5379118ee0491f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253065"
---
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a><span data-ttu-id="5db55-102">擷取段落及其樣式 (C#)</span><span class="sxs-lookup"><span data-stu-id="5db55-102">Retrieving the Paragraphs and Their Styles (C#)</span></span>
<span data-ttu-id="5db55-103">在此範例中，我們會撰寫一個從 WordprocessingML 文件擷取段落節點的查詢。</span><span class="sxs-lookup"><span data-stu-id="5db55-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="5db55-104">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="5db55-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="5db55-105">這個查詢是根據上述範例 ([尋找預設段落樣式 (C#)](./finding-the-default-paragraph-style.md)) 中的查詢所建置，該範例會從樣式清單擷取預設的樣式。</span><span class="sxs-lookup"><span data-stu-id="5db55-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="5db55-106">系統需要這個資訊，讓查詢可以識別沒有明確設定樣式之段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="5db55-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="5db55-107">段落樣式是透過 `w:pPr` 項目設定的；如果段落不包含這個項目，則會格式化為預設樣式。</span><span class="sxs-lookup"><span data-stu-id="5db55-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="5db55-108">本主題說明某些查詢片段的重要性，然後將查詢顯示為完整、實用範例的一部分。</span><span class="sxs-lookup"><span data-stu-id="5db55-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5db55-109">範例</span><span class="sxs-lookup"><span data-stu-id="5db55-109">Example</span></span>  
 <span data-ttu-id="5db55-110">在文件及其樣式中擷取所有段落之查詢的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="5db55-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 <span data-ttu-id="5db55-111">這個運算式類似上述範例 ([尋找預設段落樣式 (C#)](./finding-the-default-paragraph-style.md)) 中的查詢來源。</span><span class="sxs-lookup"><span data-stu-id="5db55-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (C#)](./finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="5db55-112">主要差異在於，這個運算式使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸而非 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="5db55-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="5db55-113">該查詢使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸是因為在具有章節的文件中，段落將不會是本文項目的直接子系，而會在階層中的兩個層級下。</span><span class="sxs-lookup"><span data-stu-id="5db55-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="5db55-114">藉由使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸，不管文件是否使用章節，程式碼都可以運作。</span><span class="sxs-lookup"><span data-stu-id="5db55-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5db55-115">範例</span><span class="sxs-lookup"><span data-stu-id="5db55-115">Example</span></span>  
 <span data-ttu-id="5db55-116">此查詢使用 `let` 子句來判斷包含樣式節點的項目。</span><span class="sxs-lookup"><span data-stu-id="5db55-116">The query uses a `let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="5db55-117">如果沒有項目，則 `styleNode` 會設定為 `null`：</span><span class="sxs-lookup"><span data-stu-id="5db55-117">If there is no element, then `styleNode` is set to `null`:</span></span>  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 <span data-ttu-id="5db55-118">`let` 子句會先使用 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸來尋找名稱為 `pPr` 的所有項目，然後使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法來尋找名稱為 `pStyle` 的所有子項目，最後使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準查詢運算子，將集合轉換為單一子句。</span><span class="sxs-lookup"><span data-stu-id="5db55-118">The `let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="5db55-119">如果集合是空的，`styleNode` 會設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5db55-119">If the collection is empty, `styleNode` is set to `null`.</span></span> <span data-ttu-id="5db55-120">若要尋找 `pStyle` 下階節點，這是相當實用的慣用句。</span><span class="sxs-lookup"><span data-stu-id="5db55-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="5db55-121">請注意，如果 `pPr` 子節點不存在，擲出例外狀況不會讓程式碼失敗；但是，`styleNode` 會設定為 `null`，這是此 `let` 子句所需的行為。</span><span class="sxs-lookup"><span data-stu-id="5db55-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `null`, which is the desired behavior of this `let` clause.</span></span>  
  
 <span data-ttu-id="5db55-122">此查詢會使用兩個成員 (`StyleName` 和 `ParagraphNode`) 規劃一組匿名型別。</span><span class="sxs-lookup"><span data-stu-id="5db55-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5db55-123">範例</span><span class="sxs-lookup"><span data-stu-id="5db55-123">Example</span></span>  
 <span data-ttu-id="5db55-124">此範例會處理 WordprocessingML 文件，並從 WordprocessingML 文件擷取段落節點。</span><span class="sxs-lookup"><span data-stu-id="5db55-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="5db55-125">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="5db55-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="5db55-126">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="5db55-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="5db55-127">新的查詢會在以下程式碼的註解中叫出。</span><span class="sxs-lookup"><span data-stu-id="5db55-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="5db55-128">您可以在[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md) 中找到建立此範例之來源文件的指示。</span><span class="sxs-lookup"><span data-stu-id="5db55-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="5db55-129">這個範例會使用在 WindowsBase 組件中找到的類別。</span><span class="sxs-lookup"><span data-stu-id="5db55-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="5db55-130">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="5db55-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="5db55-131">這個範例會在套用至[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md) 中所述的文件時產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="5db55-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
## <a name="next-steps"></a><span data-ttu-id="5db55-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5db55-132">Next Steps</span></span>  
 <span data-ttu-id="5db55-133">在下個主題 ([擷取段落的文字 (C#)](./retrieving-the-text-of-the-paragraphs.md)) 中，將會建立查詢以擷取下一個段落的文字。</span><span class="sxs-lookup"><span data-stu-id="5db55-133">In the next topic, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db55-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5db55-134">See also</span></span>

- [<span data-ttu-id="5db55-135">教學課程：管理 WordprocessingML 文件中的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="5db55-135">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
