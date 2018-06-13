---
title: 如何：從 XmlReader 串流 XML 片段 (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 8e2baed3ca32ea4273993fe5bed43fef768204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321060"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="26992-102">如何：從 XmlReader 串流 XML 片段 (C#)</span><span class="sxs-lookup"><span data-stu-id="26992-102">How to: Stream XML Fragments from an XmlReader (C#)</span></span>
<span data-ttu-id="26992-103">當您必須處理大型 XML 檔案時，可能無法將整個 XML 樹狀載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="26992-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="26992-104">這個主題顯示如何使用 <xref:System.Xml.XmlReader> 串流片段。</span><span class="sxs-lookup"><span data-stu-id="26992-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="26992-105">使用 <xref:System.Xml.XmlReader> 讀取 <xref:System.Xml.Linq.XElement> 物件的其中一個最有效方式為，撰寫您自己自訂的座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="26992-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="26992-106">座標軸方法通常會傳回集合，例如，<xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，如本主題的範例中所示。</span><span class="sxs-lookup"><span data-stu-id="26992-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="26992-107">在自訂座標軸方法中，呼叫 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法來建立 XML 片段後，使用 `yield return` 傳回集合。</span><span class="sxs-lookup"><span data-stu-id="26992-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="26992-108">這會將延後執行語意 (Semantics) 提供給您自訂的座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="26992-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="26992-109">當您從 <xref:System.Xml.XmlReader> 物件建立 XML 樹狀結構時，<xref:System.Xml.XmlReader> 必須定位在項目上。</span><span class="sxs-lookup"><span data-stu-id="26992-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="26992-110"><xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法在讀取項目的關閉標記前不會傳回。</span><span class="sxs-lookup"><span data-stu-id="26992-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="26992-111">如果您要建立部分樹狀結構，您可以具現化 <xref:System.Xml.XmlReader>、將讀取器定位在您要轉換為 <xref:System.Xml.Linq.XElement> 樹狀結構的節點上，然後建立 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="26992-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="26992-112">[如何：串流 XML 片段並存取標頭資訊 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) 主題包含如何串流更複雜文件的資訊與範例。</span><span class="sxs-lookup"><span data-stu-id="26992-112">The topic [How to: Stream XML Fragments with Access to Header Information (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="26992-113">[如何：執行大型 XML 文件的串流轉換 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) 主題包含使用 LINQ to XML 轉換非常大的 XML 文件，同時維護小的記憶體使用量的範例。</span><span class="sxs-lookup"><span data-stu-id="26992-113">The topic [How to: Perform Streaming Transform of Large XML Documents (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26992-114">範例</span><span class="sxs-lookup"><span data-stu-id="26992-114">Example</span></span>  
 <span data-ttu-id="26992-115">這個範例會建立自訂座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="26992-115">This example creates a custom axis method.</span></span> <span data-ttu-id="26992-116">您可以使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢進行查詢。</span><span class="sxs-lookup"><span data-stu-id="26992-116">You can query it by using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="26992-117">自訂座標軸方法  `StreamRootChildDoc` 是一種方法，特別針對讀取具有重複 `Child` 項目的文件而設計。</span><span class="sxs-lookup"><span data-stu-id="26992-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 <span data-ttu-id="26992-118">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="26992-118">This example produces the following output:</span></span>  
  
```  
bbb  
ccc  
```  
  
 <span data-ttu-id="26992-119">在此範例中，來源文件很小。</span><span class="sxs-lookup"><span data-stu-id="26992-119">In this example, the source document is very small.</span></span> <span data-ttu-id="26992-120">但是，即使有數百萬的 `Child` 元素，此範例的記憶體使用量還是很小。</span><span class="sxs-lookup"><span data-stu-id="26992-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26992-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="26992-121">See Also</span></span>  
 [<span data-ttu-id="26992-122">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="26992-122">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
