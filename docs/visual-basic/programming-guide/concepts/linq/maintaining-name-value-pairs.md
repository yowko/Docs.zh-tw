---
title: "維護名稱 / 值組 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 54db297ecd39e37492dcf8bb4de4f64476662670
ms.lasthandoff: 03/13/2017


---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>維護名稱/值組 (Visual Basic)
許多應用程式都必須維護妥善保存為成對名稱/值的資訊。 這類資訊可能是組態或全域設定的相關資訊。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 包含一些有助您輕鬆保存成對名稱/值組的方法。 您可以將該資訊保存為屬性或一組子項目。  
  
 將資訊保存為屬性或子項目的其中一個差異在於，屬性所擁有的條件約束中，僅能有一個具有項目之特定名稱的屬性。 這項限制不適用於子項目。  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue 和 SetElementValue  
 兩種方法，可加強保留名稱/值組是<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>和<xref:System.Xml.Linq.XElement.SetElementValue%2A>.</xref:System.Xml.Linq.XElement.SetElementValue%2A> </xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 這些兩個方法具有類似的語意 (Semantics)。  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>可以加入、 修改或移除項目的屬性。</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
-   如果您呼叫<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>具有不存在之屬性的名稱，此方法會建立新的屬性並將它加入至指定的項目。</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
-   如果您呼叫<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>具有現有屬性的名稱以及某些指定的內容，屬性的內容會取代指定的內容。</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
-   如果您呼叫<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>同名的現有屬性，並指定 null 的內容，該屬性會移除從其父代。</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A>可以加入、 修改或移除項目的子項目。</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
-   如果您呼叫<xref:System.Xml.Linq.XElement.SetElementValue%2A>具有不存在之子項目的名稱，此方法會建立新的項目並將它加入至指定的項目。</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
-   如果您呼叫<xref:System.Xml.Linq.XElement.SetElementValue%2A>具有現有項目的名稱以及某些指定內容，項目的內容會取代指定的內容。</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
-   如果您呼叫<xref:System.Xml.Linq.XElement.SetElementValue%2A>同名的現有項目，並為內容指定 null，從其父代移除項目。</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
## <a name="example"></a>範例  
 下列範例會建立沒有屬性的項目。 然後它會使用<xref:System.Xml.Linq.XElement.SetAttributeValue%2A>方法來建立並維護一份名稱/值組。</xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22)  
root.SetAttributeValue("Left", 20)  
root.SetAttributeValue("Bottom", 122)  
root.SetAttributeValue("Right", 300)  
root.SetAttributeValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
  
' Replace the value of Top.  
root.SetAttributeValue("Top", 10)  
Console.WriteLine(root)  
  
' Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
```  
  
 這個範例會產生下列輸出：  
  
```  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>範例  
 下列範例會建立沒有子項目的項目。 然後它會使用<xref:System.Xml.Linq.XElement.SetElementValue%2A>方法來建立並維護一份名稱/值組。</xref:System.Xml.Linq.XElement.SetElementValue%2A>  
  
```vb  
' Create an element with no content.  
Dim root As XElement = <Root/>  
  
' Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22)  
root.SetElementValue("Left", 20)  
root.SetElementValue("Bottom", 122)  
root.SetElementValue("Right", 300)  
root.SetElementValue("DefaultColor", "Color.Red")  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Replace the value of Top.  
root.SetElementValue("Top", 10)  
Console.WriteLine(root)  
Console.WriteLine("----")  
  
' Remove DefaultColor.  
root.SetElementValue("DefaultColor", Nothing)  
Console.WriteLine(root)  
  
```  
  
 這個範例會產生下列輸出：  
  
```  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A></xref:System.Xml.Linq.XElement.SetAttributeValue%2A>   
 <xref:System.Xml.Linq.XElement.SetElementValue%2A></xref:System.Xml.Linq.XElement.SetElementValue%2A>   
 [修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
