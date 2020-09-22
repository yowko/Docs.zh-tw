---
title: DirectCast 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 7b070b8eba240440821f7984a9336c2ecaf61706
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867082"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="e1d61-102">DirectCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1d61-102">DirectCast Operator (Visual Basic)</span></span>

<span data-ttu-id="e1d61-103">引進型別轉換作業（以繼承或實作為基礎）。</span><span class="sxs-lookup"><span data-stu-id="e1d61-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1d61-104">備註</span><span class="sxs-lookup"><span data-stu-id="e1d61-104">Remarks</span></span>  

 <span data-ttu-id="e1d61-105">`DirectCast` 不會使用 Visual Basic 執行時間 helper 常式進行轉換，因此它可以提供比 `CType` 轉換成和轉換資料類型時更好的效能 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="e1d61-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="e1d61-106">您可以使用 `DirectCast` 類似于使用 [CType 函數](../functions/ctype-function.md) 和 [TryCast 運算子](trycast-operator.md) 關鍵字的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e1d61-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="e1d61-107">您會提供運算式做為第一個引數，以及將它轉換為第二個引數的類型。</span><span class="sxs-lookup"><span data-stu-id="e1d61-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="e1d61-108">`DirectCast` 需要兩個引數的資料類型之間的繼承或實現關聯性。</span><span class="sxs-lookup"><span data-stu-id="e1d61-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="e1d61-109">這表示一個類型必須繼承自另一個型別或從中執行。</span><span class="sxs-lookup"><span data-stu-id="e1d61-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="e1d61-110">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="e1d61-110">Errors and Failures</span></span>  

 <span data-ttu-id="e1d61-111">`DirectCast` 如果偵測到沒有繼承或實現關聯性存在，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1d61-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="e1d61-112">但是缺少編譯器錯誤並不保證成功轉換。</span><span class="sxs-lookup"><span data-stu-id="e1d61-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="e1d61-113">如果所需的轉換是縮小，則在執行時間可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="e1d61-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="e1d61-114">如果發生這種情況，則執行時間會擲回 <xref:System.InvalidCastException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="e1d61-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="e1d61-115">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="e1d61-115">Conversion Keywords</span></span>  

 <span data-ttu-id="e1d61-116">類型轉換關鍵字的比較如下所示。</span><span class="sxs-lookup"><span data-stu-id="e1d61-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="e1d61-117">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e1d61-117">Keyword</span></span>|<span data-ttu-id="e1d61-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="e1d61-118">Data types</span></span>|<span data-ttu-id="e1d61-119">引數關聯性</span><span class="sxs-lookup"><span data-stu-id="e1d61-119">Argument relationship</span></span>|<span data-ttu-id="e1d61-120">運行時失敗</span><span class="sxs-lookup"><span data-stu-id="e1d61-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="e1d61-121">CType Function</span><span class="sxs-lookup"><span data-stu-id="e1d61-121">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="e1d61-122">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="e1d61-122">Any data types</span></span>|<span data-ttu-id="e1d61-123">必須在兩個資料類型之間定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="e1d61-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="e1d61-124">拋出 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="e1d61-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="e1d61-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="e1d61-125">Any data types</span></span>|<span data-ttu-id="e1d61-126">一種類型必須繼承自或執行其他類型</span><span class="sxs-lookup"><span data-stu-id="e1d61-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="e1d61-127">拋出 <xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="e1d61-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="e1d61-128">TryCast 運算子</span><span class="sxs-lookup"><span data-stu-id="e1d61-128">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="e1d61-129">僅限參考型別</span><span class="sxs-lookup"><span data-stu-id="e1d61-129">Reference types only</span></span>|<span data-ttu-id="e1d61-130">一種類型必須繼承自或執行其他類型</span><span class="sxs-lookup"><span data-stu-id="e1d61-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="e1d61-131">不傳回[任何](../nothing.md)專案</span><span class="sxs-lookup"><span data-stu-id="e1d61-131">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1d61-132">範例</span><span class="sxs-lookup"><span data-stu-id="e1d61-132">Example</span></span>  

 <span data-ttu-id="e1d61-133">下列範例示範兩個的用法 `DirectCast` ，一個在執行時間失敗，另一個則成功。</span><span class="sxs-lookup"><span data-stu-id="e1d61-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="e1d61-134">在上述範例中，的執行時間類型 `q` 為 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="e1d61-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="e1d61-135">`CType` 成功 `Double` ，因為可以轉換成 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="e1d61-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="e1d61-136">不過，第一次 `DirectCast` 在執行時間失敗，因為的執行時間型別 `Double` 與之間沒有繼承關聯性 `Integer` ，即使轉換存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="e1d61-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="e1d61-137">第二個是 `DirectCast` 成功的，因為它會從型別轉換 <xref:System.Windows.Forms.Form> 成型別 <xref:System.Windows.Forms.Control> ，從中 <xref:System.Windows.Forms.Form> 繼承。</span><span class="sxs-lookup"><span data-stu-id="e1d61-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d61-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d61-138">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e1d61-139">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="e1d61-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="e1d61-140">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="e1d61-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
