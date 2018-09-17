---
title: 擷取段落的文字 (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 1d23addb4c4c1ea17343585392fbe08fef08568a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45658505"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a>擷取段落的文字 (C#)
這個範例是根據上述範例 ([擷取段落及其樣式 (C#)](../../../../csharp/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)) 所建置。 這個新的範例會將每個段落的文字當做字串擷取。  
  
 若要擷取文字，此範例可加入逐一查看匿名型別之集合的其他查詢，並規劃加入新成員 `Text` 之匿名型別的新集合。 它會使用 <xref:System.Linq.Enumerable.Aggregate%2A> 標準查詢運算子，將多個字串串連到一個字串。  
  
 此技術 (也就是，先規劃為匿名型別的集合，然後使用此集合規劃為匿名型別的新集合) 是實用的常見慣用句。 在沒有規劃為第一個匿名型別的情況下，可能已經撰寫這個查詢。 不過，因為延遲評估的緣故，這麼做不會使用太多額外的處理電源。 此慣用句會在堆積上建立更多短期存在的物件，但實質上，這不會降低效能。  
  
 當然，此慣用句可能會撰寫包含功能的單一查詢以擷取段落、每個段落的樣式，以及每個段落的文字。 不過，這通常有助於將更複雜的查詢分割為多個查詢，因為所產生的程式碼更為模組化而且更容易維護。 此外，如果您需要重複使用某部分查詢，當查詢以此種方式撰寫時，重構比較容易。  
  
 這些鏈結在一起的查詢會使用在[教學課程：將查詢鏈結在一起 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) 主題中詳細檢查的處理模型。  
  
## <a name="example"></a>範例  
 此範例會處理 WordprocessingML 文件，以判斷項目節點、樣式名稱，以及每個段落的文字。 此範例在這個教學課程中，會在先前的範例上建置。 新的查詢會在以下程式碼的註解中叫出。  
  
 如需建立此範例之來源文件的指示，請參閱[建立來源 Office Open XML 文件 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)。  
  
 這個範例會使用 WindowsBase 組件的類別。 它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
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
  
// Find all paragraphs in the document.  
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
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 這個範例會在套用至[建立來源 Office Open XML 文件 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md) 中所述的文件時產生下列輸出。  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a>後續步驟  
 下一個範例顯示如何使用擴充方法 (而非 <xref:System.Linq.Enumerable.Aggregate%2A>)，將多個字串串連到一個字串。  
  
-   [使用擴充方法進行重構 (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a>請參閱

- [教學課程：管理 WordprocessingML 文件中的內容 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
- [LINQ to XML 中的延後執行和延遲評估 (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
