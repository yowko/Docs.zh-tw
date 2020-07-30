---
title: 以不同的組織結構投影 XML (C#)
description: 瞭解如何以不同于來源 XML 的圖形來投影 XML。 請參閱使用來自 WindowsBase 元件之類別的程式碼範例。
ms.date: 07/20/2015
ms.assetid: 4cb6b14a-32dc-4a2a-813e-bf9368fa8d86
ms.openlocfilehash: 492c0671b6a81f7e6b8d5f93698f84b88b14bd23
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299093"
---
# <a name="projecting-xml-in-a-different-shape-c"></a><span data-ttu-id="4779c-104">以不同的組織結構投影 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4779c-104">Projecting XML in a Different Shape (C#)</span></span>
<span data-ttu-id="4779c-105">本主題顯示以不同於來源 XML 的組織結構規劃 XML 的範例。</span><span class="sxs-lookup"><span data-stu-id="4779c-105">This topic shows an example of projecting XML that is in a different shape than the source XML.</span></span>  
  
 <span data-ttu-id="4779c-106">許多典型的 XML 轉換都包含鏈結的查詢，如此範例中所示。</span><span class="sxs-lookup"><span data-stu-id="4779c-106">Many typical XML transformations consist of chained queries, as in this example.</span></span> <span data-ttu-id="4779c-107">常見的狀況是，從特定格式的 XML 開始，將中繼結果規劃為匿名型別或具名型別的集合，最後再將結果規劃回完全不同於來源 XML 之組織結構的 XML。</span><span class="sxs-lookup"><span data-stu-id="4779c-107">It is common to start with some form of XML, project intermediate results as collections of anonymous types or named types, and then finally to project the results back into XML that is in an entirely different shape than the source XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4779c-108">範例</span><span class="sxs-lookup"><span data-stu-id="4779c-108">Example</span></span>  
 <span data-ttu-id="4779c-109">此範例會處理 WordprocessingML 文件，並從 WordprocessingML 文件擷取段落節點。</span><span class="sxs-lookup"><span data-stu-id="4779c-109">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="4779c-110">它也可以識別每個段落的樣式和文字。</span><span class="sxs-lookup"><span data-stu-id="4779c-110">It also identifies the style and text of each paragraph.</span></span> <span data-ttu-id="4779c-111">最後，此範例會使用不同的組織結構規劃 XML。</span><span class="sxs-lookup"><span data-stu-id="4779c-111">Finally, the example projects XML with a different shape.</span></span> <span data-ttu-id="4779c-112">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="4779c-112">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="4779c-113">進行規劃的新陳述式會在以下程式碼的註解中叫出。</span><span class="sxs-lookup"><span data-stu-id="4779c-113">The new statement that does the projection is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="4779c-114">如需建立此範例之來源文件的指示，請參閱[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="4779c-114">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="4779c-115">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="4779c-115">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="4779c-116">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="4779c-116">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
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
                    Uri styleUri =  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
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
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        // The following is the new code that projects XML in a new shape.  
        XElement root = new XElement("Root",  
            from p in paraWithText  
            select new XElement("Paragraph",  
                new XElement("StyleName", p.StyleName),  
                new XElement("Text", p.Text)  
            )  
        );  
  
        Console.WriteLine(root);  
    }  
}  
```  
  
 <span data-ttu-id="4779c-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4779c-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Paragraph>  
    <StyleName>Heading1</StyleName>  
    <Text>Parsing WordprocessingML with LINQ to XML</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>The following example prints to the console.</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>using System;</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>class Program {</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    public static void (string[] args) {</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>        Console.WriteLine("Hello World");</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    }</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>}</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>This example produces the following output:</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>Hello World</Text>  
  </Paragraph>  
</Root>  
```  
  
## <a name="next-steps"></a><span data-ttu-id="4779c-118">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4779c-118">Next Steps</span></span>  
 <span data-ttu-id="4779c-119">在下一個範例中，您將在 Word 文件中進行查詢以尋找所有文字：</span><span class="sxs-lookup"><span data-stu-id="4779c-119">In the next example, you'll query to find all the text in a Word document:</span></span>  
  
- [<span data-ttu-id="4779c-120">尋找 Word 文件中的文字 (C#)</span><span class="sxs-lookup"><span data-stu-id="4779c-120">Finding Text in Word Documents (C#)</span></span>](./finding-text-in-word-documents.md)  
  