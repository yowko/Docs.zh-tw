---
title: 使用純虛擬函式進行重構 (C#)
description: 瞭解如何使用純虛擬函式來重構程式碼。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: a3f0084d9de27f3f215cc3ba527ada93f7a3d61a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300107"
---
# <a name="refactoring-using-a-pure-function-c"></a><span data-ttu-id="37350-104">使用純虛擬函式進行重構 (C#)</span><span class="sxs-lookup"><span data-stu-id="37350-104">Refactoring Using a Pure Function (C#)</span></span>
<span data-ttu-id="37350-105">下列範例會重構先前的範例，[使用擴充方法（c #）進行重構](./refactoring-using-an-extension-method.md)，以使用純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="37350-105">The following example refactors the previous example, [Refactoring Using an Extension Method (C#)](./refactoring-using-an-extension-method.md), to use a pure function.</span></span> <span data-ttu-id="37350-106">在此範例中，用來尋找段落文字的程式碼會移到純靜態方法 `ParagraphText` 。</span><span class="sxs-lookup"><span data-stu-id="37350-106">In this example, the code to find the text of a paragraph is moved to the pure static method `ParagraphText`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37350-107">範例</span><span class="sxs-lookup"><span data-stu-id="37350-107">Example</span></span>  
 <span data-ttu-id="37350-108">此範例會處理 WordprocessingML 文件，並從 WordprocessingML 文件擷取段落節點。</span><span class="sxs-lookup"><span data-stu-id="37350-108">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="37350-109">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="37350-109">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="37350-110">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="37350-110">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="37350-111">重構的程式碼會在以下程式碼的註解中叫出。</span><span class="sxs-lookup"><span data-stu-id="37350-111">The refactored code is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="37350-112">如需建立此範例之來源文件的指示，請參閱[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="37350-112">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="37350-113">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="37350-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="37350-114">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="37350-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
 <span data-ttu-id="37350-115">此範例會產生與重構前相同的輸出：</span><span class="sxs-lookup"><span data-stu-id="37350-115">This example produces the same output as before the refactoring:</span></span>  
  
```output  
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
  
### <a name="next-steps"></a><span data-ttu-id="37350-116">後續步驟</span><span class="sxs-lookup"><span data-stu-id="37350-116">Next Steps</span></span>  
 <span data-ttu-id="37350-117">下一個範例顯示如何將 XML 規劃為不同的組織結構：</span><span class="sxs-lookup"><span data-stu-id="37350-117">The next example shows how to project XML into a different shape:</span></span>  
  
- [<span data-ttu-id="37350-118">以不同的組織結構投影 (C#)</span><span class="sxs-lookup"><span data-stu-id="37350-118">Projecting XML in a Different Shape (C#)</span></span>](./projecting-xml-in-a-different-shape.md)  
  
## <a name="see-also"></a><span data-ttu-id="37350-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37350-119">See also</span></span>

- [<span data-ttu-id="37350-120">教學課程：管理 WordprocessingML 文件中的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="37350-120">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="37350-121">使用擴充方法進行重構 (C#)</span><span class="sxs-lookup"><span data-stu-id="37350-121">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)
- [<span data-ttu-id="37350-122">重構為純虛擬函式 (C#)</span><span class="sxs-lookup"><span data-stu-id="37350-122">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
