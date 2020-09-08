---
title: 使用純虛擬函式進行重構-LINQ to XML
description: 瞭解如何使用純虛擬函式進行重構
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a3416a45-9e12-4e4a-9747-897f06eef510
ms.openlocfilehash: 68d21b2ba3c2dbb353d86b84c6ea0cd1b3b6d3bc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552788"
---
# <a name="refactor-using-a-pure-function-linq-to-xml"></a><span data-ttu-id="f910e-103">使用純虛擬函式重構 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="f910e-103">Refactor using a pure function (LINQ to XML)</span></span>

<span data-ttu-id="f910e-104">下列範例會重構先前的範例， [使用擴充方法進行重構](refactor-extension-method.md)，以使用純虛擬函式。</span><span class="sxs-lookup"><span data-stu-id="f910e-104">The following example refactors the previous example, [Refactor using an extension method](refactor-extension-method.md), to use a pure function.</span></span> <span data-ttu-id="f910e-105">它會將尋找段落文字的程式碼移到純靜態方法 `ParagraphText` 。</span><span class="sxs-lookup"><span data-stu-id="f910e-105">It moves the code that finds the text of a paragraph to the pure static method `ParagraphText`.</span></span>

## <a name="example-retrieve-the-paragraph-nodes-and-their-styles"></a><span data-ttu-id="f910e-106">範例：取出段落節點及其樣式</span><span class="sxs-lookup"><span data-stu-id="f910e-106">Example: Retrieve the paragraph nodes and their styles</span></span>

<span data-ttu-id="f910e-107">此範例會處理 WordprocessingML 檔，以抓取段落節點。</span><span class="sxs-lookup"><span data-stu-id="f910e-107">This example processes a WordprocessingML document, retrieving the paragraph nodes.</span></span> <span data-ttu-id="f910e-108">它也可以識別每個段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="f910e-108">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="f910e-109">此範例在這個教學課程中，會在先前的範例上建置。</span><span class="sxs-lookup"><span data-stu-id="f910e-109">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="f910e-110">重構的程式碼會在以下程式碼的註解中叫出。</span><span class="sxs-lookup"><span data-stu-id="f910e-110">The refactored code is called out in comments in the code below.</span></span>

<span data-ttu-id="f910e-111">建立此範例之來源文件的指示，位於 [建立來源 Office OPEN XML 檔](create-source-office-open-xml-document.md)中。</span><span class="sxs-lookup"><span data-stu-id="f910e-111">The instructions for creating the source document for this example are in [Create the source Office Open XML document](create-source-office-open-xml-document.md).</span></span>

<span data-ttu-id="f910e-112">這個範例會使用 WindowsBase 組件的類別。</span><span class="sxs-lookup"><span data-stu-id="f910e-112">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="f910e-113">它會使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="f910e-113">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>

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

```vb
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String
        Dim sb = New StringBuilder()
        For Each s In source
            sb.Append(s)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String)) As String
        Dim sb = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item))
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal separator As String) As String
        Dim sb = New StringBuilder()
        For Each s As T In source
            sb.Append(s).Append(separator)
        Next
        Return sb.ToString()
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _
    ByVal func As Func(Of T, String), ByVal separator As String) As String
        Dim sb = New StringBuilder()
        For Each item As T In source
            sb.Append(func(item)).Append(separator)
        Next
        Return sb.ToString()
    End Function

    ' This is a new method that assembles the paragraph text.
    Public Function ParagraphText(ByVal e As XElement) As String
        Dim w = e.Name.Namespace
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))
    End Function

    ' Following function is required because Visual Basic doesn't support short circuit evaluation
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _
                                         ByVal defaultStyle As String) As String
        If styleNode Is Nothing Then
            Return defaultStyle
        Else
            Return styleNode.@w:val
        End If
    End Function

    Sub Main()
        Dim fileName = "SampleDoc.docx"

        Dim documentRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"
        Dim stylesRelationshipType = _
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"
        Dim wordmlNamespace = _
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"
        Dim xDoc As XDocument = Nothing
        Dim styleDoc As XDocument = Nothing

        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)
            Dim docPackageRelationship As PackageRelationship = _
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()
            If (docPackageRelationship IsNot Nothing) Then
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _
                  docPackageRelationship.TargetUri)
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)

                '  Load the document XML in the part into an XDocument instance.
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))

                '  Find the styles part. There will only be one.
                Dim styleRelation As PackageRelationship = _
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()
                If styleRelation IsNot Nothing Then
                    Dim styleUri As Uri = _
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)

                    '  Load the style XML in the part into an XDocument instance.
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))
                End If
            End If
        End Using

        Dim defaultStyle = _
            ( _
                From style In styleDoc.Root.<w:style> _
                Where style.@w:type = "paragraph" And _
                      style.@w:default = "1" _
                Select style _
            ).First().@w:styleId

        ' Find all paragraphs in the document.
        Dim paragraphs = _
            From para In xDoc.Root.<w:body>...<w:p> _
        Let styleNode = para.<w:pPr>.<w:pStyle>.FirstOrDefault _
        Select New With { _
            .ParagraphNode = para, _
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _
        }

        ' Retrieve the text of each paragraph.
        Dim paraWithText = _
            From para In paragraphs _
            Select New With { _
                .ParagraphNode = para.ParagraphNode, _
                .StyleName = para.StyleName, _
                .Text = ParagraphText(para.ParagraphNode) _
            }

        For Each p In paraWithText
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)
        Next
    End Sub
End Module
```

<span data-ttu-id="f910e-114">此範例會產生與重構前相同的輸出：</span><span class="sxs-lookup"><span data-stu-id="f910e-114">This example produces the same output as before the refactoring:</span></span>

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

```output
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<
StyleName:Normal ><
StyleName:Normal >The following example prints to the console.<
StyleName:Normal ><
StyleName:Code >Imports System<
StyleName:Code ><
StyleName:Code >Class Program<
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<
StyleName:Code >        Console.WriteLine("Hello World")<
StyleName:Code >   End Sub<
StyleName:Code >End Class<
StyleName:Normal ><
StyleName:Normal >This example produces the following output:<
StyleName:Normal ><
StyleName:Code >Hello World<
```

<span data-ttu-id="f910e-115">本教學課程的下一篇文章會示範如何將 XML 投影至不同的圖形：</span><span class="sxs-lookup"><span data-stu-id="f910e-115">The next article in this tutorial shows how to project XML into a different shape:</span></span>

- [<span data-ttu-id="f910e-116">不同圖形中的專案 XML</span><span class="sxs-lookup"><span data-stu-id="f910e-116">Project XML in a different shape</span></span>](project-xml-different-shape.md)

## <a name="see-also"></a><span data-ttu-id="f910e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f910e-117">See also</span></span>

- [<span data-ttu-id="f910e-118">教學課程：操作 WordprocessingML 檔中的內容</span><span class="sxs-lookup"><span data-stu-id="f910e-118">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
- [<span data-ttu-id="f910e-119">使用擴充方法重構</span><span class="sxs-lookup"><span data-stu-id="f910e-119">Refactor using an extension method</span></span>](refactor-extension-method.md)
- [<span data-ttu-id="f910e-120">重構為純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="f910e-120">Refactor into pure functions</span></span>](refactor-pure-functions.md)
