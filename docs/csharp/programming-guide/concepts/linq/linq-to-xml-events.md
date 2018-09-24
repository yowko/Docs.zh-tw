---
title: LINQ to XML 事件 (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 6308d81eac830e11b6d58f8e460dfa377663cd21
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46578546"
---
# <a name="linq-to-xml-events-c"></a>LINQ to XML 事件 (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件可讓您在 XML 樹狀結構有所更改時收到通知。  
  
 您可以將事件加入到任何 <xref:System.Xml.Linq.XObject> 的執行個體。 接著，事件處理常式將會收到修改該 <xref:System.Xml.Linq.XObject> 及其任何子代的事件。 例如，您可以將事件處理常式加入到樹狀結構的根目錄，並從該事件處理常式處理樹狀結構的所有修改。  
  
 如需 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件的範例，請參閱 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed>。  
  
## <a name="types-and-events"></a>型別與事件  
 使用事件時，您可以使用下列型別：  
  
|類型|描述|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|引發 <xref:System.Xml.Linq.XObject> 的事件時，指定事件型別。|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。|  
  
 修改 XML 樹狀結構時，會引發下列事件：  
  
|Event - 事件|描述|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|只會在此 <xref:System.Xml.Linq.XObject> 或其任何子代即將變更前發生。|  
|<xref:System.Xml.Linq.XObject.Changed>|<xref:System.Xml.Linq.XObject> 已變更時或其任何子代已變更時發生。|  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 當您想要維護 XML 樹狀結構中的特定彙總資訊時，這些事件相當實用。 例如，您可能想要維護發票明細項目總計的發票總數。 此範例使用事件維護複雜項目 `Items` 下，所有子項目的總計。  
  
### <a name="code"></a>程式碼  
  
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
  
### <a name="comments"></a>註解  
 此程式碼會產生下列輸出：  
  
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
  
## <a name="see-also"></a>請參閱

- [進階 LINQ to XML 程式設計 (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
