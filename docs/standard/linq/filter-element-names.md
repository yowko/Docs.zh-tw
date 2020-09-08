---
title: 如何篩選元素名稱-LINQ to XML
description: 瞭解如何在呼叫會傳回 System.xml.linq.xelement> 之 IEnumerable 的方法時，篩選元素名稱。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 1f831fe0008c94b3956e93f3ced7176d8c0bf34e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552105"
---
# <a name="how-to-filter-on-element-names-linq-to-xml"></a>如何篩選項目名稱 (LINQ to XML)

當您呼叫可傳回 <xref:System.Collections.Generic.IEnumerable%601> 之 <xref:System.Xml.Linq.XElement> 的其中一個方法時，您可以篩選項目名稱。

## <a name="example-retrieve-descendants-filtered-to-a-specified-name"></a>範例：取出已篩選為指定名稱的子系

此範例會抓取已篩選成隻包含具有指定名稱之子系的子系集合。

這個範例會使用 XML [檔範例 xml 檔：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> items =
    from el in po.Descendants("ProductName")
    select el;
foreach(XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string) prdName);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim items As IEnumerable(Of XElement) = _
    From el In po...<ProductName> _
    Select el
For Each prdName As XElement In items
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
Next
```

這個範例會產生下列輸出：

```output
ProductName:Lawnmower
ProductName:Baby Monitor
```

其他傳回 <xref:System.Collections.Generic.IEnumerable%601> 集合之 <xref:System.Xml.Linq.XElement> 的方法都依照相同的模式。 它們的簽章類似於 <xref:System.Xml.Linq.XContainer.Elements%2A> 及 <xref:System.Xml.Linq.XContainer.Descendants%2A>。 下列是具有類似方法簽章之方法的完整清單：

- <xref:System.Xml.Linq.XNode.Ancestors%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a>範例：從命名空間中的 XML 取得

下列範例顯示命名空間中的相同 XML 查詢。 如需詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

此範例會使用 XML [檔範例 xml 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-namespace.md)。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
IEnumerable<XElement> items =
    from el in po.Descendants(aw + "ProductName")
    select el;
foreach (XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string)prdName);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim items As IEnumerable(Of XElement) = _
            From el In po...<aw:ProductName> _
            Select el
        For Each prdName As XElement In items
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
        Next
    End Sub
End Module
```

這個範例會產生下列輸出：

```output
{http://www.adventure-works.com}ProductName:Lawnmower
{http://www.adventure-works.com}ProductName:Baby Monitor
```

## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸總覽](linq-xml-axes-overview.md)
