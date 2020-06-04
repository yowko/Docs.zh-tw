---
title: 晚期繫結多載解析無法套用至 '<procedurename>'，因為進行存取的執行個體為介面類型
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 4500a177c7a4729fe5131af1b007fd38e77afe07
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397333"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>晚期繫結多載解析無法套用至 '\<procedurename>'，因為進行存取的執行個體為介面類型

編譯器嘗試解析多載屬性或程式的參考，但參考失敗，因為引數是型別 `Object` ，而參考物件具有介面的資料型別。 `Object`引數會強制編譯器將參考解析為晚期繫結。

在這些情況下，編譯器會透過執行類別（而不是透過基礎介面）來解析多載。 如果類別重新命名其中一個多載版本，則編譯器不會將該版本視為多載，因為它的名稱不同。 這會導致編譯器忽略重新命名的版本，因為它可能是解析參考的正確選擇。

**錯誤識別碼：** BC30933

## <a name="to-correct-this-error"></a>更正這個錯誤

- 使用 `CType` 將引數從轉換成您想要呼叫之多載的簽章所 `Object` 指定的類型。

  請注意，它不會協助將參考物件轉換成基礎介面。 您必須轉換引數，以避免發生這個錯誤。

## <a name="example"></a>範例

下列範例顯示呼叫 `Sub` 在編譯時期造成此錯誤的多載程式。

```vb
Module m1
    Interface i1
        Sub s1(ByVal p1 As Integer)
        Sub s1(ByVal p1 As Double)
    End Interface
    Class c1
        Implements i1
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1
        End Sub
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1
        End Sub
    End Class
    Sub Main()
        Dim refer As i1 = New c1
        Dim o1 As Object = 3.1415
        ' The following reference is INVALID and causes a compiler error.
        refer.s1(o1)
    End Sub
End Module
```

在上述範例中，如果編譯器允許以撰寫的呼叫 `s1` ，則會透過類別 `c1` 而不是介面來進行解析 `i1` 。 這表示編譯器不會考慮 `s2` ，因為它的名稱在中是不同的 `c1` ，即使是由定義的正確選擇也是一樣 `i1` 。

您可以藉由將呼叫變更為下列任一行程式碼來更正錯誤：

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

上述程式碼的每一行都會明確地將 `Object` 變數轉換 `o1` 為多載所定義的其中一個參數類型。

## <a name="see-also"></a>另請參閱

- [程序多載化](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [多載解析](../../programming-guide/language-features/procedures/overload-resolution.md)
- [CType Function](../functions/ctype-function.md)
