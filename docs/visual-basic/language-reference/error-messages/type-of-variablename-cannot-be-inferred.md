---
title: 無法推斷 '<variablename>' 的類型，因為迴圈繫結和 step 子句不會擴展為相同類型
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512712"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="2b4c3-102">無法推斷 '\<variablename > ' 的類型, 因為迴圈系結和 step 變數不會擴展為相同的類型</span><span class="sxs-lookup"><span data-stu-id="2b4c3-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="2b4c3-103">您撰寫了一個`For...Next`迴圈, 因為下列條件成立, 編譯器無法推斷迴圈控制變數的資料類型:</span><span class="sxs-lookup"><span data-stu-id="2b4c3-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="2b4c3-104">未使用 `As` 子句指定迴圈控制變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="2b4c3-105">迴圈繫結和 step 變數包含至少兩種資料類型。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-105">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="2b4c3-106">資料類型之間沒有標準轉換存在。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-106">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="2b4c3-107">因此, 編譯器無法推斷迴圈控制變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="2b4c3-108">在下列範例中, step 變數是一個字元, 而迴圈界限都是整數。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="2b4c3-109">由於字元和整數之間沒有標準轉換, 因此會回報此錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="2b4c3-110">**錯誤識別碼:** BC30982</span><span class="sxs-lookup"><span data-stu-id="2b4c3-110">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2b4c3-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2b4c3-111">To correct this error</span></span>

- <span data-ttu-id="2b4c3-112">視需要變更迴圈系結和步驟變數的類型, 使其中至少有一個是其他專案的類型。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="2b4c3-113">在上述範例中, 請將的類型`stepVar`變更`Integer`為。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="2b4c3-114">-或-</span><span class="sxs-lookup"><span data-stu-id="2b4c3-114">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="2b4c3-115">使用明確轉換函式, 將迴圈界限和步驟變數轉換成適當的類型。</span><span class="sxs-lookup"><span data-stu-id="2b4c3-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="2b4c3-116">在上述範例中, 將`Val`函數套用至。 `stepVar`</span><span class="sxs-lookup"><span data-stu-id="2b4c3-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="2b4c3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b4c3-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="2b4c3-118">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="2b4c3-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="2b4c3-119">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="2b4c3-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="2b4c3-120">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="2b4c3-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="2b4c3-121">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="2b4c3-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="2b4c3-122">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="2b4c3-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="2b4c3-123">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="2b4c3-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
