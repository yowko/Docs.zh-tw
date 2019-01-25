---
title: DirectCast 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 4b8ffbe018872c3ae467fb9bf15e3b03595fd640
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659770"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="faca0-102">DirectCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faca0-102">DirectCast Operator (Visual Basic)</span></span>
<span data-ttu-id="faca0-103">採用根據繼承或實作的型別轉換作業。</span><span class="sxs-lookup"><span data-stu-id="faca0-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faca0-104">備註</span><span class="sxs-lookup"><span data-stu-id="faca0-104">Remarks</span></span>  
 <span data-ttu-id="faca0-105">`DirectCast` 不會使用 Visual Basic 執行階段 helper 常式，進行轉換，因此它可以提供稍微較佳的效能比`CType`資料型別來回轉換時`Object`。</span><span class="sxs-lookup"><span data-stu-id="faca0-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="faca0-106">您使用`DirectCast`關鍵字與您所使用的方式類似[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)並[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="faca0-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) keyword.</span></span> <span data-ttu-id="faca0-107">您提供的運算式，做為第一個引數並將它轉換成做為第二個引數的型別。</span><span class="sxs-lookup"><span data-stu-id="faca0-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="faca0-108">`DirectCast` 需要兩個引數的資料類型之間的繼承或實作關聯性。</span><span class="sxs-lookup"><span data-stu-id="faca0-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="faca0-109">這表示一種類型必須繼承自或實作其他。</span><span class="sxs-lookup"><span data-stu-id="faca0-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="faca0-110">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="faca0-110">Errors and Failures</span></span>  
 <span data-ttu-id="faca0-111">`DirectCast` 偵測到沒有繼承或實作關聯性存在時，會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="faca0-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="faca0-112">但是沒有編譯器錯誤並不保證成功的轉換。</span><span class="sxs-lookup"><span data-stu-id="faca0-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="faca0-113">如果所需的轉換縮小，它可能無法在執行階段。</span><span class="sxs-lookup"><span data-stu-id="faca0-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="faca0-114">如果發生這種情況，執行階段會擲回<xref:System.InvalidCastException>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="faca0-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="faca0-115">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="faca0-115">Conversion Keywords</span></span>  
 <span data-ttu-id="faca0-116">類型轉換關鍵字的比較如下所示。</span><span class="sxs-lookup"><span data-stu-id="faca0-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="faca0-117">關鍵字</span><span class="sxs-lookup"><span data-stu-id="faca0-117">Keyword</span></span>|<span data-ttu-id="faca0-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="faca0-118">Data types</span></span>|<span data-ttu-id="faca0-119">引數的關聯性</span><span class="sxs-lookup"><span data-stu-id="faca0-119">Argument relationship</span></span>|<span data-ttu-id="faca0-120">執行階段失敗</span><span class="sxs-lookup"><span data-stu-id="faca0-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="faca0-121">CType 函式</span><span class="sxs-lookup"><span data-stu-id="faca0-121">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="faca0-122">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="faca0-122">Any data types</span></span>|<span data-ttu-id="faca0-123">兩個資料類型之間，則必須定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="faca0-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="faca0-124">會擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="faca0-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="faca0-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="faca0-125">Any data types</span></span>|<span data-ttu-id="faca0-126">一種類型必須繼承自或實作另一個型別</span><span class="sxs-lookup"><span data-stu-id="faca0-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="faca0-127">會擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="faca0-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="faca0-128">TryCast 運算子</span><span class="sxs-lookup"><span data-stu-id="faca0-128">TryCast Operator</span></span>](../../../visual-basic/language-reference/operators/trycast-operator.md)|<span data-ttu-id="faca0-129">僅參考型別</span><span class="sxs-lookup"><span data-stu-id="faca0-129">Reference types only</span></span>|<span data-ttu-id="faca0-130">一種類型必須繼承自或實作另一個型別</span><span class="sxs-lookup"><span data-stu-id="faca0-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="faca0-131">傳回[Nothing](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="faca0-131">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="faca0-132">範例</span><span class="sxs-lookup"><span data-stu-id="faca0-132">Example</span></span>  
 <span data-ttu-id="faca0-133">下列範例示範兩種用法`DirectCast`，無法在執行的階段，另一個的其中一個成功。</span><span class="sxs-lookup"><span data-stu-id="faca0-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 <span data-ttu-id="faca0-134">在上述範例中，執行階段類型`q`是`Double`。</span><span class="sxs-lookup"><span data-stu-id="faca0-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="faca0-135">`CType` 成功，因為`Double`可轉換成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="faca0-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="faca0-136">不過，第一個`DirectCast`在執行階段失敗，因為執行階段類型的`Double`沒有與繼承關係`Integer`，即使有轉換。</span><span class="sxs-lookup"><span data-stu-id="faca0-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="faca0-137">第二個`DirectCast`成功，因為它將從類型轉換<xref:System.Windows.Forms.Form>鍵入<xref:System.Windows.Forms.Control>，從中<xref:System.Windows.Forms.Form>繼承。</span><span class="sxs-lookup"><span data-stu-id="faca0-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faca0-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="faca0-138">See also</span></span>
- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="faca0-139">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="faca0-139">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="faca0-140">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="faca0-140">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
