---
title: 無法推斷 '<variablename>' 的類型，因為迴圈繫結和 step 子句不會擴展為相同類型
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 1330cbd6567b69df9bd811ced49c6df2e120a0b2
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161205"
---
# <a name="bc30982-type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>BC30982：無法推斷 ' ' 的類型， \<variablename> 因為迴圈界限和 step 變數不會擴展為相同的類型

您已撰寫迴圈，讓 `For...Next` 編譯器無法推斷迴圈控制變數的資料類型，因為下列條件成立：

- 未使用 `As` 子句指定迴圈控制變數的資料類型。

- 迴圈繫結和 step 變數包含至少兩種資料類型。

- 資料類型之間沒有標準轉換存在。

 因此，編譯器無法推斷迴圈控制變數的資料類型。

 在下列範例中，step 變數是一個字元，而迴圈系結都是整數。 因為字元和整數之間沒有標準轉換，所以會報告此錯誤。

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**錯誤識別碼：** BC30982

## <a name="to-correct-this-error"></a>更正這個錯誤

- 視需要變更「迴圈界限」和「步驟」變數的類型，如此一來，至少其中一個類型就是其他人所擴展的類型。 在上述範例中，將的型別變更 `stepVar` 為 `Integer` 。

  ```vb
  Dim stepVar = 1
  ```

  -或-

  ```vb
  Dim stepVar As Integer = 1
  ```

- 使用明確的轉換函式，將迴圈界限和 step 變數轉換成適當的類型。 在上述範例中，請將 `Val` 函數套用至 `stepVar` 。

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next 陳述式](../statements/for-next-statement.md)
- [隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [區域型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 陳述式](../statements/option-infer-statement.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
