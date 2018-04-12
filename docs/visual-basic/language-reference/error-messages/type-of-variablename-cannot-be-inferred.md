---
title: 類型 &#39;&lt;variablename&gt;&#39; 無法推斷，因為迴圈繫結和 step 變數不會擴展為相同的型別
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="cd14a-102">類型 &#39;&lt;variablename&gt;&#39; 無法推斷，因為迴圈繫結和 step 變數不會擴展為相同的型別</span><span class="sxs-lookup"><span data-stu-id="cd14a-102">Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="cd14a-103">您已經撰寫`For...Next`迴圈下列條件成立，因為編譯器無法推斷迴圈控制變數的資料類型：</span><span class="sxs-lookup"><span data-stu-id="cd14a-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
-   <span data-ttu-id="cd14a-104">未使用 `As` 子句指定迴圈控制變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd14a-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
-   <span data-ttu-id="cd14a-105">迴圈繫結和 step 變數包含至少兩種資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd14a-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
-   <span data-ttu-id="cd14a-106">資料型別之間，沒有標準轉換存在。</span><span class="sxs-lookup"><span data-stu-id="cd14a-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="cd14a-107">因此，編譯器無法推斷迴圈控制變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd14a-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="cd14a-108">在下列範例中，步驟變數是字元和迴圈繫結都是這兩個整數。</span><span class="sxs-lookup"><span data-stu-id="cd14a-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="cd14a-109">因為沒有標準轉換字元和整數之間，會報告此錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd14a-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="cd14a-110">**錯誤 ID:** BC30982</span><span class="sxs-lookup"><span data-stu-id="cd14a-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd14a-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cd14a-111">To correct this error</span></span>  
  
-   <span data-ttu-id="cd14a-112">變更類型的迴圈繫結和 step 變數在必要時，使至少一個其他擴展為型別。</span><span class="sxs-lookup"><span data-stu-id="cd14a-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="cd14a-113">在上述範例中，變更的類型`stepVar`至`Integer`。</span><span class="sxs-lookup"><span data-stu-id="cd14a-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="cd14a-114">-或-</span><span class="sxs-lookup"><span data-stu-id="cd14a-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   <span data-ttu-id="cd14a-115">使用明確的轉換函式的迴圈繫結和 step 變數轉換成適當的型別。</span><span class="sxs-lookup"><span data-stu-id="cd14a-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="cd14a-116">在上述範例中，套用`Val`函式以`stepVar`。</span><span class="sxs-lookup"><span data-stu-id="cd14a-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cd14a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd14a-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="cd14a-118">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="cd14a-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="cd14a-119">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="cd14a-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="cd14a-120">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="cd14a-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="cd14a-121">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="cd14a-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="cd14a-122">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="cd14a-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="cd14a-123">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="cd14a-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
