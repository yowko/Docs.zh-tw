---
title: 如何取出單一子項目-LINQ to XML
description: '取出具有指定名稱的第一個子項目。 您可以在 c # 中使用 System.xml.linq.xcontainer.elements，並在 Visual Basic 中使用陣列索引子標記法。'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552704"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a>如何擷取單一子元素 (LINQ to XML)

本文說明如何取出單一子項目，也就是具有指定名稱的第一個子專案。 在 c # 中，您可以使用方法來完成這項作業 <xref:System.Xml.Linq.XContainer.Element%2A> 。 在 Visual Basic 您可以使用陣列索引子標記法來進行。

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a>範例：取出具有指定名稱的第一個元素

下列範例會 `DeliveryNotes` 從範例 xml 檔中的 xml 檔抓取第一個元素 [：典型的採購訂單](sample-xml-file-typical-purchase-order.md)。

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

這個範例會產生下列輸出：

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a>範例：從命名空間中的 XML 取得

下列範例會執行與上述範例相同的動作，但針對命名空間中的 XML 執行這項操作。 它會使用 XML [檔範例 xml 檔：命名空間中的典型採購訂單](sample-xml-file-typical-purchase-order-namespace.md)。 如需命名空間的詳細資訊，請參閱 [命名空間總覽](namespaces-overview.md)。

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim e As XElement = po.<aw:DeliveryNotes>(0)
        Console.WriteLine(e)
    End Sub
End Module
```

這個範例會產生下列輸出：

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a>另請參閱

- [LINQ to XML 軸總覽](linq-xml-axes-overview.md)
