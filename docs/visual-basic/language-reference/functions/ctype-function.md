---
title: "CType 函式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d804ce75929592675068fdc434a1ba7429fa5373
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="74edc-102">CType 函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74edc-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="74edc-103">傳回運算式明確轉換指定的資料類型、 物件、 結構、 類別或介面的結果。</span><span class="sxs-lookup"><span data-stu-id="74edc-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74edc-104">語法</span><span class="sxs-lookup"><span data-stu-id="74edc-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="74edc-105">組件</span><span class="sxs-lookup"><span data-stu-id="74edc-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="74edc-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="74edc-106">Any valid expression.</span></span> <span data-ttu-id="74edc-107">如果值`expression`超出所允許的範圍`typename`，Visual Basic 會擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74edc-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="74edc-108">任何運算式中合法`As`中的子句`Dim`陳述式，也就是任何資料類型、 物件、 結構、 類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="74edc-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74edc-109">備註</span><span class="sxs-lookup"><span data-stu-id="74edc-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="74edc-110">您也可以使用下列函數來執行類型轉換：</span><span class="sxs-lookup"><span data-stu-id="74edc-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="74edc-111">類型轉換函式，例如`CByte`， `CDbl`，和`CInt`來執行特定資料型別轉換。</span><span class="sxs-lookup"><span data-stu-id="74edc-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="74edc-112">如需詳細資訊，請參閱[類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="74edc-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="74edc-113">[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)或[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="74edc-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="74edc-114">這些運算子需要一種類型繼承自或實作其他的型別。</span><span class="sxs-lookup"><span data-stu-id="74edc-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="74edc-115">它們可以提供稍微較佳的效能比`CType`時的轉換`Object`資料型別。</span><span class="sxs-lookup"><span data-stu-id="74edc-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="74edc-116">`CType`已編譯的內嵌，這表示，轉換程式碼的程式碼可評估運算式的一部分。</span><span class="sxs-lookup"><span data-stu-id="74edc-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="74edc-117">在某些情況下，更快的程式碼執行因為程序不會呼叫以執行轉換。</span><span class="sxs-lookup"><span data-stu-id="74edc-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="74edc-118">如果沒有轉換定義從`expression`至`typename`(例如，從`Integer`至`Date`)，Visual Basic 會顯示編譯時間錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="74edc-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="74edc-119">如果轉換失敗，在執行階段，會擲回適當的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74edc-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="74edc-120">如果有縮小轉換失敗，<xref:System.OverflowException>是最常見的結果。</span><span class="sxs-lookup"><span data-stu-id="74edc-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="74edc-121">如果未定義，轉換<xref:System.InvalidCastException>在擲回。</span><span class="sxs-lookup"><span data-stu-id="74edc-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="74edc-122">比方說，這種情況`expression`的型別`Object`不轉換成它的執行階段型別且`typename`。</span><span class="sxs-lookup"><span data-stu-id="74edc-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="74edc-123">資料類型，是否`expression`或`typename`是類別或結構，您定義了，您可以定義`CType`上該類別或結構做為轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="74edc-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="74edc-124">這可讓`CType`做為*多載運算子*。</span><span class="sxs-lookup"><span data-stu-id="74edc-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="74edc-125">如果您這樣做，您可以控制之間的轉換與類別或結構，包括可能會擲回的例外狀況行為。</span><span class="sxs-lookup"><span data-stu-id="74edc-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="74edc-126">多載化</span><span class="sxs-lookup"><span data-stu-id="74edc-126">Overloading</span></span>  
 <span data-ttu-id="74edc-127">`CType`運算子也能在類別或您的程式碼之外定義的結構上多載。</span><span class="sxs-lookup"><span data-stu-id="74edc-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="74edc-128">如果您的程式碼轉換，或從這類類別或結構，請務必了解的行為及其`CType`運算子。</span><span class="sxs-lookup"><span data-stu-id="74edc-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="74edc-129">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="74edc-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="74edc-130">轉換的動態物件</span><span class="sxs-lookup"><span data-stu-id="74edc-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="74edc-131">動態物件的類型轉換都是透過使用者定義的動態轉換使用<xref:System.Dynamic.DynamicObject.TryConvert%2A>或<xref:System.Dynamic.DynamicMetaObject.BindConvert%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="74edc-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="74edc-132">如果您使用動態物件，使用<xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A>方法，將轉換的動態物件。</span><span class="sxs-lookup"><span data-stu-id="74edc-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74edc-133">範例</span><span class="sxs-lookup"><span data-stu-id="74edc-133">Example</span></span>  
 <span data-ttu-id="74edc-134">下列範例會使用`CType`函式將轉換運算式，以便`Single`資料型別。</span><span class="sxs-lookup"><span data-stu-id="74edc-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 <span data-ttu-id="74edc-135">如需其他範例，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="74edc-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74edc-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="74edc-136">See Also</span></span>  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="74edc-137">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="74edc-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="74edc-138">轉換函式</span><span class="sxs-lookup"><span data-stu-id="74edc-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="74edc-139">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="74edc-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="74edc-140">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="74edc-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="74edc-141">.NET Framework 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="74edc-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
