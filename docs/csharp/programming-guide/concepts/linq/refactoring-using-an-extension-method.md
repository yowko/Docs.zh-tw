---
title: 使用擴充方法進行重構 (C#)
description: 瞭解如何使用擴充方法來重構程式碼。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
ms.assetid: c5fc123d-af10-4a2f-b8e4-db921efb2639
ms.openlocfilehash: e786f0e1514156535fd6a6033e37ed8879e99709
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381940"
---
# <a name="refactoring-using-an-extension-method-c"></a><span data-ttu-id="198ec-104">使用擴充方法進行重構 (C#)</span><span class="sxs-lookup"><span data-stu-id="198ec-104">Refactoring Using an Extension Method (C#)</span></span>
<span data-ttu-id="198ec-105">這個範例是根據上述範例 ([擷取段落的文字 (C#)](./retrieving-the-text-of-the-paragraphs.md)) 所建置，方法是使用當成擴充方法實作的純虛擬函式來重構字串的串連。</span><span class="sxs-lookup"><span data-stu-id="198ec-105">This example builds on the previous example, [Retrieving the Text of the Paragraphs (C#)](./retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="198ec-106">前一個範例使用 <xref:System.Linq.Enumerable.Aggregate%2A> 標準查詢運算子，將多個字串串連到一個字串。</span><span class="sxs-lookup"><span data-stu-id="198ec-106">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="198ec-107">不過，撰寫擴充方法來執行這個動作更為方便，因為所產生的查詢更小而且更簡單。</span><span class="sxs-lookup"><span data-stu-id="198ec-107">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="198ec-108">範例</span><span class="sxs-lookup"><span data-stu-id="198ec-108">Example</span></span>  
 <span data-ttu-id="198ec-109">這個範例會處理 WordprocessingML 文件，以擷取段落、每個段落的樣式，以及每個段落的文字。</span><span class="sxs-lookup"><span data-stu-id="198ec-109">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="198ec-110">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="198ec-110">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="198ec-111">此範例包含 `StringConcatenate` 方法的多個多載。</span><span class="sxs-lookup"><span data-stu-id="198ec-111">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="198ec-112">您可以在[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md) 中找到建立此範例之來源文件的指示。</span><span class="sxs-lookup"><span data-stu-id="198ec-112">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="198ec-113">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="198ec-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="198ec-114">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="198ec-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
```  
  
## <a name="example"></a><span data-ttu-id="198ec-115">範例</span><span class="sxs-lookup"><span data-stu-id="198ec-115">Example</span></span>  
 <span data-ttu-id="198ec-116">`StringConcatenate` 方法的多載有四個。</span><span class="sxs-lookup"><span data-stu-id="198ec-116">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="198ec-117">一個多載只採用一個字串集合並傳回單一字串。</span><span class="sxs-lookup"><span data-stu-id="198ec-117">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="198ec-118">另一個多載可以採用任何型別的集合，然後將該專案從集合的單一子句委派到字串。</span><span class="sxs-lookup"><span data-stu-id="198ec-118">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="198ec-119">還有其他兩個多載可讓您指定分隔符號字串。</span><span class="sxs-lookup"><span data-stu-id="198ec-119">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="198ec-120">下列程式碼會使用全部四個多載。</span><span class="sxs-lookup"><span data-stu-id="198ec-120">The following code uses all four overloads.</span></span>  
  
```csharp  
string[] numbers = { "one", "two", "three" };  
  
Console.WriteLine("{0}", numbers.StringConcatenate());  
Console.WriteLine("{0}", numbers.StringConcatenate(":"));  
  
int[] intNumbers = { 1, 2, 3 };  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString()));  
Console.WriteLine("{0}", intNumbers.StringConcatenate(i => i.ToString(), ":"));  
```  
  
 <span data-ttu-id="198ec-121">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="198ec-121">This example produces the following output:</span></span>  
  
```output  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="198ec-122">範例</span><span class="sxs-lookup"><span data-stu-id="198ec-122">Example</span></span>  
 <span data-ttu-id="198ec-123">現在可以修改範例以利用新的擴充方法：</span><span class="sxs-lookup"><span data-stu-id="198ec-123">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
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
                Text = para  
                       .ParagraphNode  
                       .Elements(w + "r")  
                       .Elements(w + "t")  
                       .StringConcatenate(e => (string)e)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="198ec-124">這個範例會在套用至[建立來源 Office Open XML 文件 (C#)](./creating-the-source-office-open-xml-document.md) 中所述的文件時產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="198ec-124">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
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
  
 <span data-ttu-id="198ec-125">請注意，這個重構是重構到純虛擬函式的變數。</span><span class="sxs-lookup"><span data-stu-id="198ec-125">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="198ec-126">下一個主題將更詳細介紹重構到純虛擬函式的概念。</span><span class="sxs-lookup"><span data-stu-id="198ec-126">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="198ec-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="198ec-127">Next Steps</span></span>  
 <span data-ttu-id="198ec-128">下一個範例顯示如何使用純虛擬函式，以另一種方式重構此程式碼：</span><span class="sxs-lookup"><span data-stu-id="198ec-128">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="198ec-129">使用純虛擬函式進行重構 (C#)</span><span class="sxs-lookup"><span data-stu-id="198ec-129">Refactoring Using a Pure Function (C#)</span></span>](./refactoring-using-a-pure-function.md)
  
## <a name="see-also"></a><span data-ttu-id="198ec-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="198ec-130">See also</span></span>

- [<span data-ttu-id="198ec-131">教學課程：管理 WordprocessingML 文件中的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="198ec-131">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
- [<span data-ttu-id="198ec-132">重構為純虛擬函式 (C#)</span><span class="sxs-lookup"><span data-stu-id="198ec-132">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
