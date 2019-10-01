---
title: 運算式會遞迴地呼叫包含的屬性 '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698573"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>運算式會遞迴地呼叫包含屬性 ' @no__t 0propertyname > '
屬性定義的 `Set` 程式中的語句會將值儲存在屬性名稱中。  
  
 保存屬性值的建議方法是在屬性的容器中定義 @no__t 0 變數，並同時在 `Get` 和 @no__t 2 程式中使用它。 @No__t 0 程式應該會將傳入的值儲存在此 @no__t 1 變數中。  
  
 @No__t-0 程式的行為就像是 @no__t 1 程式，因此它可以藉由遇到 @no__t 2 語句，將值指派給屬性名稱，並傳回控制權。 不過，建議的方法是在[Return 語句](../../../visual-basic/language-reference/statements/return-statement.md)中包含 `Private` 變數做為值。  
  
 @No__t-0 程式的行為就像是不會傳回值的 @no__t 1 程式。 因此，程式或屬性名稱在 `Set` 程式中沒有特殊意義，而且您無法在其中儲存值。  
  
 下列範例說明可能造成此錯誤的方法，後面接著建議的方法。  
  
```vb  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC42026  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 重寫屬性定義，以使用上述範例中所述的建議方法。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)
