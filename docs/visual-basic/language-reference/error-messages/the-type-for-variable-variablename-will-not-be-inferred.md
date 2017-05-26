---
title: "變數的型別 &quot;&lt;variablename&gt;&quot; 將不會推斷，因為繫結至封閉範圍中的欄位 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
dev_langs:
- VB
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ab7d69c34a58dc898553868258c4fdf6b81db343
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>變數的型別 '&lt;variablename&gt;' 將不會推斷，因為繫結至封閉範圍中的欄位
變數的型別 '\<variablename >' 將不會推斷，因為繫結至封閉範圍中的欄位。 您可以變更名稱 '\<variablename >'，或使用完整限定的名稱 （例如 'Me.variablename' 或 'MyBase.variablename'）。  
  
 在程式碼中的迴圈控制變數具有相同名稱做為類別或其他封閉範圍的欄位。 因為使用控制變數，而沒有`As`子句，它會繫結至封閉範圍中的欄位和編譯器不會為其建立新的變數或推斷其型別。  
  
 在下列範例中，`Index`中的控制項變數`For`陳述式中，繫結至`Index`欄位`Customer`類別。 編譯器不會建立新的變數，控制變數的`Index`或推斷其型別。  
  
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
  
 根據預設，這個訊息是一個警告。 隱藏警告的方式或如何將警告視為錯誤的相關資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC42110  
  
### <a name="to-address-this-warning"></a>解決這個警告  
  
-   也不是類別的欄位名稱的識別項來變更其名稱，讓迴圈控制變數本機。  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   釐清的迴圈控制變數繫結至 [類別] 欄位加`Me.`變數名稱。  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   除了依賴區域型別推斷，使用`As`子句來指定迴圈控制變數的型別。  
  
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
 [每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...下一個陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [如何︰ 參考物件的目前執行個體](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

