---
title: 如何：尋找具有特定屬性的項目 (XPath-LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4bb38d2c-bc7c-4196-8909-aaf41fb86b28
ms.openlocfilehash: 36f725a7684dc009dbfb956a1584fd6ca5e487b0
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267037"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-visual-basic"></a>如何：查找具有特定屬性的元素（XPath-LINQ 到 XML）（可視基本）
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
  
```console
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
## <a name="see-also"></a>另請參閱

- [XPath 使用者的 LINQ 到 XML（可視基本）](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
