---
title: "如何︰ 鏈結軸心方法呼叫 (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c0e9d440ab50b7f275296731e5210578bcedcaa
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a>如何︰ 鏈結軸心方法呼叫 (LINQ to XML) (Visual Basic)
您在程式碼中使用的常見模式為呼叫座標軸方法，然後呼叫其中一個擴充方法座標軸。  
  
 有兩個座標軸名稱`Elements`可傳回集合的項目︰<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>方法和<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> 您可以結合這兩個座標軸，在樹狀的指定深度，尋找指定之名稱的所有項目。  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>和<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>找到所有`Name`項目的所有`Address`項目的所有`PurchaseOrder`項目。</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 多份採購訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 這是因為其中一個實作的`Elements`軸是當做擴充方法上<xref:System.Collections.Generic.IEnumerable%601>的<xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer> </xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>衍生自<xref:System.Xml.Linq.XContainer>，因此您可以呼叫<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>方法呼叫的結果，在<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XElement>  
  
## <a name="example"></a>範例  
 有時候您會想要在可能有也可能沒有介入祖系時，擷取特定項目深度的所有項目。 例如，在下列文件中，您可能想要擷取 `ConfigParameter` 項目子系的所有 `Customer` 項目，但不是 `ConfigParameter` 項目子系的 `Root`。  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 若要這樣做，您可以使用<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>座標軸，如下︰</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同技術。 如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 這個範例會使用下列 XML 文件︰[範例 XML 檔︰ 命名空間中的多個採購訂單](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 軸心方法 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
