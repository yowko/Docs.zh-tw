---
title: Visual Basic 中的預設命名空間範圍
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: af868454c9d1dce7d8bf5a1902f64eff8db8780c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710361"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a>Visual Basic 中的預設命名空間範圍
在 XML 樹狀結構中表示的預設命名空間不在查詢的範圍內。 如果您擁有的 XML 位於預設命名空間中，您仍然必須宣告 <xref:System.Xml.Linq.XNamespace> 變數，然後將它與區域名稱結合，讓限定名稱 (Qualified Name) 得以用於查詢中。  
  
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
  
 相較于上述錯誤編碼的範例, 使用 Visual Basic 時的正確方法是宣告和初始化全域預設命名空間。 這會將所有 XML 屬性放在預設的命名空間中。 此範例不需要其他任何修改，就可以讓它正常運作。  
  
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

- [命名空間總覽 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
