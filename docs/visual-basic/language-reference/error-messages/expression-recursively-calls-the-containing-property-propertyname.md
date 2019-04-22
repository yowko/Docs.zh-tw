---
title: 運算式會遞迴地呼叫包含的屬性 '<propertyname>'
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: a758d05cca5ca71943b0ef08184aef5b2c457739
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836840"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>運算式遞迴呼叫包含的屬性 '\<屬性名稱 >'
中的陳述式`Set`屬性定義的程序會將值儲存至屬性的名稱。  
  
 保留的屬性值的建議的方法是定義`Private`屬性的容器中的變數，並用它在這兩`Get`和`Set`程序。 `Set`程序應該再儲存輸入的值，在這個`Private`變數。  
  
 `Get`程序的行為類似`Function`程序，以便它可以將值指派給屬性名稱，並將控制權傳回所遇到`End Get`陳述式。 建議的方法，不過，是加入`Private`變數中的值設定為[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Set`程序的行為類似`Sub`程序中，不會傳回值。 因此，程序或屬性名稱具有內沒有特殊意義`Set`程序中，而且您無法將值儲存到其中。  
  
 下列範例說明可能會造成這個錯誤，後面接著建議的方法的方法。  
  
```  
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
  
 **錯誤 ID:** BC42026  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請重寫的屬性定義，以使用建議的方法，在上述範例所示。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)
