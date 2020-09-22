---
title: TryCast 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: dc4807781f9e1aaf894016952911bd7b32c42948
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875321"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="20d8f-102">TryCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d8f-102">TryCast Operator (Visual Basic)</span></span>

<span data-ttu-id="20d8f-103">引進不會擲回例外狀況的類型轉換作業。</span><span class="sxs-lookup"><span data-stu-id="20d8f-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20d8f-104">備註</span><span class="sxs-lookup"><span data-stu-id="20d8f-104">Remarks</span></span>  

 <span data-ttu-id="20d8f-105">如果嘗試的轉換失敗， `CType` 而且 `DirectCast` 兩者都會擲回 <xref:System.InvalidCastException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="20d8f-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="20d8f-106">這可能會對應用程式的效能造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="20d8f-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="20d8f-107">`TryCast` 不會傳回 [任何](../nothing.md)專案，因此，您只需要針對傳回的結果進行測試，而不需要處理可能的例外狀況 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="20d8f-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="20d8f-108">使用 `TryCast` 關鍵字的方式與使用 [CType 函數](../functions/ctype-function.md) 和 [DirectCast 運算子](directcast-operator.md) 關鍵字的方式相同。</span><span class="sxs-lookup"><span data-stu-id="20d8f-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="20d8f-109">您會提供運算式做為第一個引數，以及將它轉換為第二個引數的類型。</span><span class="sxs-lookup"><span data-stu-id="20d8f-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="20d8f-110">`TryCast` 只在參考型別上運作，例如類別和介面。</span><span class="sxs-lookup"><span data-stu-id="20d8f-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="20d8f-111">它需要兩個類型之間的繼承或實現關聯性。</span><span class="sxs-lookup"><span data-stu-id="20d8f-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="20d8f-112">這表示一個類型必須繼承自另一個型別或從中執行。</span><span class="sxs-lookup"><span data-stu-id="20d8f-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="20d8f-113">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="20d8f-113">Errors and Failures</span></span>  

 <span data-ttu-id="20d8f-114">`TryCast` 如果偵測到沒有繼承或實現關聯性存在，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="20d8f-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="20d8f-115">但是缺少編譯器錯誤並不保證成功轉換。</span><span class="sxs-lookup"><span data-stu-id="20d8f-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="20d8f-116">如果所需的轉換是縮小，則在執行時間可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="20d8f-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="20d8f-117">如果發生這種情況，則不會傳回 `TryCast` [任何內容](../nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="20d8f-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="20d8f-118">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="20d8f-118">Conversion Keywords</span></span>  

 <span data-ttu-id="20d8f-119">類型轉換關鍵字的比較如下所示。</span><span class="sxs-lookup"><span data-stu-id="20d8f-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="20d8f-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="20d8f-120">Keyword</span></span>|<span data-ttu-id="20d8f-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="20d8f-121">Data types</span></span>|<span data-ttu-id="20d8f-122">引數關聯性</span><span class="sxs-lookup"><span data-stu-id="20d8f-122">Argument relationship</span></span>|<span data-ttu-id="20d8f-123">運行時失敗</span><span class="sxs-lookup"><span data-stu-id="20d8f-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="20d8f-124">CType Function</span><span class="sxs-lookup"><span data-stu-id="20d8f-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="20d8f-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="20d8f-125">Any data types</span></span>|<span data-ttu-id="20d8f-126">必須在兩個資料類型之間定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="20d8f-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="20d8f-127">拋出 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="20d8f-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="20d8f-128">DirectCast 運算子</span><span class="sxs-lookup"><span data-stu-id="20d8f-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="20d8f-129">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="20d8f-129">Any data types</span></span>|<span data-ttu-id="20d8f-130">一種類型必須繼承自或執行其他類型</span><span class="sxs-lookup"><span data-stu-id="20d8f-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="20d8f-131">拋出 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="20d8f-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="20d8f-132">僅限參考型別</span><span class="sxs-lookup"><span data-stu-id="20d8f-132">Reference types only</span></span>|<span data-ttu-id="20d8f-133">一種類型必須繼承自或執行其他類型</span><span class="sxs-lookup"><span data-stu-id="20d8f-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="20d8f-134">不傳回[任何](../nothing.md)專案</span><span class="sxs-lookup"><span data-stu-id="20d8f-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20d8f-135">範例</span><span class="sxs-lookup"><span data-stu-id="20d8f-135">Example</span></span>  

 <span data-ttu-id="20d8f-136">下列範例示範如何使用 `TryCast`。</span><span class="sxs-lookup"><span data-stu-id="20d8f-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="20d8f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20d8f-137">See also</span></span>

- [<span data-ttu-id="20d8f-138">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="20d8f-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="20d8f-139">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="20d8f-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
