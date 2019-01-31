---
title: HOW TO：擷取單一子項目 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: edb13ab043e7b7ffa2fb749fa6009727a43454bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672977"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>HOW TO：擷取單一子項目 (LINQ to XML) (C#)
這個主題會說明如何擷取單一子項目 (如果有子項目的名稱)。 當您知道子項目的名稱，而且只有一個項目擁有這個名稱，只擷取一個項目 (而不是擷取一個集合) 可能很方便。  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> 方法會使用指定的 <xref:System.Xml.Linq.XElement>，傳回第一個子系 <xref:System.Xml.Linq.XName>。  
  
 如果您要在 Visual Basic 中擷取單一子項目，常用的方法是使用 XML 屬性，然後使用陣列索引子標記法擷取第一個項目。  
  
## <a name="example"></a>範例  
 下列範例示範 <xref:System.Xml.Linq.XContainer.Element%2A> 方法的用法。 此範例會採用名稱為 `po` 的 XML 樹狀結構，並尋找名稱為 `Comment` 的第一個項目。  
  
 Visual Basic 範例會顯示使用陣列索引子標記法來擷取單一項目。  
  
 此範例使用下列 XML 文件：[XML 範例檔：典型訂購單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同程式碼。 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 此範例使用下列 XML 文件：[XML 範例檔：命名空間中的典型訂購單](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)。  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML 座標軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
