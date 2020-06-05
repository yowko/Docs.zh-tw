---
title: CType Function
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406426"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="09154-102">CType 函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09154-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="09154-103">傳回將運算式明確轉換成指定之資料類型、物件、結構、類別或介面的結果。</span><span class="sxs-lookup"><span data-stu-id="09154-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="09154-104">語法</span><span class="sxs-lookup"><span data-stu-id="09154-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="09154-105">組件</span><span class="sxs-lookup"><span data-stu-id="09154-105">Parts</span></span>

<span data-ttu-id="09154-106">`expression`任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="09154-106">`expression` Any valid expression.</span></span> <span data-ttu-id="09154-107">如果的值 `expression` 超出允許的範圍，Visual Basic 會擲回 `typename` 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="09154-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="09154-108">`typename`語句中子句內任何合法的運算式 `As` `Dim` ，也就是任何資料類型、物件、結構、類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="09154-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="09154-109">備註</span><span class="sxs-lookup"><span data-stu-id="09154-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="09154-110">您也可以使用下列函數來執行類型轉換：</span><span class="sxs-lookup"><span data-stu-id="09154-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="09154-111">類型轉換函式 `CByte` ，例如、 `CDbl` 和， `CInt` 會執行特定資料類型的轉換。</span><span class="sxs-lookup"><span data-stu-id="09154-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="09154-112">如需詳細資訊，請參閱 [類型轉換函數](type-conversion-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="09154-112">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="09154-113">[DirectCast 運算子](../operators/directcast-operator.md)或[TryCast 運算子](../operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="09154-113">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="09154-114">這些運算子需要一個型別繼承自或執行另一個型別。</span><span class="sxs-lookup"><span data-stu-id="09154-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="09154-115">它們可以提供比 `CType` 資料類型來回轉換時更好的效能 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="09154-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="09154-116">`CType`是以內嵌方式編譯，這表示轉換程式碼是評估運算式之程式碼的一部分。</span><span class="sxs-lookup"><span data-stu-id="09154-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="09154-117">在某些情況下，程式碼的執行速度會更快，因為不會呼叫任何程式來執行轉換。</span><span class="sxs-lookup"><span data-stu-id="09154-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="09154-118">如果未將任何轉換從定義 `expression` 為 `typename` （例如，從 `Integer` 到 `Date` ），Visual Basic 會顯示編譯時期錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="09154-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="09154-119">如果轉換在執行時間失敗，則會擲回適當的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="09154-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="09154-120">如果縮小轉換失敗， <xref:System.OverflowException> 則是最常見的結果。</span><span class="sxs-lookup"><span data-stu-id="09154-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="09154-121">如果未定義轉換，則會擲回 <xref:System.InvalidCastException> 。</span><span class="sxs-lookup"><span data-stu-id="09154-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="09154-122">例如，如果 `expression` 的型別為 `Object` ，而且其執行時間型別沒有轉換成，就可能發生這種情況 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="09154-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="09154-123">如果或的資料類型 `expression` `typename` 是您已定義的類別或結構，您可以 `CType` 在該類別或結構上將定義為轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="09154-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="09154-124">這會使成為多載 `CType` *運算子*。</span><span class="sxs-lookup"><span data-stu-id="09154-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="09154-125">如果您這樣做，您可以控制從類別或結構轉換的行為，包括可以擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="09154-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="09154-126">多載化</span><span class="sxs-lookup"><span data-stu-id="09154-126">Overloading</span></span>

<span data-ttu-id="09154-127">`CType`運算子也可以在程式碼外部定義的類別或結構上多載。</span><span class="sxs-lookup"><span data-stu-id="09154-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="09154-128">如果您的程式碼會在這類類別或結構之間進行轉換，請確定您瞭解其 `CType` 運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="09154-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="09154-129">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="09154-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="09154-130">轉換動態物件</span><span class="sxs-lookup"><span data-stu-id="09154-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="09154-131">動態物件的類型轉換是由使用或方法的使用者定義動態轉換所 <xref:System.Dynamic.DynamicObject.TryConvert%2A> 執行 <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> 。</span><span class="sxs-lookup"><span data-stu-id="09154-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="09154-132">如果您使用的是動態物件，請使用 <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> 方法來轉換動態物件。</span><span class="sxs-lookup"><span data-stu-id="09154-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="09154-133">範例</span><span class="sxs-lookup"><span data-stu-id="09154-133">Example</span></span>

<span data-ttu-id="09154-134">下列範例會使用 `CType` 函數，將運算式轉換為 `Single` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="09154-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="09154-135">如需其他範例，請參閱[隱含和明確轉換](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="09154-135">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09154-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09154-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="09154-137">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="09154-137">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="09154-138">轉換函式</span><span class="sxs-lookup"><span data-stu-id="09154-138">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="09154-139">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="09154-139">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="09154-140">How to: Define a Conversion Operator</span><span class="sxs-lookup"><span data-stu-id="09154-140">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="09154-141">.NET Framework 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="09154-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
