---
title: 運算式會遞迴地呼叫包含的屬性 '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: e3a9f4cf2f4105d2c449813bf0c593860df7d1f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409500"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>運算式會遞迴地呼叫包含的屬性 '\<propertyname>'
屬性定義的程式中的語句會將 `Set` 值儲存至屬性的名稱。  
  
 保存屬性值的建議方法是 `Private` 在屬性的容器中定義變數，並在和程式中使用它 `Get` `Set` 。 `Set`然後，此程式應該將傳入的值儲存在此變數中 `Private` 。  
  
 此程式的 `Get` 行為就像 `Function` 程式，因此可以藉由遇到語句，將值指派給屬性名稱，並傳回控制權 `End Get` 。 不過，建議的方法是在 `Private` [Return 語句](../statements/return-statement.md)中包含變數作為值。  
  
 此程式的 `Set` 行為就像是 `Sub` 不會傳回值的程式。 因此，程式或屬性名稱在程式中沒有特殊意義 `Set` ，而且您無法在其中儲存值。  
  
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
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC42026  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 重寫屬性定義，以使用上述範例中所述的建議方法。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Statement](../statements/property-statement.md)
- [Set 語句](../statements/set-statement.md)
