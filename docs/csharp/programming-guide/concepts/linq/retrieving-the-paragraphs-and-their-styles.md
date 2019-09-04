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
# <a name="retrieving-the-paragraphs-and-their-styles-c"></a>擷取段落及其樣式 (C#)
在此範例中，我們會撰寫一個從 WordprocessingML 文件擷取段落節點的查詢。 它也可以識別每個段落的樣式。  
  
 這個查詢是根據上述範例 ([尋找預設段落樣式 (C#)](./finding-the-default-paragraph-style.md)) 中的查詢所建置，該範例會從樣式清單擷取預設的樣式。 系統需要這個資訊，讓查詢可以識別沒有明確設定樣式之段落的樣式。 段落樣式是透過 `w:pPr` 項目設定的；如果段落不包含這個項目，則會格式化為預設樣式。  
  
 本主題說明某些查詢片段的重要性，然後將查詢顯示為完整、實用範例的一部分。  
  
## <a name="example"></a>範例  
 在文件及其樣式中擷取所有段落之查詢的來源如下所示：  
  
```csharp  
xDoc.Root.Element(w + "body").Descendants(w + "p")  
```  
  
 這個運算式類似上述範例 ([尋找預設段落樣式 (C#)](./finding-the-default-paragraph-style.md)) 中的查詢來源。 主要差異在於，這個運算式使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸而非 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。 該查詢使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸是因為在具有章節的文件中，段落將不會是本文項目的直接子系，而會在階層中的兩個層級下。 藉由使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸，不管文件是否使用章節，程式碼都可以運作。  
  
## <a name="example"></a>範例  
 此查詢使用 `let` 子句來判斷包含樣式節點的項目。 如果沒有項目，則 `styleNode` 會設定為 `null`：  
  
```csharp  
let styleNode = para.Elements(w + "pPr").Elements(w + "pStyle").FirstOrDefault()  
```  
  
 `let` 子句會先使用 <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸來尋找名稱為 `pPr` 的所有項目，然後使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法來尋找名稱為 `pStyle` 的所有子項目，最後使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準查詢運算子，將集合轉換為單一子句。 如果集合是空的，`styleNode` 會設定為 `null`。 若要尋找 `pStyle` 下階節點，這是相當實用的慣用句。 請注意，如果 `pPr` 子節點不存在，擲出例外狀況不會讓程式碼失敗；但是，`styleNode` 會設定為 `null`，這是此 `let` 子句所需的行為。  
  
 此查詢會使用兩個成員 (`StyleName` 和 `ParagraphNode`) 規劃一組匿名型別。  
  
## <a name="example"></a>範例  
 此範例會處理 WordprocessingML 文件，並從 WordprocessingML 文件擷取段落節點。 它也可以識別每個段落的樣式。 此範例在這個教學課程中，會在先前的範例上建置。 新的查詢會在以下程式碼的註解中叫出。  
  
 您可以在[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md) 中找到建立此範例之來源文件的指示。  
  
 這個範例會使用在 WindowsBase 組件中找到的類別。 它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。  
  
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
  
 這個範例會在套用至[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md) 中所述的文件時產生下列輸出。  
  
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
  
## <a name="next-steps"></a>後續步驟  
 在下個主題 ([擷取段落的文字 (C#)](./retrieving-the-text-of-the-paragraphs.md)) 中，將會建立查詢以擷取下一個段落的文字。  
  
## <a name="see-also"></a>另請參閱

- [教學課程：管理 WordprocessingML 文件中的內容 (C#)](./shape-of-wordprocessingml-documents.md)
