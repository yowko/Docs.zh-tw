---
title: HOW TO：擷取項目的集合 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: fef12745bd608622f071f72049f242405d17ed7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253425"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>作法：擷取項目的集合 (LINQ to XML) (C#)
這個主題會示範 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。 此方法會擷取項目之子項目的集合。  
  
## <a name="example"></a>範例  
 此範例會逐一查看 `purchaseOrder` 項目的子項目。  
  
 此範例使用下列 XML 文件：[XML 範例檔：典型訂購單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 此範例會產生下列輸出。  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML 座標軸 (C#)](./linq-to-xml-axes-overview.md)
