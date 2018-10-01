---
title: LINQ to XML 事件 (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 6308d81eac830e11b6d58f8e460dfa377663cd21
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47230731"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="d8e8b-102">LINQ to XML 事件 (C#)</span><span class="sxs-lookup"><span data-stu-id="d8e8b-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d8e8b-103">事件可讓您在 XML 樹狀結構有所更改時收到通知。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="d8e8b-104">您可以將事件加入到任何 <xref:System.Xml.Linq.XObject> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="d8e8b-105">接著，事件處理常式將會收到修改該 <xref:System.Xml.Linq.XObject> 及其任何子代的事件。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="d8e8b-106">例如，您可以將事件處理常式加入到樹狀結構的根目錄，並從該事件處理常式處理樹狀結構的所有修改。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="d8e8b-107">如需 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件的範例，請參閱 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed>。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="d8e8b-108">型別與事件</span><span class="sxs-lookup"><span data-stu-id="d8e8b-108">Types and Events</span></span>  
 <span data-ttu-id="d8e8b-109">使用事件時，您可以使用下列型別：</span><span class="sxs-lookup"><span data-stu-id="d8e8b-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="d8e8b-110">類型</span><span class="sxs-lookup"><span data-stu-id="d8e8b-110">Type</span></span>|<span data-ttu-id="d8e8b-111">描述</span><span class="sxs-lookup"><span data-stu-id="d8e8b-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="d8e8b-112">引發 <xref:System.Xml.Linq.XObject> 的事件時，指定事件型別。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="d8e8b-113">提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="d8e8b-114">修改 XML 樹狀結構時，會引發下列事件：</span><span class="sxs-lookup"><span data-stu-id="d8e8b-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="d8e8b-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="d8e8b-115">Event</span></span>|<span data-ttu-id="d8e8b-116">描述</span><span class="sxs-lookup"><span data-stu-id="d8e8b-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="d8e8b-117">只會在此 <xref:System.Xml.Linq.XObject> 或其任何子代即將變更前發生。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="d8e8b-118"><xref:System.Xml.Linq.XObject> 已變更時或其任何子代已變更時發生。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d8e8b-119">範例</span><span class="sxs-lookup"><span data-stu-id="d8e8b-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d8e8b-120">描述</span><span class="sxs-lookup"><span data-stu-id="d8e8b-120">Description</span></span>  
 <span data-ttu-id="d8e8b-121">當您想要維護 XML 樹狀結構中的特定彙總資訊時，這些事件相當實用。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="d8e8b-122">例如，您可能想要維護發票明細項目總計的發票總數。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="d8e8b-123">此範例使用事件維護複雜項目 `Items` 下，所有子項目的總計。</span><span class="sxs-lookup"><span data-stu-id="d8e8b-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d8e8b-124">程式碼</span><span class="sxs-lookup"><span data-stu-id="d8e8b-124">Code</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="d8e8b-125">註解</span><span class="sxs-lookup"><span data-stu-id="d8e8b-125">Comments</span></span>  
 <span data-ttu-id="d8e8b-126">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d8e8b-126">This code produces the following output:</span></span>  
  
```  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8e8b-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8e8b-127">See Also</span></span>

- [<span data-ttu-id="d8e8b-128">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="d8e8b-128">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
