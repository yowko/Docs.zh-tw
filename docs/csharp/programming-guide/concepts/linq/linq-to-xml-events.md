---
title: "LINQ to XML 事件 (C#) | Microsoft Docs"
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
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 174c7dbc26d38efb8faec2d2d68468d7d8bea588
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="18a9c-102">LINQ to XML 事件 (C#)</span><span class="sxs-lookup"><span data-stu-id="18a9c-102">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="18a9c-103"> 事件可讓您在 XML 樹狀結構有所更改時收到通知。</span><span class="sxs-lookup"><span data-stu-id="18a9c-103"> events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="18a9c-104">您可以將事件新增至任何 <xref:System.Xml.Linq.XObject> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="18a9c-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="18a9c-105">事件處理常式即會收到該 <xref:System.Xml.Linq.XObject> 及其任何子系的修改事件。</span><span class="sxs-lookup"><span data-stu-id="18a9c-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="18a9c-106">例如，您可以將事件處理常式加入到樹狀結構的根目錄，並從該事件處理常式處理樹狀結構的所有修改。</span><span class="sxs-lookup"><span data-stu-id="18a9c-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="18a9c-107">如需 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 事件的範例，請參閱 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed>。</span><span class="sxs-lookup"><span data-stu-id="18a9c-107">For examples of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="18a9c-108">型別與事件</span><span class="sxs-lookup"><span data-stu-id="18a9c-108">Types and Events</span></span>  
 <span data-ttu-id="18a9c-109">使用事件時，您可以使用下列型別：</span><span class="sxs-lookup"><span data-stu-id="18a9c-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="18a9c-110">類型</span><span class="sxs-lookup"><span data-stu-id="18a9c-110">Type</span></span>|<span data-ttu-id="18a9c-111">描述</span><span class="sxs-lookup"><span data-stu-id="18a9c-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="18a9c-112"><xref:System.Xml.Linq.XObjectChange></span><span class="sxs-lookup"><span data-stu-id="18a9c-112"><xref:System.Xml.Linq.XObjectChange></span></span>|<span data-ttu-id="18a9c-113">指定引發 <xref:System.Xml.Linq.XObject> 事件時的事件類型。</span><span class="sxs-lookup"><span data-stu-id="18a9c-113">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<span data-ttu-id="18a9c-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></span><span class="sxs-lookup"><span data-stu-id="18a9c-114"><xref:System.Xml.Linq.XObjectChangeEventArgs></span></span>|<span data-ttu-id="18a9c-115">提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="18a9c-115">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="18a9c-116">修改 XML 樹狀結構時，會引發下列事件：</span><span class="sxs-lookup"><span data-stu-id="18a9c-116">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="18a9c-117">事件</span><span class="sxs-lookup"><span data-stu-id="18a9c-117">Event</span></span>|<span data-ttu-id="18a9c-118">描述</span><span class="sxs-lookup"><span data-stu-id="18a9c-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18a9c-119"><xref:System.Xml.Linq.XObject.Changing></span><span class="sxs-lookup"><span data-stu-id="18a9c-119"><xref:System.Xml.Linq.XObject.Changing></span></span>|<span data-ttu-id="18a9c-120">只會在此 <xref:System.Xml.Linq.XObject> 或其任何子系即將變更前發生。</span><span class="sxs-lookup"><span data-stu-id="18a9c-120">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<span data-ttu-id="18a9c-121"><xref:System.Xml.Linq.XObject.Changed></span><span class="sxs-lookup"><span data-stu-id="18a9c-121"><xref:System.Xml.Linq.XObject.Changed></span></span>|<span data-ttu-id="18a9c-122"><xref:System.Xml.Linq.XObject> 已變更或其任何子系已變更時發生。</span><span class="sxs-lookup"><span data-stu-id="18a9c-122">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="18a9c-123">範例</span><span class="sxs-lookup"><span data-stu-id="18a9c-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="18a9c-124">描述</span><span class="sxs-lookup"><span data-stu-id="18a9c-124">Description</span></span>  
 <span data-ttu-id="18a9c-125">當您想要維護 XML 樹狀結構中的特定彙總資訊時，這些事件相當實用。</span><span class="sxs-lookup"><span data-stu-id="18a9c-125">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="18a9c-126">例如，您可能想要維護發票明細項目總計的發票總數。</span><span class="sxs-lookup"><span data-stu-id="18a9c-126">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="18a9c-127">此範例使用事件維護複雜項目 `Items` 下，所有子項目的總計。</span><span class="sxs-lookup"><span data-stu-id="18a9c-127">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="18a9c-128">程式碼</span><span class="sxs-lookup"><span data-stu-id="18a9c-128">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="18a9c-129">註解</span><span class="sxs-lookup"><span data-stu-id="18a9c-129">Comments</span></span>  
 <span data-ttu-id="18a9c-130">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="18a9c-130">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18a9c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18a9c-131">See Also</span></span>  
 [<span data-ttu-id="18a9c-132">進階 LINQ to XML 程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="18a9c-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
