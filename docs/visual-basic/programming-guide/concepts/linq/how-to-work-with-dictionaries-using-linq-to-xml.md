---
title: HOW TO：使用 LINQ to XML （Visual Basic）處理字典
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 9773b926d16b51ea912792b0f348a26a9a3c7a29
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835089"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>HOW TO：使用 LINQ to XML （Visual Basic）處理字典
將各種資料結構轉換為 XML，以及將 XML 轉回其他資料結構通常很方便。 這個主題藉由來回轉換 <xref:System.Collections.Generic.Dictionary%602> 和 XML 來顯示這個一般方法的特定實作。  
  
## <a name="example"></a>範例  
 這個範例會在內嵌運算式中使用 XML 常值和查詢。 查詢會投射新的 <xref:System.Xml.Linq.XElement> 物件，然後成為 `Root` @no__t 2 物件的新內容。  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 此程式碼會產生下列輸出：  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>範例  
 下列程式碼會從 XML 建立字典。  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 此程式碼會產生下列輸出：  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>另請參閱

- [投影和轉換（LINQ to XML）（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
