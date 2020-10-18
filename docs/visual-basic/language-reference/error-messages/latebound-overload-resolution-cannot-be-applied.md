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
ms.openlocfilehash: 090ec6f3bbf56350fda2ab15c974b0bc6b15e3d3
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162514"
---
# <a name="bc30933-latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>BC30933：晚期繫結多載解析無法套用至 ' \<procedurename> '，因為存取的實例為介面類別型

編譯器嘗試解析多載屬性或程式的參考，但參考失敗，因為引數的型別為 `Object` ，而且參考的物件有介面的資料型別。 `Object`引數會強制編譯器將參考解析為晚期繫結。

在這些情況下，編譯器會透過實類別（而不是透過基礎介面）解析多載。 如果類別重新命名其中一個多載版本，則編譯器不會將該版本視為多載，因為其名稱不同。 接著，當編譯器可能是解析參考的正確選擇時，會導致編譯器忽略重新命名的版本。

**錯誤識別碼：** BC30933

## <a name="to-correct-this-error"></a>更正這個錯誤

- 使用 `CType` 將引數轉換成您想要呼叫之多載簽章所 `Object` 指定的型別。

  請注意，它不會協助將參考物件轉換成基礎介面。 您必須轉換引數，以避免此錯誤。

## <a name="example"></a>範例

下列範例 `Sub` 會顯示在編譯時期導致此錯誤之多載程式的呼叫。

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

在上述範例中，如果編譯器允許以撰寫的呼叫 `s1` ，則會透過類別 `c1` （而非介面）進行解析 `i1` 。 這表示編譯器不會考慮 `s2` ，因為它的名稱在中是不同的 `c1` ，雖然它是所定義的正確選擇 `i1` 。

您可以藉由變更下列任一行程式碼的呼叫來修正錯誤：

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

上述每一行程式碼都會將變數明確地 `Object` 轉換 `o1` 成針對多載所定義的其中一個參數類型。

## <a name="see-also"></a>另請參閱

- [程序多載化](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [多載解析](../../programming-guide/language-features/procedures/overload-resolution.md)
- [CType Function](../functions/ctype-function.md)
