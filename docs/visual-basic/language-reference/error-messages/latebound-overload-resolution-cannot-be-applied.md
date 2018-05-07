---
title: 晚期繫結多載解析無法套用至&#39;&lt;程序名稱&gt;&#39;因為存取的執行個體為介面類型
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: e41cbf30f06547ef39553e31542e4e8b6df49a3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>晚期繫結多載解析無法套用至&#39;&lt;程序名稱&gt;&#39;因為存取的執行個體為介面類型
編譯器正在嘗試將參考解析成的多載的屬性或程序，但參考失敗，因為引數是型別`Object`和參考的物件具有介面的資料類型。 `Object`引數會強制編譯器解析參考為晚期繫結。  
  
 在這些情況下，編譯器就會透過實作類別而不是透過基礎介面的多載解析。 如果類別重新命名其中一個多載版本，編譯器不會將該版本，要多載，因為其名稱都不相同。 這會導致編譯器忽略已重新命名的版本時，它可能已解析參考正確的選擇。  
  
 **錯誤 ID:** BC30933  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用`CType`轉換引數從`Object`指定您想要呼叫的多載簽章的型別。  
  
     請注意，它不會協助參考物件轉換為基礎的介面。 您必須轉換為避免此錯誤的引數。  
  
## <a name="example"></a>範例  
 下列範例會示範呼叫多載的`Sub`在編譯時期會造成這個錯誤的程序。  
  
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
  
 在上述範例中，如果編譯器允許呼叫`s1`當寫入時，解析度也不會透過類別發生`c1`而不是介面`i1`。 這表示編譯器不會考慮`s2`因為其名稱中不同`c1`，即使它是正確的選擇，因為所定義`i1`。  
  
 您可以更正錯誤，請變更下列程式碼的呼叫：  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 上述程式碼行的每個明確轉換`Object`變數`o1`其中一個多載定義的參數型別。  
  
## <a name="see-also"></a>另請參閱  
 [程序多載化](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [多載解析](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)
