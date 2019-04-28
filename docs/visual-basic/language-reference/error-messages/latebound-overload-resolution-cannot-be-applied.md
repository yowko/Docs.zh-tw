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
ms.openlocfilehash: 7f2ae3bb0e7c09d966c53fb17b1cbe675dfce8b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921104"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>晚期繫結多載解析無法套用至 '\<程序名稱 >' 因為進行存取的執行個體為介面類型
編譯器嘗試解析其參考的多載的屬性或程序，但參考會失敗，因為引數的型別是`Object`和參考的物件具有介面的資料類型。 `Object`引數會強制編譯器解析為晚期繫結參考。  
  
 在這些情況下，編譯器會解析而不是透過基礎的介面實作的類別透過多載。 如果類別重新命名其中一個多載版本，編譯器不會將該版本是多載，因為它的名稱不同。 這也會導致編譯器忽略已重新命名的版本，當它可能已解析參考正確的選擇。  
  
 **錯誤 ID:** BC30933  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用`CType`要轉型的引數，從`Object`您想要呼叫的多載簽章所指定的型別。  
  
     請注意，它無法協助參考將物件轉換為基礎的介面。 您必須轉換為避免此錯誤的引數。  
  
## <a name="example"></a>範例  
 下列範例示範呼叫多載的`Sub`在編譯時期會造成這個錯誤的程序。  
  
```  
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
  
 在上述範例中，如果編譯器允許在呼叫`s1`解析度寫入時，需要透過類別的地方`c1`而不是介面`i1`。 這表示編譯器不會考慮`s2`因為其名稱中的不同`c1`，即使它是正確的選擇，因為所定義`i1`。  
  
 您可以藉由變更下列幾行程式碼的其中一種方法的呼叫來更正此錯誤：  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 每個上述幾行程式碼明確轉換`Object`變數`o1`其中一個多載所定義的參數類型。  
  
## <a name="see-also"></a>另請參閱

- [程序多載化](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [多載解析](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)
