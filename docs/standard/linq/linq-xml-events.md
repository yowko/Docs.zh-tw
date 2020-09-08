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
# <a name="linq-to-xml-events-linq-to-xml"></a>LINQ to XML 事件 (LINQ to XML) 

LINQ to XML 事件可讓您在 XML 樹狀結構遭到更改時收到通知。

您可以將事件加入任何的任何實例 <xref:System.Xml.Linq.XObject> 。 接著，事件處理常式將會收到修改該 <xref:System.Xml.Linq.XObject> 及其任何子代的事件。 例如，您可以將事件處理常式加入到樹狀結構的根目錄，並從該事件處理常式處理樹狀結構的所有修改。

如需 LINQ to XML 事件的範例，請參閱 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 。

## <a name="types-and-events"></a>類型和事件

使用事件時，您可以使用下列型別：

|類型|描述|
|----------|-----------------|
|<xref:System.Xml.Linq.XObjectChange>|引發 <xref:System.Xml.Linq.XObject> 的事件時，指定事件型別。|
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。|

修改 XML 樹狀結構時，會引發下列事件：

|事件|描述|
|-----------|-----------------|
|<xref:System.Xml.Linq.XObject.Changing>|只會在此 <xref:System.Xml.Linq.XObject> 或其任何子代即將變更前發生。|
|<xref:System.Xml.Linq.XObject.Changed>|<xref:System.Xml.Linq.XObject> 已變更時或其任何子代已變更時發生。|

## <a name="example-use-events-to-maintain-a-proper-total-when-items-are-changed"></a>範例：在專案變更時使用事件來維持適當的總計

當您想要維護 XML 樹狀結構中的特定彙總資訊時，這些事件相當實用。 例如，您可能會想要維護髮票明細專案總和的發票總計。 此範例使用事件維護複雜項目 `Items` 下，所有子項目的總計。

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

這個範例會產生下列輸出：

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
