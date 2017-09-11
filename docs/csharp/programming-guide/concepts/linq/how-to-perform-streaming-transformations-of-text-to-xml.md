---
title: "如何：執行文字到 XML 的串流轉換 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3351f88bb27807714b3566992242e72a5d03ac14
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="8e7e8-102">如何：執行文字到 XML 的串流轉換 (C#)</span><span class="sxs-lookup"><span data-stu-id="8e7e8-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="8e7e8-103">處理文字檔的其中一個方法是撰寫擴充方法，該方法會使用 `yield return` 建構將文字檔一次串流一行。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="8e7e8-104">然後您可以撰寫利用延後的方式處理文字檔的 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="8e7e8-105">如果您接著使用 <xref:System.Xml.Linq.XStreamingElement> 串流輸出，您就可以使用最少量的記憶體建立文字檔到 XML 的轉換，而不必在乎來源文字檔的大小。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="8e7e8-106">關於串流轉換有一些警告。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="8e7e8-107">在您可以處理一次整個檔案的情況下，以及您可以用行出現在來源文件中的順序處理這些行時，最適合使用串流轉換。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="8e7e8-108">如果您必須多次處理檔案，或者，如果您必須在處理檔案前排序行，您將會失去使用串流技術的好處。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e7e8-109">範例</span><span class="sxs-lookup"><span data-stu-id="8e7e8-109">Example</span></span>  
 <span data-ttu-id="8e7e8-110">下列文字檔 People.txt 為這個範例的來源。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="8e7e8-111">下列程式碼包含的擴充方法可以用延緩的方式，串流文字檔的行。</span><span class="sxs-lookup"><span data-stu-id="8e7e8-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 <span data-ttu-id="8e7e8-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8e7e8-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e7e8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e7e8-113">See Also</span></span>  
 <span data-ttu-id="8e7e8-114"><xref:System.Xml.Linq.XStreamingElement></span><span class="sxs-lookup"><span data-stu-id="8e7e8-114"><xref:System.Xml.Linq.XStreamingElement></span></span>   
 [<span data-ttu-id="8e7e8-115">進階查詢技術 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8e7e8-115">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

