---
title: '如何在 c # 中執行文字到 XML 的串流轉換-LINQ to XML'
description: 您可以使用一次釋放一行的擴充方法，以串流處理文字檔進行處理。 相較于載入整個檔案然後進行處理的技術，這項技術可減少記憶體需求。
ms.date: 07/20/2015
dev_langs:
- csharp
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 8e0d710d7cbc6de8cc60721c211376a82b6c29fc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552789"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-in-c-linq-to-xml"></a><span data-ttu-id="2cd62-104">如何在 c # 中執行文字到 XML 的串流轉換 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="2cd62-104">How to perform streaming transformations of text to XML in C# (LINQ to XML)</span></span>

<span data-ttu-id="2cd62-105">您可以使用一次釋放一行的擴充方法，以串流處理文字檔進行處理。</span><span class="sxs-lookup"><span data-stu-id="2cd62-105">You can use an extension method that releases a line at a time to stream a text file for processing.</span></span> <span data-ttu-id="2cd62-106">相較于載入整個檔案然後進行處理的技術，這項技術可減少記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="2cd62-106">This technique reduces memory requirements compared to techniques which load the entire file and then process it.</span></span>

<span data-ttu-id="2cd62-107">擴充方法可以使用結構提供這一行 `yield return` 。</span><span class="sxs-lookup"><span data-stu-id="2cd62-107">The extension method can provide the line using the `yield return` construct.</span></span> <span data-ttu-id="2cd62-108">LINQ 查詢可以延遲延遲的方式處理資料流程。</span><span class="sxs-lookup"><span data-stu-id="2cd62-108">A LINQ query can process the stream in a lazy deferred fashion.</span></span> <span data-ttu-id="2cd62-109">如果您使用 <xref:System.Xml.Linq.XStreamingElement> 來串流輸出，則不論來源文字檔的大小為何，您都可以建立從文字檔到 XML 的轉換，使用最少量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="2cd62-109">If you use <xref:System.Xml.Linq.XStreamingElement> to stream output, you can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

> [!NOTE]
> <span data-ttu-id="2cd62-110">在您可以處理整個檔案一次的情況下，最好採用此技術，從來源文件中依序採用這些行。</span><span class="sxs-lookup"><span data-stu-id="2cd62-110">The technique is best applied in situations in which you can process the entire file once, taking the lines in order from the source document.</span></span> <span data-ttu-id="2cd62-111">處理檔案一次以上，或在處理之前進行排序，可減少串流技術的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="2cd62-111">Processing the file more than once, or sorting before processing, reduces the performance benefits of a streaming technique.</span></span>

## <a name="example-use-an-extension-method-to-stream-text"></a><span data-ttu-id="2cd62-112">範例使用擴充方法來串流文字</span><span class="sxs-lookup"><span data-stu-id="2cd62-112">Example Use an extension method to stream text</span></span>

<span data-ttu-id="2cd62-113">此範例會使用下列文字檔（People.txt）作為其來源：</span><span class="sxs-lookup"><span data-stu-id="2cd62-113">The example uses the following text file, People.txt, as its source:</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

<span data-ttu-id="2cd62-114">在範例的程式碼中，擴充方法會 `Lines` 一次提供一行文字：</span><span class="sxs-lookup"><span data-stu-id="2cd62-114">In the code for the example, extension method `Lines` provides the text a line at a time:</span></span>

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
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
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
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

<span data-ttu-id="2cd62-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="2cd62-115">The example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2cd62-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cd62-116">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
