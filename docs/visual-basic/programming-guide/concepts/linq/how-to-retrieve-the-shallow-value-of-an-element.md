---
title: "如何︰ 擷取表層值的項目 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 39a0648bb3fd09b9e323560b447be3cc445d5b7f
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a>如何︰ 擷取表層值的項目 (Visual Basic)
本主題說明如何取得項目的表層值。 表層值僅是特定項目的值。與深層值不同的是，深層值包含了由所有子代項目連結成單一字串的值。  
  
 當您使用轉換擷取元素值或<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>屬性，擷取的是深層值。</xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> 若要擷取表層值，您可以使用 `ShallowValue` 擴充方法，如下列範例所示。 當您想要根據項目的內容進行選取時，擷取表層值就非常有用。  
  
 下列範例會宣告擷取項目表層值的擴充方法。 接著會在查詢中使用此擴充方法，將所有包含計算值的項目列出。  
  
## <a name="example"></a>範例  
 下列文字檔 Report.xml 是此範例的原始檔。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```vb  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function ShallowValue(ByVal xe As XElement)  
        Return xe _  
               .Nodes() _  
               .OfType(Of XText)() _  
               .Aggregate(New StringBuilder(), _  
                              Function(s, c) s.Append(c), _  
                              Function(s) s.ToString())  
    End Function  
  
    Sub Main()  
        Dim root As XElement = XElement.Load("Report.xml")  
  
        Dim query As IEnumerable(Of XElement) = _  
            From el In root.Descendants() _  
            Where (el.ShallowValue().StartsWith("=")) _  
            Select el  
  
        For Each q As XElement In query  
            Console.WriteLine("{0}{1}{2}", _  
                q.Name.ToString().PadRight(8), _  
                q.Attribute("Name").ToString().PadRight(20), _  
                q.ShallowValue())  
        Next  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 軸心方法 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
