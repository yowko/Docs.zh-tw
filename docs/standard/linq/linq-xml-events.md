---
title: LINQ to XML 事件-LINQ to XML
description: 瞭解如何使用 XML 事件來監視 XML 樹狀結構的變更。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 755aa1a449e873a2c4f5b17d4df3eee7ecfa9969
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552233"
---
# <a name="linq-to-xml-events-linq-to-xml"></a><span data-ttu-id="03ca9-103">LINQ to XML 事件 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="03ca9-103">LINQ to XML Events (LINQ to XML)</span></span>

<span data-ttu-id="03ca9-104">LINQ to XML 事件可讓您在 XML 樹狀結構遭到更改時收到通知。</span><span class="sxs-lookup"><span data-stu-id="03ca9-104">LINQ to XML events enable you to be notified when an XML tree is altered.</span></span>

<span data-ttu-id="03ca9-105">您可以將事件加入任何的任何實例 <xref:System.Xml.Linq.XObject> 。</span><span class="sxs-lookup"><span data-stu-id="03ca9-105">You can add events to any instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="03ca9-106">接著，事件處理常式將會收到修改該 <xref:System.Xml.Linq.XObject> 及其任何子代的事件。</span><span class="sxs-lookup"><span data-stu-id="03ca9-106">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="03ca9-107">例如，您可以將事件處理常式加入到樹狀結構的根目錄，並從該事件處理常式處理樹狀結構的所有修改。</span><span class="sxs-lookup"><span data-stu-id="03ca9-107">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>

<span data-ttu-id="03ca9-108">如需 LINQ to XML 事件的範例，請參閱 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 。</span><span class="sxs-lookup"><span data-stu-id="03ca9-108">For examples of LINQ to XML events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>

## <a name="types-and-events"></a><span data-ttu-id="03ca9-109">類型和事件</span><span class="sxs-lookup"><span data-stu-id="03ca9-109">Types and events</span></span>

<span data-ttu-id="03ca9-110">使用事件時，您可以使用下列型別：</span><span class="sxs-lookup"><span data-stu-id="03ca9-110">You use the following types when working with events:</span></span>

|<span data-ttu-id="03ca9-111">類型</span><span class="sxs-lookup"><span data-stu-id="03ca9-111">Type</span></span>|<span data-ttu-id="03ca9-112">描述</span><span class="sxs-lookup"><span data-stu-id="03ca9-112">Description</span></span>|
|----------|-----------------|
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="03ca9-113">引發 <xref:System.Xml.Linq.XObject> 的事件時，指定事件型別。</span><span class="sxs-lookup"><span data-stu-id="03ca9-113">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="03ca9-114">提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="03ca9-114">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|

<span data-ttu-id="03ca9-115">修改 XML 樹狀結構時，會引發下列事件：</span><span class="sxs-lookup"><span data-stu-id="03ca9-115">The following events are raised when you modify an XML tree:</span></span>

|<span data-ttu-id="03ca9-116">事件</span><span class="sxs-lookup"><span data-stu-id="03ca9-116">Event</span></span>|<span data-ttu-id="03ca9-117">描述</span><span class="sxs-lookup"><span data-stu-id="03ca9-117">Description</span></span>|
|-----------|-----------------|
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="03ca9-118">只會在此 <xref:System.Xml.Linq.XObject> 或其任何子代即將變更前發生。</span><span class="sxs-lookup"><span data-stu-id="03ca9-118">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="03ca9-119"><xref:System.Xml.Linq.XObject> 已變更時或其任何子代已變更時發生。</span><span class="sxs-lookup"><span data-stu-id="03ca9-119">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|

## <a name="example-use-events-to-maintain-a-proper-total-when-items-are-changed"></a><span data-ttu-id="03ca9-120">範例：在專案變更時使用事件來維持適當的總計</span><span class="sxs-lookup"><span data-stu-id="03ca9-120">Example: Use events to maintain a proper total when items are changed</span></span>

<span data-ttu-id="03ca9-121">當您想要維護 XML 樹狀結構中的特定彙總資訊時，這些事件相當實用。</span><span class="sxs-lookup"><span data-stu-id="03ca9-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="03ca9-122">例如，您可能會想要維護髮票明細專案總和的發票總計。</span><span class="sxs-lookup"><span data-stu-id="03ca9-122">For example, you may want to maintain an invoice total that's the sum of the line items of the invoice.</span></span> <span data-ttu-id="03ca9-123">此範例使用事件維護複雜項目 `Items` 下，所有子項目的總計。</span><span class="sxs-lookup"><span data-stu-id="03ca9-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>

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

```vb
Module Module1
    Dim WithEvents items As XElement = Nothing
    Dim total As XElement = Nothing
    Dim root As XElement = _
            <Root>
                <Total>0</Total>
                <Items></Items>
            </Root>

    Private Sub XObjectChanged( _
            ByVal sender As Object, _
            ByVal cea As XObjectChangeEventArgs) _
            Handles items.Changed
        Select Case cea.ObjectChange
            Case XObjectChange.Add
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) + _
                            CInt((DirectCast(sender, XText)).Value))
                End If
            Case XObjectChange.Remove
                If sender.GetType() Is GetType(XElement) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XElement)).Value))
                End If
                If sender.GetType() Is GetType(XText) Then
                    total.Value = CStr(CInt(total.Value) - _
                            CInt((DirectCast(sender, XText)).Value))
                End If
        End Select
        Console.WriteLine("Changed {0} {1}", _
                            sender.GetType().ToString(), _
                            cea.ObjectChange.ToString())
    End Sub

    Sub Main()
        total = root.<Total>(0)
        items = root.<Items>(0)
        items.SetElementValue("Item1", 25)
        items.SetElementValue("Item2", 50)
        items.SetElementValue("Item2", 75)
        items.SetElementValue("Item3", 133)
        items.SetElementValue("Item1", Nothing)
        items.SetElementValue("Item4", 100)
        Console.WriteLine("Total:{0}", CInt(total))
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="03ca9-124">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="03ca9-124">This example produces the following output:</span></span>

```output
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
