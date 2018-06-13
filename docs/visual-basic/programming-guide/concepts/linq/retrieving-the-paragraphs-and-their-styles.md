---
title: 擷取段落及其樣式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 5b8075b5aa05c32d2dc894149a8fa53f103138c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648303"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="13f5d-102">擷取段落及其樣式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13f5d-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="13f5d-103">在此範例中，我們會撰寫一個從 WordprocessingML 文件擷取段落節點的查詢。</span><span class="sxs-lookup"><span data-stu-id="13f5d-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="13f5d-104">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="13f5d-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="13f5d-105">此查詢會根據在前一個範例中，查詢[尋找預設段落樣式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)，抓取的預設樣式的樣式清單。</span><span class="sxs-lookup"><span data-stu-id="13f5d-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="13f5d-106">系統需要這個資訊，讓查詢可以識別沒有明確設定樣式之段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="13f5d-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="13f5d-107">段落樣式是透過 `w:pPr` 項目設定的；如果段落不包含這個項目，則會格式化為預設樣式。</span><span class="sxs-lookup"><span data-stu-id="13f5d-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="13f5d-108">本主題說明某些查詢片段的重要性，然後將查詢顯示為完整、實用範例的一部分。</span><span class="sxs-lookup"><span data-stu-id="13f5d-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f5d-109">範例</span><span class="sxs-lookup"><span data-stu-id="13f5d-109">Example</span></span>  
 <span data-ttu-id="13f5d-110">在文件及其樣式中擷取所有段落之查詢的來源如下所示：</span><span class="sxs-lookup"><span data-stu-id="13f5d-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="13f5d-111">此運算式是類似於在上一個範例中，查詢的來源[尋找預設段落樣式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)。</span><span class="sxs-lookup"><span data-stu-id="13f5d-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="13f5d-112">主要差異在於，這個運算式使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸而非 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。</span><span class="sxs-lookup"><span data-stu-id="13f5d-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="13f5d-113">該查詢使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸是因為在具有章節的文件中，段落將不會是本文項目的直接子系，而會在階層中的兩個層級下。</span><span class="sxs-lookup"><span data-stu-id="13f5d-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="13f5d-114">藉由使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸，不管文件是否使用章節，程式碼都可以運作。</span><span class="sxs-lookup"><span data-stu-id="13f5d-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f5d-115">範例</span><span class="sxs-lookup"><span data-stu-id="13f5d-115">Example</span></span>  
 <span data-ttu-id="13f5d-116">此查詢使用 `Let` 子句來判斷包含樣式節點的項目。</span><span class="sxs-lookup"><span data-stu-id="13f5d-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="13f5d-117">如果沒有項目，則 `styleNode` 會設定為 `Nothing`：</span><span class="sxs-lookup"><span data-stu-id="13f5d-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="13f5d-118">`Let` 子句會先使用 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸來尋找名稱為 `pPr` 的所有項目，然後使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法來尋找名稱為 `pStyle` 的所有子項目，最後使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準查詢運算子，將集合轉換為單一子句。</span><span class="sxs-lookup"><span data-stu-id="13f5d-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="13f5d-119">如果集合是空的，`styleNode` 會設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="13f5d-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="13f5d-120">若要尋找 `pStyle` 下階節點，這是相當實用的慣用句。</span><span class="sxs-lookup"><span data-stu-id="13f5d-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="13f5d-121">請注意，如果 `pPr` 子節點不存在，擲出例外狀況不會讓程式碼失敗；但是，`styleNode` 會設定為 `Nothing`，這是此 `Let` 子句所需的行為。</span><span class="sxs-lookup"><span data-stu-id="13f5d-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="13f5d-122">此查詢會使用兩個成員 (`StyleName` 和 `ParagraphNode`) 規劃一組匿名型別。</span><span class="sxs-lookup"><span data-stu-id="13f5d-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f5d-123">範例</span><span class="sxs-lookup"><span data-stu-id="13f5d-123">Example</span></span>  
 <span data-ttu-id="13f5d-124">此範例會處理 WordprocessingML 文件，並從 WordprocessingML 文件擷取段落節點。</span><span class="sxs-lookup"><span data-stu-id="13f5d-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="13f5d-125">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="13f5d-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="13f5d-126">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="13f5d-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="13f5d-127">新的查詢會在以下程式碼的註解中叫出。</span><span class="sxs-lookup"><span data-stu-id="13f5d-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="13f5d-128">您可以找到建立此範例中的來源文件的指示[建立來源 Office Open XML 文件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="13f5d-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="13f5d-129">這個範例會使用在 WindowsBase 組件中找到的類別。</span><span class="sxs-lookup"><span data-stu-id="13f5d-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="13f5d-130">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="13f5d-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="13f5d-131">這個範例會產生下列輸出時套用至文件中所述[建立來源 Office Open XML 文件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="13f5d-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
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
  
## <a name="next-steps"></a><span data-ttu-id="13f5d-132">後續步驟</span><span class="sxs-lookup"><span data-stu-id="13f5d-132">Next Steps</span></span>  
 <span data-ttu-id="13f5d-133">在下一個主題中，[擷取段落 (Visual Basic) 的文字](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)，您將建立查詢以擷取段落的文字。</span><span class="sxs-lookup"><span data-stu-id="13f5d-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f5d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13f5d-134">See Also</span></span>  
 [<span data-ttu-id="13f5d-135">教學課程： 操作 WordprocessingML 文件 (Visual Basic) 中的內容</span><span class="sxs-lookup"><span data-stu-id="13f5d-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
