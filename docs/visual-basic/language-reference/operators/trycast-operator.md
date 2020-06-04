---
title: TryCast 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: 8f0d4f612cd5a96e0b0ab7305c41e00790613cc8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406371"
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="ef3a6-102">TryCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef3a6-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="ef3a6-103">引進不會擲回例外狀況的類型轉換作業。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef3a6-104">備註</span><span class="sxs-lookup"><span data-stu-id="ef3a6-104">Remarks</span></span>  
 <span data-ttu-id="ef3a6-105">如果嘗試的轉換失敗， `CType` 且 `DirectCast` 兩者都擲回 <xref:System.InvalidCastException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="ef3a6-106">這可能會對應用程式的效能造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="ef3a6-107">`TryCast`不會傳回[任何內容](../nothing.md)，因此，您只需要針對傳回的結果進行測試，而不必處理可能的例外狀況 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-107">`TryCast` returns [Nothing](../nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="ef3a6-108">使用 `TryCast` 關鍵字的方式與使用[CType 函數](../functions/ctype-function.md)和[DirectCast Operator](directcast-operator.md)關鍵字相同。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-108">You use the `TryCast` keyword the same way you use the [CType Function](../functions/ctype-function.md) and the [DirectCast Operator](directcast-operator.md) keyword.</span></span> <span data-ttu-id="ef3a6-109">您會提供運算式做為第一個引數，以及要將它轉換成做為第二個引數的類型。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="ef3a6-110">`TryCast`只會在參考型別上運作，例如類別和介面。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="ef3a6-111">它需要兩個類型之間的繼承或實現關聯性。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="ef3a6-112">這表示一種類型必須繼承或執行另一個。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="ef3a6-113">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="ef3a6-113">Errors and Failures</span></span>  
 <span data-ttu-id="ef3a6-114">`TryCast`如果偵測到沒有繼承或實現關聯性存在，就會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="ef3a6-115">但是缺少編譯器錯誤並不保證轉換成功。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="ef3a6-116">如果想要的轉換縮小，可能會在執行時間失敗。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="ef3a6-117">如果發生這種情況，則不會傳回 `TryCast` [任何內容](../nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-117">If this happens, `TryCast` returns [Nothing](../nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="ef3a6-118">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="ef3a6-118">Conversion Keywords</span></span>  
 <span data-ttu-id="ef3a6-119">類型轉換關鍵字的比較如下所示。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="ef3a6-120">關鍵字</span><span class="sxs-lookup"><span data-stu-id="ef3a6-120">Keyword</span></span>|<span data-ttu-id="ef3a6-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="ef3a6-121">Data types</span></span>|<span data-ttu-id="ef3a6-122">引數關聯性</span><span class="sxs-lookup"><span data-stu-id="ef3a6-122">Argument relationship</span></span>|<span data-ttu-id="ef3a6-123">運行時失敗</span><span class="sxs-lookup"><span data-stu-id="ef3a6-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="ef3a6-124">CType Function</span><span class="sxs-lookup"><span data-stu-id="ef3a6-124">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="ef3a6-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="ef3a6-125">Any data types</span></span>|<span data-ttu-id="ef3a6-126">必須在兩個資料類型之間定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="ef3a6-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="ef3a6-127">引發<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="ef3a6-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="ef3a6-128">DirectCast 運算子</span><span class="sxs-lookup"><span data-stu-id="ef3a6-128">DirectCast Operator</span></span>](directcast-operator.md)|<span data-ttu-id="ef3a6-129">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="ef3a6-129">Any data types</span></span>|<span data-ttu-id="ef3a6-130">一種類型必須繼承自或執行另一個類型</span><span class="sxs-lookup"><span data-stu-id="ef3a6-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="ef3a6-131">引發<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="ef3a6-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="ef3a6-132">僅限參考型別</span><span class="sxs-lookup"><span data-stu-id="ef3a6-132">Reference types only</span></span>|<span data-ttu-id="ef3a6-133">一種類型必須繼承自或執行另一個類型</span><span class="sxs-lookup"><span data-stu-id="ef3a6-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="ef3a6-134">不傳回[任何內容](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="ef3a6-134">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef3a6-135">範例</span><span class="sxs-lookup"><span data-stu-id="ef3a6-135">Example</span></span>  
 <span data-ttu-id="ef3a6-136">下列範例示範如何使用 `TryCast`。</span><span class="sxs-lookup"><span data-stu-id="ef3a6-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ef3a6-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef3a6-137">See also</span></span>

- [<span data-ttu-id="ef3a6-138">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="ef3a6-138">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="ef3a6-139">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="ef3a6-139">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
