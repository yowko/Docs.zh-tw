---
title: '如何取出元素的集合（LINQ to XML）（c #）'
description: 'C # 中的 Elements 方法會抓取元素的子項目集合。 這個 LINQ to XML 範例會逐一查看專案的子項目。'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103360"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>如何取出元素的集合（LINQ to XML）（c #）
這個主題會示範 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。 此方法會擷取項目之子項目的集合。  
  
## <a name="example"></a>範例  
 此範例會逐一查看 `purchaseOrder` 項目的子項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。  
  
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
  
## <a name="see-also"></a>請參閱

- [LINQ to XML 座標軸 (C#)](./linq-to-xml-axes-overview.md)
