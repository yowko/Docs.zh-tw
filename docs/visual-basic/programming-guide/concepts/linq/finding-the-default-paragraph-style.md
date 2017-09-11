---
title: "尋找預設段落樣式 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 22d97c95a1dec52c0290555daeedce51c5a567e3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="b0658-102">尋找預設段落樣式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0658-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="b0658-103">管理中的資訊 WordprocessingML 文件教學課程的第一個工作是文件中找到的預設段落樣式。</span><span class="sxs-lookup"><span data-stu-id="b0658-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0658-104">範例</span><span class="sxs-lookup"><span data-stu-id="b0658-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b0658-105">描述</span><span class="sxs-lookup"><span data-stu-id="b0658-105">Description</span></span>  
 <span data-ttu-id="b0658-106">下列範例會開啟 Office Open XML WordprocessingML 文件、尋找文件和封裝的樣式部分，然後執行尋找預設樣式名稱的查詢。</span><span class="sxs-lookup"><span data-stu-id="b0658-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="b0658-107">如需 Office Open XML 文件封裝和組件，其中包含的資訊，請參閱[詳細資料的 Office Open XML WordprocessingML 文件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)。</span><span class="sxs-lookup"><span data-stu-id="b0658-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="b0658-108">查詢會尋找名稱為 `w:style` 的節點，其中擁有名稱為 `w:type` 且值為 "paragraph" 的屬性，同時也擁有名稱為 `w:default` 且值為 "1" 的屬性。</span><span class="sxs-lookup"><span data-stu-id="b0658-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="b0658-109">因為會有這些屬性只有一個 XML 節點，此查詢會使用<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName>運算子，將集合轉換為單一子句。</xref:System.Linq.Enumerable.First%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b0658-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=fullName> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="b0658-110">接著，它會取得名稱為 `w:styleId` 之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b0658-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="b0658-111">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="b0658-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="b0658-112">它會使用中的型別<xref:System.IO.Packaging?displayProperty=fullName>命名空間。</xref:System.IO.Packaging?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b0658-112">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b0658-113">程式碼</span><span class="sxs-lookup"><span data-stu-id="b0658-113">Code</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="b0658-114">註解</span><span class="sxs-lookup"><span data-stu-id="b0658-114">Comments</span></span>  
 <span data-ttu-id="b0658-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b0658-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="b0658-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b0658-116">Next Steps</span></span>  
 <span data-ttu-id="b0658-117">在下一個範例中，您將建立在文件及其樣式中尋找所有段落的類似查詢︰</span><span class="sxs-lookup"><span data-stu-id="b0658-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="b0658-118">擷取段落及其樣式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0658-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="b0658-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0658-119">See Also</span></span>  
 [<span data-ttu-id="b0658-120">教學課程︰ 操作 WordprocessingML 文件 (Visual Basic) 中的內容</span><span class="sxs-lookup"><span data-stu-id="b0658-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
