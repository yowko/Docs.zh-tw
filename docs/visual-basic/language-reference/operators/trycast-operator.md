---
title: TryCast 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: d8825b8eee35ea514d4001a6a5c1cc5139c67454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600146"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="cc0c2-102">TryCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc0c2-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="cc0c2-103">導入了沒有擲回例外狀況的類型轉換作業。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc0c2-104">備註</span><span class="sxs-lookup"><span data-stu-id="cc0c2-104">Remarks</span></span>  
 <span data-ttu-id="cc0c2-105">如果嘗試的轉換失敗，`CType`和`DirectCast`同時擲回<xref:System.InvalidCastException>錯誤。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="cc0c2-106">這可能會影響應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="cc0c2-107">`TryCast` 傳回[Nothing](../../../visual-basic/language-reference/nothing.md)，如此一來，而不必處理可能的例外狀況，您只需要測試傳回的結果，針對`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="cc0c2-108">您使用`TryCast`關鍵字您使用的相同方式[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)和[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="cc0c2-109">您提供的運算式做為第一個引數並將它轉換為做為第二個引數的型別。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="cc0c2-110">`TryCast` 只在參考類型，例如類別和介面上的作業。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="cc0c2-111">它需要兩個類型之間的繼承或實作關聯性。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="cc0c2-112">這表示一個型別必須繼承自或實作的其他。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="cc0c2-113">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="cc0c2-113">Errors and Failures</span></span>  
 <span data-ttu-id="cc0c2-114">`TryCast` 如果它偵測到沒有繼承或實作關聯性存在，會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="cc0c2-115">但沒有編譯器錯誤並不保證成功的轉換。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="cc0c2-116">如果所要的轉換縮小，它可能無法在執行階段。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="cc0c2-117">如果發生這種情況，`TryCast`傳回[Nothing](../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="cc0c2-118">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="cc0c2-118">Conversion Keywords</span></span>  
 <span data-ttu-id="cc0c2-119">的類型轉換關鍵字比較，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="cc0c2-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="cc0c2-120">Keyword</span></span>|<span data-ttu-id="cc0c2-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="cc0c2-121">Data types</span></span>|<span data-ttu-id="cc0c2-122">引數關聯性</span><span class="sxs-lookup"><span data-stu-id="cc0c2-122">Argument relationship</span></span>|<span data-ttu-id="cc0c2-123">執行階段失敗</span><span class="sxs-lookup"><span data-stu-id="cc0c2-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="cc0c2-124">CType 函式</span><span class="sxs-lookup"><span data-stu-id="cc0c2-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="cc0c2-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="cc0c2-125">Any data types</span></span>|<span data-ttu-id="cc0c2-126">兩個資料類型之間，則必須定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="cc0c2-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="cc0c2-127">擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="cc0c2-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="cc0c2-128">DirectCast 運算子</span><span class="sxs-lookup"><span data-stu-id="cc0c2-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="cc0c2-129">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="cc0c2-129">Any data types</span></span>|<span data-ttu-id="cc0c2-130">一種類型必須繼承自或實作其他的型別</span><span class="sxs-lookup"><span data-stu-id="cc0c2-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="cc0c2-131">擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="cc0c2-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="cc0c2-132">只參考型別</span><span class="sxs-lookup"><span data-stu-id="cc0c2-132">Reference types only</span></span>|<span data-ttu-id="cc0c2-133">一種類型必須繼承自或實作其他的型別</span><span class="sxs-lookup"><span data-stu-id="cc0c2-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="cc0c2-134">傳回[做任何動作](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="cc0c2-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cc0c2-135">範例</span><span class="sxs-lookup"><span data-stu-id="cc0c2-135">Example</span></span>  
 <span data-ttu-id="cc0c2-136">下列範例示範如何使用 `TryCast`。</span><span class="sxs-lookup"><span data-stu-id="cc0c2-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cc0c2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc0c2-137">See Also</span></span>  
 [<span data-ttu-id="cc0c2-138">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="cc0c2-138">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="cc0c2-139">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="cc0c2-139">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
