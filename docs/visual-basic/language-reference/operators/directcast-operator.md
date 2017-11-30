---
title: "DirectCast 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords: DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9b81abea364e328b831ee98c3b847161c3f7dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="13739-102">DirectCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13739-102">DirectCast Operator (Visual Basic)</span></span>
<span data-ttu-id="13739-103">導入了根據繼承或實作的型別轉換作業。</span><span class="sxs-lookup"><span data-stu-id="13739-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13739-104">備註</span><span class="sxs-lookup"><span data-stu-id="13739-104">Remarks</span></span>  
 <span data-ttu-id="13739-105">`DirectCast`不會使用 Visual Basic 執行階段 helper 常式轉換，讓它可以提供稍微較佳的效能比`CType`資料型別進行來回轉換時`Object`。</span><span class="sxs-lookup"><span data-stu-id="13739-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="13739-106">您使用`DirectCast`關鍵字的使用方式類似於[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)和[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="13739-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) keyword.</span></span> <span data-ttu-id="13739-107">您提供的運算式做為第一個引數並將它轉換為做為第二個引數的型別。</span><span class="sxs-lookup"><span data-stu-id="13739-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="13739-108">`DirectCast`需要兩個引數的資料類型之間的繼承或實作關聯性。</span><span class="sxs-lookup"><span data-stu-id="13739-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="13739-109">這表示一個型別必須繼承自或實作的其他。</span><span class="sxs-lookup"><span data-stu-id="13739-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="13739-110">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="13739-110">Errors and Failures</span></span>  
 <span data-ttu-id="13739-111">`DirectCast`如果它偵測到沒有繼承或實作關聯性存在，會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="13739-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="13739-112">但沒有編譯器錯誤並不保證成功的轉換。</span><span class="sxs-lookup"><span data-stu-id="13739-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="13739-113">如果所要的轉換縮小，它可能無法在執行階段。</span><span class="sxs-lookup"><span data-stu-id="13739-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="13739-114">如果發生這種情況，執行階段會擲回<xref:System.InvalidCastException>錯誤。</span><span class="sxs-lookup"><span data-stu-id="13739-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="13739-115">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="13739-115">Conversion Keywords</span></span>  
 <span data-ttu-id="13739-116">的類型轉換關鍵字比較，如下所示。</span><span class="sxs-lookup"><span data-stu-id="13739-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="13739-117">關鍵字</span><span class="sxs-lookup"><span data-stu-id="13739-117">Keyword</span></span>|<span data-ttu-id="13739-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="13739-118">Data types</span></span>|<span data-ttu-id="13739-119">引數關聯性</span><span class="sxs-lookup"><span data-stu-id="13739-119">Argument relationship</span></span>|<span data-ttu-id="13739-120">執行階段失敗</span><span class="sxs-lookup"><span data-stu-id="13739-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="13739-121">CType 函式</span><span class="sxs-lookup"><span data-stu-id="13739-121">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="13739-122">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="13739-122">Any data types</span></span>|<span data-ttu-id="13739-123">兩個資料類型之間，則必須定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="13739-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="13739-124">擲回<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="13739-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="13739-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="13739-125">Any data types</span></span>|<span data-ttu-id="13739-126">一種類型必須繼承自或實作其他的型別</span><span class="sxs-lookup"><span data-stu-id="13739-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="13739-127">擲回<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="13739-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="13739-128">TryCast 運算子</span><span class="sxs-lookup"><span data-stu-id="13739-128">TryCast Operator</span></span>](../../../visual-basic/language-reference/operators/trycast-operator.md)|<span data-ttu-id="13739-129">只參考型別</span><span class="sxs-lookup"><span data-stu-id="13739-129">Reference types only</span></span>|<span data-ttu-id="13739-130">一種類型必須繼承自或實作其他的型別</span><span class="sxs-lookup"><span data-stu-id="13739-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="13739-131">傳回[做任何動作](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="13739-131">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="13739-132">範例</span><span class="sxs-lookup"><span data-stu-id="13739-132">Example</span></span>  
 <span data-ttu-id="13739-133">下列範例會示範兩種用途`DirectCast`，無法在執行的階段，另一個的其中一個成功。</span><span class="sxs-lookup"><span data-stu-id="13739-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 <span data-ttu-id="13739-134">在上述範例中，執行階段輸入的`q`是`Double`。</span><span class="sxs-lookup"><span data-stu-id="13739-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="13739-135">`CType`會成功，因為`Double`可以轉換成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="13739-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="13739-136">不過，第一個`DirectCast`會在執行階段失敗，因為執行階段類型的`Double`沒有與繼承關係`Integer`，即使有轉換。</span><span class="sxs-lookup"><span data-stu-id="13739-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="13739-137">第二個`DirectCast`會成功，因為它會從類型轉換<xref:System.Windows.Forms.Form>輸入<xref:System.Windows.Forms.Control>，從中<xref:System.Windows.Forms.Form>繼承。</span><span class="sxs-lookup"><span data-stu-id="13739-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13739-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13739-138">See Also</span></span>  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="13739-139">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="13739-139">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="13739-140">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="13739-140">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
