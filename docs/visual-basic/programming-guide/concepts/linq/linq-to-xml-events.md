---
title: LINQ to XML 事件 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 34923928-b99c-4004-956e-38f6db25e910
ms.openlocfilehash: dcdaf321cfb75ca77e1d8b3f5a541a9418c3f512
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823333"
---
# <a name="linq-to-xml-events-visual-basic"></a><span data-ttu-id="96f2e-102">LINQ to XML 事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96f2e-102">LINQ to XML Events (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="96f2e-103">事件可讓您在 XML 樹狀結構有所更改時收到通知。</span><span class="sxs-lookup"><span data-stu-id="96f2e-103">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="96f2e-104">您可以將事件加入到任何 <xref:System.Xml.Linq.XObject> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="96f2e-104">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="96f2e-105">接著，事件處理常式將會收到修改該 <xref:System.Xml.Linq.XObject> 及其任何子代的事件。</span><span class="sxs-lookup"><span data-stu-id="96f2e-105">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="96f2e-106">例如，您可以將事件處理常式加入到樹狀結構的根目錄，並從該事件處理常式處理樹狀結構的所有修改。</span><span class="sxs-lookup"><span data-stu-id="96f2e-106">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="96f2e-107">如需 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件的範例，請參閱 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed>。</span><span class="sxs-lookup"><span data-stu-id="96f2e-107">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="96f2e-108">型別與事件</span><span class="sxs-lookup"><span data-stu-id="96f2e-108">Types and Events</span></span>  
 <span data-ttu-id="96f2e-109">使用事件時，您可以使用下列型別：</span><span class="sxs-lookup"><span data-stu-id="96f2e-109">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="96f2e-110">類型</span><span class="sxs-lookup"><span data-stu-id="96f2e-110">Type</span></span>|<span data-ttu-id="96f2e-111">描述</span><span class="sxs-lookup"><span data-stu-id="96f2e-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="96f2e-112">引發 <xref:System.Xml.Linq.XObject> 的事件時，指定事件型別。</span><span class="sxs-lookup"><span data-stu-id="96f2e-112">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="96f2e-113">提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="96f2e-113">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="96f2e-114">修改 XML 樹狀結構時，會引發下列事件：</span><span class="sxs-lookup"><span data-stu-id="96f2e-114">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="96f2e-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="96f2e-115">Event</span></span>|<span data-ttu-id="96f2e-116">描述</span><span class="sxs-lookup"><span data-stu-id="96f2e-116">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="96f2e-117">只會在此 <xref:System.Xml.Linq.XObject> 或其任何子代即將變更前發生。</span><span class="sxs-lookup"><span data-stu-id="96f2e-117">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="96f2e-118"><xref:System.Xml.Linq.XObject> 已變更時或其任何子代已變更時發生。</span><span class="sxs-lookup"><span data-stu-id="96f2e-118">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96f2e-119">範例</span><span class="sxs-lookup"><span data-stu-id="96f2e-119">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="96f2e-120">描述</span><span class="sxs-lookup"><span data-stu-id="96f2e-120">Description</span></span>  
 <span data-ttu-id="96f2e-121">當您想要維護 XML 樹狀結構中的特定彙總資訊時，這些事件相當實用。</span><span class="sxs-lookup"><span data-stu-id="96f2e-121">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="96f2e-122">例如，您可能想要維護發票明細項目總計的發票總數。</span><span class="sxs-lookup"><span data-stu-id="96f2e-122">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="96f2e-123">此範例使用事件維護複雜項目 `Items` 下，所有子項目的總計。</span><span class="sxs-lookup"><span data-stu-id="96f2e-123">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="96f2e-124">程式碼</span><span class="sxs-lookup"><span data-stu-id="96f2e-124">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="96f2e-125">註解</span><span class="sxs-lookup"><span data-stu-id="96f2e-125">Comments</span></span>  
 <span data-ttu-id="96f2e-126">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="96f2e-126">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96f2e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96f2e-127">See also</span></span>

- [<span data-ttu-id="96f2e-128">進階的 LINQ to XML 程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96f2e-128">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
