---
title: "在 Visual Basic 中的預設命名空間的範圍 |Microsoft 文件"
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
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c0152250cf7cfb4b6cadbcaab60eaad8ec2fb5ee
ms.lasthandoff: 03/13/2017


---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>在 Visual Basic 中的預設命名空間的範圍
在 XML 樹狀結構中表示的預設命名空間不在查詢的範圍內。 如果您擁有的預設命名空間中的 XML，您仍然必須宣告<xref:System.Xml.Linq.XNamespace>變數，並將其與要用於查詢中限定的名稱的本機名稱。</xref:System.Xml.Linq.XNamespace>  
  
 查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。  
  
 本主題中的第一組範例會顯示載入預設命名空間中的 XML 但查詢錯誤的常見方式。  
  
 第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。  
  
## <a name="example"></a>範例  
 此範例顯示在命名空間中建立 XML，以及傳回空結果集的查詢。  
  
### <a name="code"></a>程式碼  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>註解  
 此範例會產生下列結果：  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>範例  
 此範例顯示在命名空間中建立 XML，以及編碼正確的查詢。  
  
 相較於上述編碼錯誤範例中，使用 Visual Basic 時的正確方法為宣告並初始化全域預設命名空間。 這會將所有 XML 屬性放在預設的命名空間中。 此範例不需要其他任何修改，就可以讓它正常運作。  
  
### <a name="code"></a>程式碼  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a>註解  
 此範例會產生下列結果：  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>另請參閱  
 [處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
