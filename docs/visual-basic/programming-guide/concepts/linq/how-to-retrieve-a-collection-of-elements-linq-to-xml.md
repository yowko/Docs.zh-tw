---
title: 如何： 擷取項目 (LINQ to XML) 的集合 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 7ebc33ec8d1901ecb795f63b2fd9812d1acba347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a>如何： 擷取項目 (LINQ to XML) 的集合 (Visual Basic)
這個主題會示範 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。 此方法會擷取項目之子項目的集合。  
  
## <a name="example"></a>範例  
 此範例會逐一查看 `purchaseOrder` 項目的子項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 此範例會產生下列輸出。  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
