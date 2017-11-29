---
title: "類型 &#39;&lt;variablename&gt;&#39; 無法推斷，因為迴圈繫結和 step 變數不會擴展為相同的型別"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords: BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>類型 &#39;&lt;variablename&gt;&#39; 無法推斷，因為迴圈繫結和 step 變數不會擴展為相同的型別
您已經撰寫`For...Next`迴圈下列條件成立，因為編譯器無法推斷迴圈控制變數的資料類型：  
  
-   未使用 `As` 子句指定迴圈控制變數的資料類型。  
  
-   迴圈繫結和 step 變數包含至少兩種資料類型。  
  
-   資料型別之間，沒有標準轉換存在。  
  
 因此，編譯器無法推斷迴圈控制變數的資料類型。  
  
 在下列範例中，步驟變數是字元和迴圈繫結都是這兩個整數。 因為沒有標準轉換字元和整數之間，會報告此錯誤。  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **錯誤 ID:** BC30982  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   變更類型的迴圈繫結和 step 變數在必要時，使至少一個其他擴展為型別。 在上述範例中，變更的類型`stepVar`至`Integer`。  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     -或-  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   使用明確的轉換函式的迴圈繫結和 step 變數轉換成適當的型別。 在上述範例中，套用`Val`函式以`stepVar`。  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
