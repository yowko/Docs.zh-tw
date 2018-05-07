---
title: 變數的型別&#39; &lt;variablename&gt; &#39;不會推斷，因為它繫結至封閉範圍中的欄位
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: cb423e8dcced6956eb86d484607915030c91412b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>變數的型別&#39; &lt;variablename&gt; &#39;不會推斷，因為它繫結至封閉範圍中的欄位
變數的型別 '\<變數名稱 >' 不推斷，因為它繫結至封閉範圍中的欄位。 請變更名稱 '\<變數名稱 >'，或使用完整限定的名稱 （例如 'Me.variablename' 或 'MyBase.variablename'）。  
  
 在程式碼中的迴圈控制變數與其他封閉範圍或類別欄位具有相同的名稱。 因為使用此控制項變數，而沒有`As`子句，它繫結至封閉範圍中中的欄位和編譯器不會為其建立新的變數或推斷其類型。  
  
 在下列範例中，`Index`中的控制變數`For`陳述式中，繫結至`Index`欄位`Customer`類別。 編譯器不會建立新的變數，控制變數`Index`或推斷其類型。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 根據預設，這個訊息是一個警告。 如需如何隱藏警告或將警告視為錯誤的資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42110  
  
### <a name="to-address-this-warning"></a>解決這個警告  
  
-   也不是類別的欄位名稱的識別項來變更其名稱，使迴圈控制變數本機。  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   釐清，迴圈控制變數繫結至 [類別] 欄位加`Me.`變數名稱。  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   不要依賴區域類型推斷，而應使用`As`子句來指定 for 迴圈控制變數的類型。  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>範例  
 下列程式碼會顯示就地使用第一個校正先前的範例。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>另請參閱  
 [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [For Each...Next 陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [如何：參考物件目前的執行個體](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
