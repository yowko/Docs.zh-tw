---
title: "Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30982"
  - "vbc30982"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30982"
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您已撰寫 `For...Next` 迴圈，但因為下列條件為 true，編譯器無法推斷此迴圈控制變數的資料型別：  
  
-   沒有使用 `As` 子句指定迴圈控制變數的資料型別。  
  
-   迴圈繫結和 step 變數至少包含兩個資料型別。  
  
-   資料型別之間沒有標準轉換。  
  
 因此，編譯器無法推斷迴圈控制變數的資料型別。  
  
 在下列範例中，step 變數是字元，而迴圈繫結則都是整數。  由於字元和整數之間沒有標準轉換，將會報告此錯誤。  
  
```vb#  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **錯誤 ID**：BC30982  
  
### 若要更正這個錯誤  
  
-   依需要變更迴圈繫結和 step 變數的型別，讓其中一項的型別是其他迴圈繫結和 step 變數要擴展的目標型別。  在先前的範例中，將 `stepVar` 型別變更為 `Integer`。  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     \-或\-  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   使用明確轉換函式，將迴圈繫結和 step 變數轉換為適當的型別。  在先前的範例中，將 `Val` 函式套用到 `stepVar`。  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [For...Next 陳述式](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)