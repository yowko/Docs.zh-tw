---
title: '如何從 XmlReader 串流 XML 片段（c #）'
description: 瞭解如何從 XmlReader 串流 XML 片段。 這個方法是用來處理大型 XML 檔案。
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e35322724712816180d48c1957719cf87079aedd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301017"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a><span data-ttu-id="3a73b-104">如何從 XmlReader 串流 XML 片段（c #）</span><span class="sxs-lookup"><span data-stu-id="3a73b-104">How to stream XML fragments from an XmlReader (C#)</span></span>

<span data-ttu-id="3a73b-105">當您必須處理大型 XML 檔案時，可能無法將整個 XML 樹狀載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="3a73b-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="3a73b-106">這個主題顯示如何使用 <xref:System.Xml.XmlReader> 串流片段。</span><span class="sxs-lookup"><span data-stu-id="3a73b-106">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="3a73b-107">使用 <xref:System.Xml.XmlReader> 讀取 <xref:System.Xml.Linq.XElement> 物件的其中一個最有效方式為，撰寫您自己自訂的座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="3a73b-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="3a73b-108">座標軸方法通常會傳回集合，例如，<xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，如本主題的範例中所示。</span><span class="sxs-lookup"><span data-stu-id="3a73b-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="3a73b-109">在自訂座標軸方法中，呼叫 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法來建立 XML 片段後，使用 `yield return` 傳回集合。</span><span class="sxs-lookup"><span data-stu-id="3a73b-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="3a73b-110">這會將延後執行語意 (Semantics) 提供給您自訂的座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="3a73b-110">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="3a73b-111">當您從 <xref:System.Xml.XmlReader> 物件建立 XML 樹狀結構時，<xref:System.Xml.XmlReader> 必須定位在項目上。</span><span class="sxs-lookup"><span data-stu-id="3a73b-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="3a73b-112"><xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法在讀取項目的關閉標記前不會傳回。</span><span class="sxs-lookup"><span data-stu-id="3a73b-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="3a73b-113">如果您要建立部分樹狀結構，您可以具現化 <xref:System.Xml.XmlReader>、將讀取器定位在您要轉換為 <xref:System.Xml.Linq.XElement> 樹狀結構的節點上，然後建立 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="3a73b-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
<span data-ttu-id="3a73b-114">[如何串流 XML 片段並存取標頭資訊（c #）](./how-to-stream-xml-fragments-with-access-to-header-information.md)主題包含如何串流更複雜檔的資訊和範例。</span><span class="sxs-lookup"><span data-stu-id="3a73b-114">The topic [How to stream XML fragments with access to header information (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>
  
 <span data-ttu-id="3a73b-115">[如何執行大型 xml 檔的串流轉換主題（c #）](./how-to-perform-streaming-transform-of-large-xml-documents.md)包含使用 LINQ to XML 來轉換非常大的 xml 檔，同時維持小型記憶體使用量的範例。</span><span class="sxs-lookup"><span data-stu-id="3a73b-115">The topic [How to perform streaming transform of large XML documents (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a73b-116">範例</span><span class="sxs-lookup"><span data-stu-id="3a73b-116">Example</span></span>  
 <span data-ttu-id="3a73b-117">這個範例會建立自訂座標軸方法。</span><span class="sxs-lookup"><span data-stu-id="3a73b-117">This example creates a custom axis method.</span></span> <span data-ttu-id="3a73b-118">您可以使用 LINQ 查詢來查詢它。</span><span class="sxs-lookup"><span data-stu-id="3a73b-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="3a73b-119">自訂座標軸方法  `StreamRootChildDoc` 是一種方法，特別針對讀取具有重複 `Child` 項目的文件而設計。</span><span class="sxs-lookup"><span data-stu-id="3a73b-119">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="3a73b-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="3a73b-120">This example produces the following output:</span></span>  
  
```output  
bbb  
ccc  
```  
  
 <span data-ttu-id="3a73b-121">在此範例中，來源文件很小。</span><span class="sxs-lookup"><span data-stu-id="3a73b-121">In this example, the source document is very small.</span></span> <span data-ttu-id="3a73b-122">但是，即使有數百萬的 `Child` 元素，此範例的記憶體使用量還是很小。</span><span class="sxs-lookup"><span data-stu-id="3a73b-122">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
