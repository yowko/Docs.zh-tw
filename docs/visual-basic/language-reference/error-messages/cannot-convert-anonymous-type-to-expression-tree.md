---
title: 無法將匿名類型轉換為運算式樹狀架構，因為該類型含有的欄位是用來初始化其他欄位
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: ba14c0cd8781b8771ac8b746e3efec29a457294a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701182"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a>無法將匿名類型轉換為運算式樹狀架構，因為該類型含有的欄位是用來初始化其他欄位
當匿名型別的一個屬性用來初始化匿名型別的另一個屬性時，編譯器不接受匿名轉換成運算式樹狀架構。 例如，在下列程式碼中，`Prop1` 會在初始化清單中宣告，然後用來做為 `Prop2` 的初始值。  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 **錯誤識別碼：** BC36548  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將 `Prop1` 的初始值指派給本機變數。 將該變數指派給 `Prop1` 和 `Prop2`，如下列程式碼所示。  
  
    ```vb  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a>另請參閱

- [匿名型別（Visual Basic）](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [運算式樹狀結構 (Visual Basic)](../../programming-guide/concepts/expression-trees/index.md)
- [如何：使用運算式樹狀架構建立動態查詢（Visual Basic） ](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
