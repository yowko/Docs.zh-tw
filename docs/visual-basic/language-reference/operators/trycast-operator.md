---
title: TryCast 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 53306575cfc385039be3939fd87cf993b4509af4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348205"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="88b7c-102">TryCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88b7c-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="88b7c-103">引進不會擲回例外狀況的類型轉換作業。</span><span class="sxs-lookup"><span data-stu-id="88b7c-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88b7c-104">備註</span><span class="sxs-lookup"><span data-stu-id="88b7c-104">Remarks</span></span>  
 <span data-ttu-id="88b7c-105">如果嘗試的轉換失敗，`CType` 和 `DirectCast` 都會擲回 <xref:System.InvalidCastException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="88b7c-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="88b7c-106">這可能會對應用程式的效能造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="88b7c-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="88b7c-107">`TryCast` 不會傳回[任何內容](../../../visual-basic/language-reference/nothing.md)，因此您只需要針對 `Nothing`測試傳回的結果，而不需處理可能的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="88b7c-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="88b7c-108">使用 `TryCast` 關鍵字的方式與使用[CType 函數](../../../visual-basic/language-reference/functions/ctype-function.md)和[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md)關鍵字相同。</span><span class="sxs-lookup"><span data-stu-id="88b7c-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="88b7c-109">您會提供運算式做為第一個引數，以及要將它轉換成做為第二個引數的類型。</span><span class="sxs-lookup"><span data-stu-id="88b7c-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="88b7c-110">`TryCast` 只會在參考型別上運作，例如類別和介面。</span><span class="sxs-lookup"><span data-stu-id="88b7c-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="88b7c-111">它需要兩個類型之間的繼承或實現關聯性。</span><span class="sxs-lookup"><span data-stu-id="88b7c-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="88b7c-112">這表示一種類型必須繼承或執行另一個。</span><span class="sxs-lookup"><span data-stu-id="88b7c-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="88b7c-113">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="88b7c-113">Errors and Failures</span></span>  
 <span data-ttu-id="88b7c-114">如果 `TryCast` 偵測到沒有繼承或實現關聯性存在，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="88b7c-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="88b7c-115">但是缺少編譯器錯誤並不保證轉換成功。</span><span class="sxs-lookup"><span data-stu-id="88b7c-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="88b7c-116">如果想要的轉換縮小，可能會在執行時間失敗。</span><span class="sxs-lookup"><span data-stu-id="88b7c-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="88b7c-117">如果發生這種情況，`TryCast` 不會傳回[任何內容](../../../visual-basic/language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="88b7c-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="88b7c-118">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="88b7c-118">Conversion Keywords</span></span>  
 <span data-ttu-id="88b7c-119">類型轉換關鍵字的比較如下所示。</span><span class="sxs-lookup"><span data-stu-id="88b7c-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="88b7c-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="88b7c-120">Keyword</span></span>|<span data-ttu-id="88b7c-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="88b7c-121">Data types</span></span>|<span data-ttu-id="88b7c-122">引數關聯性</span><span class="sxs-lookup"><span data-stu-id="88b7c-122">Argument relationship</span></span>|<span data-ttu-id="88b7c-123">運行時失敗</span><span class="sxs-lookup"><span data-stu-id="88b7c-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="88b7c-124">CType 函式</span><span class="sxs-lookup"><span data-stu-id="88b7c-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="88b7c-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="88b7c-125">Any data types</span></span>|<span data-ttu-id="88b7c-126">必須在兩個資料類型之間定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="88b7c-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="88b7c-127">擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="88b7c-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="88b7c-128">DirectCast 運算子</span><span class="sxs-lookup"><span data-stu-id="88b7c-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="88b7c-129">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="88b7c-129">Any data types</span></span>|<span data-ttu-id="88b7c-130">一種類型必須繼承自或執行另一個類型</span><span class="sxs-lookup"><span data-stu-id="88b7c-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="88b7c-131">擲回 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="88b7c-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="88b7c-132">僅限參考型別</span><span class="sxs-lookup"><span data-stu-id="88b7c-132">Reference types only</span></span>|<span data-ttu-id="88b7c-133">一種類型必須繼承自或執行另一個類型</span><span class="sxs-lookup"><span data-stu-id="88b7c-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="88b7c-134">不傳回[任何內容](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="88b7c-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="88b7c-135">範例</span><span class="sxs-lookup"><span data-stu-id="88b7c-135">Example</span></span>  
 <span data-ttu-id="88b7c-136">下列範例示範如何使用 `TryCast`。</span><span class="sxs-lookup"><span data-stu-id="88b7c-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="88b7c-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="88b7c-137">See also</span></span>

- [<span data-ttu-id="88b7c-138">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="88b7c-138">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="88b7c-139">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="88b7c-139">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
