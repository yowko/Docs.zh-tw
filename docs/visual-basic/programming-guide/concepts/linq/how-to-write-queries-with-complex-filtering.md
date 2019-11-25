---
title: 如何：撰寫具有複雜篩選功能的查詢
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 28e84b7785948e9d50c08438494b89c906ab8505
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344448"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>How to: Write Queries with Complex Filtering (Visual Basic)
有時候您會想要利用複雜篩選撰寫 LINQ to XML 查詢。 例如，您可能必須尋找其子項目包含特定名稱和值的所有項目。 本主題提供利用複雜篩選撰寫查詢的範例。  
  
## <a name="example"></a>範例  
 這個範例顯示如何尋找其 `PurchaseOrder` 子項目的 `Address` 屬性等於 "Shipping"，而 `Type` 子項目等於 "NY" 的所有 `State` 項目。 它會在 `Where` 子句中使用巢狀查詢，而且如果集合在其中有任何項目，`Any` 運算子會傳回 `True`。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：多份採購單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
 For more information about the `Any` operator, see [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
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
  
```console  
99505  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的多份採購單](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。  
  
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
  
```console  
99505  
```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [XML 子代軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 屬性 (Attribute) 軸屬性 (Property)](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Projection Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [Quantifier Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
