---
title: "如何︰ 尋找具有特定屬性 (Visual Basic) 的項目 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 59fb7c19-d42f-40eb-8cf8-f1d5b9658eb7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ce57f1c7e0e1860d858d36ccaff256aa4afe7e2b
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-an-element-with-a-specific-attribute-visual-basic"></a>如何︰ 尋找具有特定屬性 (Visual Basic) 的項目
這個主題顯示如何尋找其屬性具有特定值的項目。  
  
## <a name="example"></a>範例  
 此範例顯示如何尋找其 `Address` 屬性具有 "Billing" 值的 `Type` 項目。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 典型採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrder.xml")  
Dim address As IEnumerable(Of XElement) = _  
    From el In root.<Address> _  
    Where el.@Type = "Billing" _  
    Select el  
For Each el As XElement In address  
    Console.WriteLine(el)  
Next  
```  
  
 此程式碼會產生下列輸出：  
  
```xml  
  
          <Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
 請注意，這個範例會使用[XML 子代軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)、 [XML 屬性軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)，而[XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 命名空間中的典型採購訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)。  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim address As IEnumerable(Of XElement) = _  
            From el In root.<aw:Address> _  
            Where el.@aw:Type = "Billing" _  
            Select el  
        For Each el As XElement In address  
            Console.WriteLine(el)  
        Next  
    End Sub  
End Module  
```  
  
 此程式碼會產生下列輸出：  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement.Attribute%2A></xref:System.Xml.Linq.XElement.Attribute%2A>   
 <xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A>   
 [基本查詢 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)   
 [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [投影作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
