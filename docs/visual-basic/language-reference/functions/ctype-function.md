---
title: CType 函式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 8f60edb2b5e2dba15526169ef10bc05c1f50a7f1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970008"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="78305-102">CType 函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78305-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="78305-103">傳回運算式明確轉換至指定的資料類型、 物件、 結構、 類別或介面的結果。</span><span class="sxs-lookup"><span data-stu-id="78305-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78305-104">語法</span><span class="sxs-lookup"><span data-stu-id="78305-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="78305-105">組件</span><span class="sxs-lookup"><span data-stu-id="78305-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="78305-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="78305-106">Any valid expression.</span></span> <span data-ttu-id="78305-107">如果值`expression`超出所允許的範圍`typename`，Visual Basic 會擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="78305-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="78305-108">任何運算式中合法`As`子句中的`Dim`陳述式，也就是任何資料類型、 物件、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="78305-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78305-109">備註</span><span class="sxs-lookup"><span data-stu-id="78305-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="78305-110">您也可以使用下列函式來執行類型轉換：</span><span class="sxs-lookup"><span data-stu-id="78305-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="78305-111">這類類型轉換函式`CByte`， `CDbl`，和`CInt`執行特定的資料型別轉換。</span><span class="sxs-lookup"><span data-stu-id="78305-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="78305-112">如需詳細資訊，請參閱 <<c0> [ 類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="78305-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="78305-113">[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或是[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="78305-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="78305-114">這些運算子需要一種型別繼承自或實作另一個型別。</span><span class="sxs-lookup"><span data-stu-id="78305-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="78305-115">它們可以提供略微好的效能比`CType`來回轉換時`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="78305-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="78305-116">`CType` 已編譯的內嵌，這表示，轉換程式碼就會評估運算式的程式碼的一部分。</span><span class="sxs-lookup"><span data-stu-id="78305-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="78305-117">在某些情況下，更快的程式碼執行因為程序不會呼叫來執行轉換。</span><span class="sxs-lookup"><span data-stu-id="78305-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="78305-118">如果沒有任何轉換從定義`expression`要`typename`(例如，從`Integer`至`Date`)，Visual Basic 會顯示編譯時間錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="78305-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="78305-119">如果在執行階段發生轉換失敗，則會擲回適當的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="78305-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="78305-120">如果縮小轉換失敗，<xref:System.OverflowException>是最常見的結果。</span><span class="sxs-lookup"><span data-stu-id="78305-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="78305-121">如果轉換，則未定義，<xref:System.InvalidCastException>中擲回。</span><span class="sxs-lookup"><span data-stu-id="78305-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="78305-122">比方說，如果此情形`expression`屬於型別`Object`不會轉換為其執行階段型別且`typename`。</span><span class="sxs-lookup"><span data-stu-id="78305-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="78305-123">資料類型，是否`expression`或是`typename`是類別或結構定義之後，您可以定義`CType`上該類別或結構為轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="78305-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="78305-124">這可讓`CType`充當*多載運算子*。</span><span class="sxs-lookup"><span data-stu-id="78305-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="78305-125">如果您這麼做，您可以控制轉換從您的類別或結構，包括可能擲回的例外狀況的行為。</span><span class="sxs-lookup"><span data-stu-id="78305-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="78305-126">多載化</span><span class="sxs-lookup"><span data-stu-id="78305-126">Overloading</span></span>  
 <span data-ttu-id="78305-127">`CType`可以也在類別或結構的程式碼外部定義上多載運算子。</span><span class="sxs-lookup"><span data-stu-id="78305-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="78305-128">如果您的程式碼將轉換至或從這類類別或結構時，務必了解的行為及其`CType`運算子。</span><span class="sxs-lookup"><span data-stu-id="78305-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="78305-129">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="78305-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="78305-130">轉換的動態物件</span><span class="sxs-lookup"><span data-stu-id="78305-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="78305-131">動態物件的類型轉換由使用者定義的使用動態轉換<xref:System.Dynamic.DynamicObject.TryConvert%2A>或<xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="78305-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="78305-132">如果您正在使用動態物件，使用<xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>方法轉換動態物件。</span><span class="sxs-lookup"><span data-stu-id="78305-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78305-133">範例</span><span class="sxs-lookup"><span data-stu-id="78305-133">Example</span></span>  
 <span data-ttu-id="78305-134">下列範例會使用`CType`函式將轉換運算式，以`Single`資料型別。</span><span class="sxs-lookup"><span data-stu-id="78305-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]  
  
 <span data-ttu-id="78305-135">如需其他範例，請參閱 <<c0> [ 隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="78305-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78305-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78305-136">See also</span></span>
- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="78305-137">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="78305-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="78305-138">轉換函式</span><span class="sxs-lookup"><span data-stu-id="78305-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="78305-139">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="78305-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="78305-140">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="78305-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="78305-141">.NET Framework 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="78305-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
