---
title: 擷取段落及其樣式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
ms.openlocfilehash: 3c6554c44c95db13aada0d9edf96cc2df595c6d1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816937"
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>擷取段落及其樣式 (Visual Basic)
在此範例中，我們會撰寫一個從 WordprocessingML 文件擷取段落節點的查詢。 它也可以識別每個段落的樣式。  
  
 此查詢是根據在上一個範例中，查詢[尋找預設段落樣式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)，表示從樣式清單擷取預設樣式。 系統需要這個資訊，讓查詢可以識別沒有明確設定樣式之段落的樣式。 段落樣式是透過 `w:pPr` 項目設定的；如果段落不包含這個項目，則會格式化為預設樣式。  
  
 本主題說明某些查詢片段的重要性，然後將查詢顯示為完整、實用範例的一部分。  
  
## <a name="example"></a>範例  
 在文件及其樣式中擷取所有段落之查詢的來源如下所示：  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 此運算式是類似於在前一個範例中，查詢的來源[尋找預設段落樣式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)。 主要差異在於，這個運算式使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸而非 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。 該查詢使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸是因為在具有章節的文件中，段落將不會是本文項目的直接子系，而會在階層中的兩個層級下。 藉由使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸，不管文件是否使用章節，程式碼都可以運作。  
  
## <a name="example"></a>範例  
 此查詢使用 `Let` 子句來判斷包含樣式節點的項目。 如果沒有項目，則 `styleNode` 會設定為 `Nothing`：  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 `Let` 子句會先使用 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸來尋找名稱為 `pPr` 的所有項目，然後使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法來尋找名稱為 `pStyle` 的所有子項目，最後使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準查詢運算子，將集合轉換為單一子句。 如果集合是空的，`styleNode` 會設定為 `Nothing`。 若要尋找 `pStyle` 下階節點，這是相當實用的慣用句。 請注意，如果 `pPr` 子節點不存在，擲出例外狀況不會讓程式碼失敗；但是，`styleNode` 會設定為 `Nothing`，這是此 `Let` 子句所需的行為。  
  
 此查詢會使用兩個成員 (`StyleName` 和 `ParagraphNode`) 規劃一組匿名型別。  
  
## <a name="example"></a>範例  
 此範例會處理 WordprocessingML 文件，並從 WordprocessingML 文件擷取段落節點。 它也可以識別每個段落的樣式。 此範例在這個教學課程中，會在先前的範例上建置。 新的查詢會在以下程式碼的註解中叫出。  
  
 您可以找到建立此範例中的來源文件的指示[建立來源 Office Open XML 文件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)。  
  
 這個範例會使用在 WindowsBase 組件中找到的類別。 它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。  
  
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
  
 此範例會產生下列輸出時套用至文件中所述[建立來源 Office Open XML 文件 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)。  
  
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
  
## <a name="next-steps"></a>後續步驟  
 在下一個主題中，[擷取段落 (Visual Basic) 的文字](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)，您將建立查詢以擷取段落的文字。  
  
## <a name="see-also"></a>另請參閱

- [教學課程：管理 WordprocessingML 文件 (Visual Basic) 中的內容](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
