---
title: "如何︰ 尋找正前面的同層級 (XPATH-LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 24e3fc1cdf03017a939424fa5df9b778116f95cd
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>如何︰ 尋找正前面的同層級 (XPATH-LINQ to XML) (Visual Basic)
有時候您會想要尋找節點正前面的同層級。 由於前面同層級座標軸的位置性述詞語意 (Semantics) 在 XPath 中與 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 相反的這個差異，這是其中一個更有趣的比較。  
  
## <a name="example"></a>範例  
 在此範例中，[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]查詢會使用<xref:System.Linq.Enumerable.Last%2A>運算子，尋找<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>所傳回的集合中的最後一個節點</xref:System.Linq.Enumerable.Last%2A> 相較之下，XPath 運算式會使用述詞搭配 1 這個值來尋找正前面的項目。  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
  
```  
  
 這個範例會產生下列輸出：  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 的 XPath 使用者 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
