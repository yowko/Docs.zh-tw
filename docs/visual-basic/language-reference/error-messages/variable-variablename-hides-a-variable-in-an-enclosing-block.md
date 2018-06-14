---
title: 變數&#39; &lt;variablename&gt; &#39;隱藏了封閉區塊中的變數
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595088"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>變數&#39; &lt;variablename&gt; &#39;隱藏了封閉區塊中的變數
區塊中的變數具有相同名稱做為另一個本機變數。  
  
 **錯誤 ID:** BC30616  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   重新命名封閉區塊中的變數，使它不是其他任何區域變數一樣。 例如:   
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   這項錯誤的常見原因是使用`Catch e As Exception`內的事件處理常式。 如果這種情況，命名`Catch`區塊變數`ex`而不是`e`。  
  
-   此錯誤的另一個常見來源是嘗試存取內宣告的區域變數`Try`中個別區塊`Catch`區塊。 若要修正此問題，外部變數宣告`Try...Catch...Finally`結構。  
  
## <a name="see-also"></a>另請參閱  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [變數宣告](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
