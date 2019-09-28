---
title: HOW TO：Debug 空的查詢結果集（Visual Basic）
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 6fc194432b1d44c1214da32d2c6978a4eeb316dc
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351785"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a>HOW TO：Debug 空的查詢結果集（Visual Basic）

查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。

本主題中的第一組範例會顯示將 XML 載入預設命名空間而且查詢錯誤的常見方式。

第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。

如需詳細資訊，請參閱[命名空間總覽（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。

## <a name="example"></a>範例

此範例顯示 XML 在命名空間中的建立，以及傳回空結果集的查詢。

```vb
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
```

此範例會產生下列結果：

```console
Result set follows:
End of result set
```

## <a name="example"></a>範例

此範例顯示 XML 在命名空間中的建立，以及編碼正確的查詢。

解決方案是宣告和初始化全域預設命名空間。 這會將所有 XML 屬性放在預設的命名空間中。 此範例不需要其他任何修改，就可以讓它正常運作。

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
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

此範例會產生下列結果：

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a>另請參閱

- [基本查詢（LINQ to XML）（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
