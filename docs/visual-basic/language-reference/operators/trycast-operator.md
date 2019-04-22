---
title: TryCast 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: c0eea4565d5040bb00743fc7864ac15b0fccdea9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831588"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="29f2b-102">TryCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29f2b-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="29f2b-103">採用的型別轉換作業不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="29f2b-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29f2b-104">備註</span><span class="sxs-lookup"><span data-stu-id="29f2b-104">Remarks</span></span>  
 <span data-ttu-id="29f2b-105">如果嘗試的轉換失敗，`CType`並`DirectCast`同時擲回<xref:System.InvalidCastException>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="29f2b-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="29f2b-106">這可能會影響您的應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="29f2b-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="29f2b-107">`TryCast` 會傳回[Nothing](../../../visual-basic/language-reference/nothing.md)，如此一來，而不必處理可能的例外狀況，您只需要測試傳回的結果，對`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="29f2b-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="29f2b-108">您使用`TryCast`關鍵字您所使用的相同方式[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)並[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="29f2b-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="29f2b-109">您提供的運算式，做為第一個引數並將它轉換成做為第二個引數的型別。</span><span class="sxs-lookup"><span data-stu-id="29f2b-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="29f2b-110">`TryCast` 僅操作於參考類型，例如類別和介面。</span><span class="sxs-lookup"><span data-stu-id="29f2b-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="29f2b-111">它需要兩個類型之間的繼承或實作關聯性。</span><span class="sxs-lookup"><span data-stu-id="29f2b-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="29f2b-112">這表示一種類型必須繼承自或實作其他。</span><span class="sxs-lookup"><span data-stu-id="29f2b-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="29f2b-113">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="29f2b-113">Errors and Failures</span></span>  
 <span data-ttu-id="29f2b-114">`TryCast` 偵測到沒有繼承或實作關聯性存在時，會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="29f2b-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="29f2b-115">但是沒有編譯器錯誤並不保證成功的轉換。</span><span class="sxs-lookup"><span data-stu-id="29f2b-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="29f2b-116">如果所需的轉換縮小，它可能無法在執行階段。</span><span class="sxs-lookup"><span data-stu-id="29f2b-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="29f2b-117">如果發生這種情況`TryCast`會傳回[Nothing](../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="29f2b-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="29f2b-118">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="29f2b-118">Conversion Keywords</span></span>  
 <span data-ttu-id="29f2b-119">類型轉換關鍵字的比較如下所示。</span><span class="sxs-lookup"><span data-stu-id="29f2b-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="29f2b-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="29f2b-120">Keyword</span></span>|<span data-ttu-id="29f2b-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="29f2b-121">Data types</span></span>|<span data-ttu-id="29f2b-122">引數的關聯性</span><span class="sxs-lookup"><span data-stu-id="29f2b-122">Argument relationship</span></span>|<span data-ttu-id="29f2b-123">執行階段失敗</span><span class="sxs-lookup"><span data-stu-id="29f2b-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="29f2b-124">CType 函式</span><span class="sxs-lookup"><span data-stu-id="29f2b-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="29f2b-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="29f2b-125">Any data types</span></span>|<span data-ttu-id="29f2b-126">兩個資料類型之間，則必須定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="29f2b-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="29f2b-127">會擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="29f2b-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="29f2b-128">DirectCast 運算子</span><span class="sxs-lookup"><span data-stu-id="29f2b-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="29f2b-129">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="29f2b-129">Any data types</span></span>|<span data-ttu-id="29f2b-130">一種類型必須繼承自或實作另一個型別</span><span class="sxs-lookup"><span data-stu-id="29f2b-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="29f2b-131">會擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="29f2b-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="29f2b-132">僅參考型別</span><span class="sxs-lookup"><span data-stu-id="29f2b-132">Reference types only</span></span>|<span data-ttu-id="29f2b-133">一種類型必須繼承自或實作另一個型別</span><span class="sxs-lookup"><span data-stu-id="29f2b-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="29f2b-134">傳回[Nothing](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="29f2b-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="29f2b-135">範例</span><span class="sxs-lookup"><span data-stu-id="29f2b-135">Example</span></span>  
 <span data-ttu-id="29f2b-136">下列範例示範如何使用 `TryCast`。</span><span class="sxs-lookup"><span data-stu-id="29f2b-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="29f2b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29f2b-137">See also</span></span>

- [<span data-ttu-id="29f2b-138">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="29f2b-138">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="29f2b-139">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="29f2b-139">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
