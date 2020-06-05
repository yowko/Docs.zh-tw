---
title: DirectCast 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 96cb2082d59373deb34d6894270205b7c1045850
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371514"
---
# <a name="directcast-operator-visual-basic"></a><span data-ttu-id="93dc7-102">DirectCast 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93dc7-102">DirectCast Operator (Visual Basic)</span></span>
<span data-ttu-id="93dc7-103">引進以繼承或實作為基礎的型別轉換作業。</span><span class="sxs-lookup"><span data-stu-id="93dc7-103">Introduces a type conversion operation based on inheritance or implementation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93dc7-104">備註</span><span class="sxs-lookup"><span data-stu-id="93dc7-104">Remarks</span></span>  
 <span data-ttu-id="93dc7-105">`DirectCast`不會使用 Visual Basic 執行時間協助程式常式進行轉換，因此它可以提供比 `CType` 在資料類型來回轉換時更好的效能 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="93dc7-105">`DirectCast` does not use the Visual Basic run-time helper routines for conversion, so it can provide somewhat better performance than `CType` when converting to and from data type `Object`.</span></span>  
  
 <span data-ttu-id="93dc7-106">您可以使用 `DirectCast` 關鍵字，類似于使用[CType 函數](../functions/ctype-function.md)和[TryCast Operator](trycast-operator.md)關鍵字的方式。</span><span class="sxs-lookup"><span data-stu-id="93dc7-106">You use the `DirectCast` keyword similar to the way you use the [CType Function](../functions/ctype-function.md) and the [TryCast Operator](trycast-operator.md) keyword.</span></span> <span data-ttu-id="93dc7-107">您會提供運算式做為第一個引數，以及要將它轉換成做為第二個引數的類型。</span><span class="sxs-lookup"><span data-stu-id="93dc7-107">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="93dc7-108">`DirectCast`需要兩個引數的資料類型之間的繼承或實現關聯性。</span><span class="sxs-lookup"><span data-stu-id="93dc7-108">`DirectCast` requires an inheritance or implementation relationship between the data types of the two arguments.</span></span> <span data-ttu-id="93dc7-109">這表示一種類型必須繼承或執行另一個。</span><span class="sxs-lookup"><span data-stu-id="93dc7-109">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="93dc7-110">錯誤和失敗</span><span class="sxs-lookup"><span data-stu-id="93dc7-110">Errors and Failures</span></span>  
 <span data-ttu-id="93dc7-111">`DirectCast`如果偵測到沒有繼承或實現關聯性存在，就會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="93dc7-111">`DirectCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="93dc7-112">但是缺少編譯器錯誤並不保證轉換成功。</span><span class="sxs-lookup"><span data-stu-id="93dc7-112">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="93dc7-113">如果想要的轉換縮小，可能會在執行時間失敗。</span><span class="sxs-lookup"><span data-stu-id="93dc7-113">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="93dc7-114">如果發生這種情況，執行時間就會擲回 <xref:System.InvalidCastException> 錯誤。</span><span class="sxs-lookup"><span data-stu-id="93dc7-114">If this happens, the runtime throws an <xref:System.InvalidCastException> error.</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="93dc7-115">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="93dc7-115">Conversion Keywords</span></span>  
 <span data-ttu-id="93dc7-116">類型轉換關鍵字的比較如下所示。</span><span class="sxs-lookup"><span data-stu-id="93dc7-116">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="93dc7-117">關鍵字</span><span class="sxs-lookup"><span data-stu-id="93dc7-117">Keyword</span></span>|<span data-ttu-id="93dc7-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="93dc7-118">Data types</span></span>|<span data-ttu-id="93dc7-119">引數關聯性</span><span class="sxs-lookup"><span data-stu-id="93dc7-119">Argument relationship</span></span>|<span data-ttu-id="93dc7-120">運行時失敗</span><span class="sxs-lookup"><span data-stu-id="93dc7-120">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="93dc7-121">CType Function</span><span class="sxs-lookup"><span data-stu-id="93dc7-121">CType Function</span></span>](../functions/ctype-function.md)|<span data-ttu-id="93dc7-122">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="93dc7-122">Any data types</span></span>|<span data-ttu-id="93dc7-123">必須在兩個資料類型之間定義擴展或縮小轉換</span><span class="sxs-lookup"><span data-stu-id="93dc7-123">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="93dc7-124">引發<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="93dc7-124">Throws <xref:System.InvalidCastException></span></span>|  
|`DirectCast`|<span data-ttu-id="93dc7-125">任何資料類型</span><span class="sxs-lookup"><span data-stu-id="93dc7-125">Any data types</span></span>|<span data-ttu-id="93dc7-126">一種類型必須繼承自或執行另一個類型</span><span class="sxs-lookup"><span data-stu-id="93dc7-126">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="93dc7-127">引發<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="93dc7-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="93dc7-128">TryCast 運算子</span><span class="sxs-lookup"><span data-stu-id="93dc7-128">TryCast Operator</span></span>](trycast-operator.md)|<span data-ttu-id="93dc7-129">僅限參考型別</span><span class="sxs-lookup"><span data-stu-id="93dc7-129">Reference types only</span></span>|<span data-ttu-id="93dc7-130">一種類型必須繼承自或執行另一個類型</span><span class="sxs-lookup"><span data-stu-id="93dc7-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="93dc7-131">不傳回[任何內容](../nothing.md)</span><span class="sxs-lookup"><span data-stu-id="93dc7-131">Returns [Nothing](../nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="93dc7-132">範例</span><span class="sxs-lookup"><span data-stu-id="93dc7-132">Example</span></span>  
 <span data-ttu-id="93dc7-133">下列範例示範的兩個用法 `DirectCast` ，一個在執行時間失敗，另一個成功。</span><span class="sxs-lookup"><span data-stu-id="93dc7-133">The following example demonstrates two uses of `DirectCast`, one that fails at run time and one that succeeds.</span></span>  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 <span data-ttu-id="93dc7-134">在上述範例中，的執行時間類型 `q` 是 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="93dc7-134">In the preceding example, the run-time type of `q` is `Double`.</span></span> <span data-ttu-id="93dc7-135">`CType`成功 `Double` ，因為可以轉換成 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="93dc7-135">`CType` succeeds because `Double` can be converted to `Integer`.</span></span> <span data-ttu-id="93dc7-136">不過，第一個 `DirectCast` 會在執行時間失敗，因為的執行時間類型 `Double` 與沒有繼承關聯性 `Integer` ，即使有轉換存在也一樣。</span><span class="sxs-lookup"><span data-stu-id="93dc7-136">However, the first `DirectCast` fails at run time because the run-time type of `Double` has no inheritance relationship with `Integer`, even though a conversion exists.</span></span> <span data-ttu-id="93dc7-137">第二個 `DirectCast` 成功，因為它會從類型轉換 <xref:System.Windows.Forms.Form> 成類型 <xref:System.Windows.Forms.Control> ，而從它 <xref:System.Windows.Forms.Form> 繼承。</span><span class="sxs-lookup"><span data-stu-id="93dc7-137">The second `DirectCast` succeeds because it converts from type <xref:System.Windows.Forms.Form> to type <xref:System.Windows.Forms.Control>, from which <xref:System.Windows.Forms.Form> inherits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93dc7-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93dc7-138">See also</span></span>

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="93dc7-139">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="93dc7-139">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="93dc7-140">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="93dc7-140">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
