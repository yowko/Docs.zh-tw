---
title: "使用純虛擬函式進行重構 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3aba03afe75f0ef30a709d6a65ee03d56c13c820
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="c2e5a-102">使用純虛擬函式進行重構 (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e5a-102">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="c2e5a-103">下列範例會重構上述範例 ([使用擴充方法進行重構 (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)) 來使用此範例中的純虛擬函式，而且尋找段落文字的程式碼會被移到純靜態方法 `ParagraphText`。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-103">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md), to use a pure function In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2e5a-104">範例</span><span class="sxs-lookup"><span data-stu-id="c2e5a-104">Example</span></span>  
 <span data-ttu-id="c2e5a-105">此範例會處理 WordprocessingML 文件，並從 WordprocessingML 文件擷取段落節點。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-105">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="c2e5a-106">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-106">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="c2e5a-107">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="c2e5a-108">重構的程式碼會在以下程式碼的註解中叫出。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-108">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="c2e5a-109">如需建立此範例之來源文件的指示，請參閱[建立來源 Office Open XML 文件 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](../../../../csharp/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="c2e5a-110">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-110">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="c2e5a-111">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="c2e5a-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
    // This is a new method that assembles the paragraph text.  
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
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri,  
                      styleRelation.TargetUri);  
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
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="c2e5a-112">此範例會產生與重構前相同的輸出：</span><span class="sxs-lookup"><span data-stu-id="c2e5a-112">This example produces the same output as before the refactoring:</span></span>  
  
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
  
### <a name="next-steps"></a><span data-ttu-id="c2e5a-113">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c2e5a-113">Next Steps</span></span>  
 <span data-ttu-id="c2e5a-114">下一個範例顯示如何將 XML 規劃為不同的組織結構：</span><span class="sxs-lookup"><span data-stu-id="c2e5a-114">The next example shows how to project XML into a different shape:</span></span>  
  
-   [<span data-ttu-id="c2e5a-115">以不同的組織結構投影 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e5a-115">Projecting XML in a Different Shape (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2e5a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2e5a-116">See Also</span></span>  
 [<span data-ttu-id="c2e5a-117">教學課程：管理 WordprocessingML 文件中的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e5a-117">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="c2e5a-118">使用擴充方法進行重構 (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e5a-118">Refactoring Using an Extension Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
 [<span data-ttu-id="c2e5a-119">重構為純虛擬函式 (C#)</span><span class="sxs-lookup"><span data-stu-id="c2e5a-119">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
