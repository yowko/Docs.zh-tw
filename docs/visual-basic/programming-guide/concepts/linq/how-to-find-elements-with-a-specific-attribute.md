---
title: HOW TO：尋找具有特定屬性 (XPATH-LINQ to XML) 項目 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: 17c5e9abf607df7311ff2552b7e9c54cbf30fd59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780480"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a>HOW TO：尋找具有特定屬性 (XPATH-LINQ to XML) 項目 (Visual Basic)
有時候您會想要尋找具有特定屬性的所有項目。 您並不關心屬性的內容。 但是，您想要根據屬性的存在與否來選擇。  
  
 XPath 運算式為：  
  
 `./*[@Select]`  
  
## <a name="example"></a>範例  
 下列程式碼只會選取具有 `Select` 屬性的項目。  
  
```vb  
Dim doc As XElement = _   
    <Root>  
        <Child1>1</Child1>  
        <Child2 Select='true'>2</Child2>  
        <Child3>3</Child3>  
        <Child4 Select='true'>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    From el In doc.Elements() _  
    Where el.@Select <> Nothing _  
    Select el  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = DirectCast(doc.XPathEvaluate _  
    ("./*[@Select]"), IEnumerable).Cast(Of XElement)()  
  
If list1.Count() = list2.Count() And _  
    list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML (Visual Basic) 的 XPath 使用者適用的](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
