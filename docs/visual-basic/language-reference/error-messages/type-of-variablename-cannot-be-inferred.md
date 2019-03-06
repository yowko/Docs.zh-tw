---
title: 無法推斷 '<variablename>' 的類型，因為迴圈繫結和 step 子句不會擴展為相同類型
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 1f1df0c7391c027994caabadc4b857bec55f5938
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367176"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>類型 '\<變數名稱 >' 無法推斷，因為迴圈繫結和 step 變數不會擴展為相同的型別
您已撰寫`For...Next`下列條件成立，因為編譯器無法推斷迴圈控制變數的資料類型的迴圈：  
  
-   未使用 `As` 子句指定迴圈控制變數的資料類型。  
  
-   迴圈繫結和 step 變數包含至少兩種資料類型。  
  
-   標準轉換存在之間的資料類型。  
  
 因此，編譯器無法推斷迴圈控制變數的資料類型。  
  
 在下列範例中，步驟變數是字元，而且迴圈繫結都是這兩個整數。 因為沒有標準轉換字元和整數之間，則會報告此錯誤。  
  
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
  
-   變更迴圈繫結和 step 變數為必要的類型，使至少一個其他擴展為的型別。 在上述範例中，將變更的型別`stepVar`至`Integer`。  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     -或-  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   您可以使用明確的轉換函式，將迴圈繫結和 step 變數轉換成適當的類型。 在上述範例中，套用`Val`函式以`stepVar`。  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
