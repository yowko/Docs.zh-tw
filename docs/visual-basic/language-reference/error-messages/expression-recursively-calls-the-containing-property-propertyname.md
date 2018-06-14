---
title: 運算式遞迴呼叫包含屬性&#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588839"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>運算式遞迴呼叫包含屬性&#39; &lt;propertyname&gt;&#39;
中的陳述式`Set`屬性定義的程序會將值儲存至屬性的名稱。  
  
 保留的屬性值的建議的方法是定義`Private`屬性的容器中的變數並將它用於兩者`Get`和`Set`程序。 `Set`程序應該然後儲存輸入的值，在這個`Private`變數。  
  
 `Get`程序的行為類似`Function`程序，讓它可以將值指派給屬性名稱，並將控制權傳回所遇到`End Get`陳述式。 建議的方法，不過，是要包含`Private`變數中的值作為[Return 陳述式](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Set`程序的行為類似`Sub`程序，它不會傳回值。 因此，程序或屬性名稱有內沒有特殊意義`Set`程序中，而且您無法將值儲存到其中。  
  
 下列範例說明可能會造成這個錯誤，後面接著的建議方法的方法。  
  
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
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42026  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請重寫要使用建議的方法，如上述範例所示的屬性定義。  
  
## <a name="see-also"></a>另請參閱  
 [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)
