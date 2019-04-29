---
title: 維護名稱 / 值組 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ac2072-d9f5-432b-84f0-a889c62fd813
ms.openlocfilehash: 67bde0954b74b7e5145dd2d930e16feb3371a881
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650933"
---
# <a name="maintaining-namevalue-pairs-visual-basic"></a>維護名稱/值組 (Visual Basic)
許多應用程式都必須維護妥善保存為成對名稱/值的資訊。 這類資訊可能是組態或全域設定的相關資訊。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 包含一些有助您輕鬆保存成對名稱/值組的方法。 您可以將該資訊保存為屬性或一組子項目。  
  
 將資訊保存為屬性或子項目的其中一個差異在於，屬性所擁有的條件約束中，僅能有一個具有項目之特定名稱的屬性。 這項限制不適用於子項目。  
  
## <a name="setattributevalue-and-setelementvalue"></a>SetAttributeValue 和 SetElementValue  
 可簡化保存成對名稱/值的兩個方法為 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 和 <xref:System.Xml.Linq.XElement.SetElementValue%2A>。 這些兩個方法具有類似的語意 (Semantics)。  
  
 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 可以加入、修改或移除項目的屬性。  
  
- 如果您呼叫的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 具有不存在之屬性的名稱，此方法會建立一個新的屬性，並將其加入到指定的項目中。  
  
- 如果您呼叫的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 具有現有屬性的名稱以及某些指定的內容，屬性的內容會取代為指定的內容。  
  
- 如果您呼叫具有現有屬性之名稱的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>，並為內容指定 Null，該屬性會從其父代移除。  
  
 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 可以加入、修改或移除項目的子項目。  
  
- 如果您呼叫的 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 具有不存在之子項目的名稱，此方法會建立一個新的項目，並將其加入到指定的項目中。  
  
- 如果您呼叫的 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 具有現有項目的名稱以及某些指定的內容，項目的內容會取代為指定的內容。  
  
- 如果您呼叫具有現有項目之名稱的 <xref:System.Xml.Linq.XElement.SetElementValue%2A>，並為內容指定 Null，該項目會從其父代移除。  
  
## <a name="example"></a>範例  
 下列範例會建立沒有屬性的項目。 接著，它會使用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 方法來建立並維護成對名稱/值的清單。  
  
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
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a>範例  
 下列範例會建立沒有子項目的項目。 接著，它會使用 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 方法來建立並維護成對名稱/值的清單。  
  
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
  
```xml  
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

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
