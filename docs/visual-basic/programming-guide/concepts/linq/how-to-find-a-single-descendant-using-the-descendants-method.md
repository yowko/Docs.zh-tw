---
title: "如何︰ 尋找單一子代使用 Descendants 方法 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 74d4dd0b805a5ea2c189cb89bcaeca3f4cac1268
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a>如何︰ 尋找單一子代使用 Descendants 方法 (Visual Basic)
您可以使用<xref:System.Xml.Linq.XContainer.Descendants%2A>座標軸方法快速撰寫程式碼來尋找唯一單一具名項目。</xref:System.Xml.Linq.XContainer.Descendants%2A> 當您想要利用特定名稱尋找特定子代時，這個技術特別實用。 您可以撰寫程式碼來導覽至所需的項目，但通常是比較快而且容易撰寫程式碼使用<xref:System.Xml.Linq.XContainer.Descendants%2A>軸。</xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
## <a name="example"></a>範例  
 這個範例會使用<xref:System.Linq.Enumerable.First%2A>標準查詢運算子。</xref:System.Linq.Enumerable.First%2A>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 此程式碼會產生下列輸出：  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊，請參閱[處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 此程式碼會產生下列輸出：  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a>另請參閱  
 [基本查詢 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
