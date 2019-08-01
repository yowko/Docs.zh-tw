---
title: 作法：撰寫具有複雜篩選的查詢 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 0459c9549238257c0a76276a1d10f6d370144214
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709857"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>作法：撰寫具有複雜篩選的查詢 (Visual Basic)
有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。 例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。 本主題提供利用複雜篩選撰寫查詢的範例。  
  
## <a name="example"></a>範例  
 這個範例顯示如何尋找其 `PurchaseOrder` 子項目的 `Address` 屬性等於 "Shipping"，而 `Type` 子項目等於 "NY" 的所有 `State` 項目。 它會在 `Where` 子句中使用巢狀查詢，而且如果集合在其中有任何項目，`Any` 運算子會傳回 `True`。  
  
 此範例使用下列 XML 文件：[XML 範例檔：多個訂購單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
 如需運算子的`Any`詳細資訊, 請參閱數量詞[作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)。  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 此程式碼會產生下列輸出：  
  
```  
99505  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊, 請參閱[命名空間總覽 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)。  
  
 此範例使用下列 XML 文件：[XML 範例檔：命名空間中的多個訂購單](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 此程式碼會產生下列輸出：  
  
```  
99505  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [基本查詢 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [XML 子代軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 屬性 (Attribute) 軸屬性 (Property)](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [投射作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [數量詞作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
