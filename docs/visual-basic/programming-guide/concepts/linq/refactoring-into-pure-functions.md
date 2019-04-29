---
title: 重構為純虛擬函式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787162"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a>重構為純虛擬函式 (Visual Basic)

純功能性轉換的重要觀點為學習如何使用純虛擬函式重構程式碼。

如同本節先前所述，純虛擬函式擁有兩個實用的特性：

- 它有沒有副作用。 函式不會變更函式以外任何類型的任何變數或資料。

- 它是一致的。 假設是相同的輸入資料集合，就永遠會傳回相同的輸出值。

 轉換為功能性程式設計的其中一種方式為重構現有的程式碼以排除不必要的副作用與外部相依性。 以此種方式，您可以建立現有程式碼的純虛擬函式版本。

這個主題討論什麼是純虛擬函式以及什麼不是純虛擬函式。 [教學課程：管理 WordprocessingML 文件 (Visual Basic) 中的內容](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)教學課程示範如何管理 WordprocessingML 文件，並包含兩個範例使用純虛擬函式重構。

## <a name="eliminating-side-effects-and-external-dependencies"></a>排除副作用與外部相依性

下列範例對照兩個非純虛擬函式與一個純虛擬函式。

### <a name="non-pure-function-that-changes-a-class-member"></a>變更類別成員的非純虛擬函式

在下列程式碼中，`HyphenatedConcat` 函式不是純虛擬函式，因為它會修改類別中的 `aMember` 資料成員：

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

此程式碼會產生下列輸出：

```
StringOne-StringTwo
```

請注意，它是不相關要修改的資料是否有`public`或是`private`存取權，或者是`shared`成員或執行個體成員。 純虛擬函式不會變更函式以外的任何資料。

### <a name="non-pure-function-that-changes-an-argument"></a>變更引數的非純虛擬函式

此外，這個相同函式的下列版本不是純虛擬函式，因為它會修改其參數 `sb` 的內容。

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

這個版本的程式會產生與第一版相同的輸出，因為 `HyphenatedConcat` 函式已經叫用 <xref:System.Text.StringBuilder.Append%2A> 成員函式來變更其第一個參數的值 (狀態)。 請注意，雖然 `HyphenatedConcat` 使用 call-by-value 參數傳遞 (Parameter Passing)，還是會發生這個改變。

> [!IMPORTANT]
> 若是參考型別 (Reference Type)，如果您依據值傳遞參數，會使參考的副本傳遞到物件。 這個副本仍然跟原始參考一樣，與相同的執行個體資料相關聯 (直到將參考變數指派給新的物件)。 對於要修改參數的函式，則不一定需要 Call-by-reference。

### <a name="pure-function"></a>純虛擬函式

這個下一個版本的程式顯示如何實作 `HyphenatedConcat` 函式做為純虛擬函式。

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

再次聲明，這個版本會產生相同的輸出行：`StringOne-StringTwo`。 請注意，若要保留串連值，它會儲存在中繼變數 `s2` 中。

其中一個可能非常實用的方法是，撰寫在本機非純虛擬但全域為純虛擬的函式 (亦即，它們可以宣告並修改本機變數)。 這類函式擁有許多值得撰寫的特性，但是會避免某些更錯綜複雜的功能性程式設計慣用句，例如，當簡易迴圈可以完成相同的事情時，必須使用遞迴。

## <a name="standard-query-operators"></a>標準查詢運算子

標準查詢運算子的重要特性為它們會被當做純虛擬函式實作。

如需詳細資訊，請參閱 <<c0> [ 標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。

## <a name="see-also"></a>另請參閱

- [純函數式轉換 (Visual Basic) 簡介](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [函數式程式設計與命令式程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
