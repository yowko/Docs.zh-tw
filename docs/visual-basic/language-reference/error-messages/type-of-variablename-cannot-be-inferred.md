---
title: 無法推斷 '<variablename>' 的類型，因為迴圈繫結和 step 子句不會擴展為相同類型
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: e90e881546c12df2c8b19ff03a4d4c7304c4596c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052673"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="cd6c8-102">類型 '\<變數名稱 >' 無法推斷，因為迴圈繫結和 step 變數不會擴展為相同的型別</span><span class="sxs-lookup"><span data-stu-id="cd6c8-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="cd6c8-103">您已撰寫`For...Next`下列條件成立，因為編譯器無法推斷迴圈控制變數的資料類型的迴圈：</span><span class="sxs-lookup"><span data-stu-id="cd6c8-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
- <span data-ttu-id="cd6c8-104">未使用 `As` 子句指定迴圈控制變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
- <span data-ttu-id="cd6c8-105">迴圈繫結和 step 變數包含至少兩種資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
- <span data-ttu-id="cd6c8-106">標準轉換存在之間的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="cd6c8-107">因此，編譯器無法推斷迴圈控制變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="cd6c8-108">在下列範例中，步驟變數是字元，而且迴圈繫結都是這兩個整數。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="cd6c8-109">因為沒有標準轉換字元和整數之間，則會報告此錯誤。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="cd6c8-110">**錯誤 ID:** BC30982</span><span class="sxs-lookup"><span data-stu-id="cd6c8-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd6c8-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cd6c8-111">To correct this error</span></span>  
  
- <span data-ttu-id="cd6c8-112">變更迴圈繫結和 step 變數為必要的類型，使至少一個其他擴展為的型別。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="cd6c8-113">在上述範例中，將變更的型別`stepVar`至`Integer`。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="cd6c8-114">-或-</span><span class="sxs-lookup"><span data-stu-id="cd6c8-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
- <span data-ttu-id="cd6c8-115">您可以使用明確的轉換函式，將迴圈繫結和 step 變數轉換成適當的類型。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="cd6c8-116">在上述範例中，套用`Val`函式以`stepVar`。</span><span class="sxs-lookup"><span data-stu-id="cd6c8-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cd6c8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd6c8-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="cd6c8-118">For...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="cd6c8-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="cd6c8-119">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="cd6c8-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="cd6c8-120">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="cd6c8-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="cd6c8-121">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="cd6c8-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="cd6c8-122">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="cd6c8-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="cd6c8-123">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="cd6c8-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
