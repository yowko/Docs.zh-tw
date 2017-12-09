---
title: Long
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: "49"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 238f64001b097b86306e0ed9630bd5df2e6a189f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="option-strict-statement"></a><span data-ttu-id="a230c-102">Long</span><span class="sxs-lookup"><span data-stu-id="a230c-102">Option Strict Statement</span></span>
<span data-ttu-id="a230c-103">不允許晚期繫結，且允許隱含型別，結果中，會限制為只有擴展轉換的隱含資料類型轉換`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="a230c-103">Restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a230c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a230c-104">Syntax</span></span>  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="a230c-105">組件</span><span class="sxs-lookup"><span data-stu-id="a230c-105">Parts</span></span>  
  
|<span data-ttu-id="a230c-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="a230c-106">Term</span></span>|<span data-ttu-id="a230c-107">定義</span><span class="sxs-lookup"><span data-stu-id="a230c-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="a230c-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a230c-108">Optional.</span></span> <span data-ttu-id="a230c-109">可讓`Option Strict`檢查。</span><span class="sxs-lookup"><span data-stu-id="a230c-109">Enables `Option Strict` checking.</span></span>|  
|`Off`|<span data-ttu-id="a230c-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a230c-110">Optional.</span></span> <span data-ttu-id="a230c-111">停用`Option Strict`檢查。</span><span class="sxs-lookup"><span data-stu-id="a230c-111">Disables `Option Strict` checking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a230c-112">備註</span><span class="sxs-lookup"><span data-stu-id="a230c-112">Remarks</span></span>  
 <span data-ttu-id="a230c-113">當`Option Strict On`或`Option Strict`會出現在檔案中，在下列情況會導致編譯時間錯誤：</span><span class="sxs-lookup"><span data-stu-id="a230c-113">When `Option Strict On` or `Option Strict` appears in a file, the following conditions cause a compile-time error:</span></span>  
  
-   <span data-ttu-id="a230c-114">隱含的縮小轉換</span><span class="sxs-lookup"><span data-stu-id="a230c-114">Implicit narrowing conversions</span></span>  
  
-   <span data-ttu-id="a230c-115">晚期繫結</span><span class="sxs-lookup"><span data-stu-id="a230c-115">Late binding</span></span>  
  
-   <span data-ttu-id="a230c-116">隱含類型導致`Object`類型</span><span class="sxs-lookup"><span data-stu-id="a230c-116">Implicit typing that results in an `Object` type</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a230c-117">您可以設定的警告組態[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，有三個設定對應至三個條件會造成編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-117">In the warning configurations that you can set on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), there are three settings that correspond to the three conditions that cause a compile-time error.</span></span> <span data-ttu-id="a230c-118">如需如何使用這些設定的資訊，請參閱[在 IDE 中設定警告組態](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)本主題稍後。</span><span class="sxs-lookup"><span data-stu-id="a230c-118">For information about how to use these settings, see [To set warning configurations in the IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) later in this topic.</span></span>  
  
 <span data-ttu-id="a230c-119">`Option Strict Off`陳述式，則會關閉錯誤和警告檢查所有的三個條件，即使開啟這些錯誤或警告，指定相關聯的 IDE 設定。</span><span class="sxs-lookup"><span data-stu-id="a230c-119">The `Option Strict Off` statement turns off error and warning checking for all three conditions, even if the associated IDE settings specify to turn on these errors or warnings.</span></span> <span data-ttu-id="a230c-120">`Option Strict On`陳述式會開啟錯誤和警告檢查所有的三個條件，即使相關聯的 IDE 設定指定要關閉這些錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="a230c-120">The `Option Strict On` statement turns on error and warning checking for all three conditions, even if the associated IDE settings specify to turn off these errors or warnings.</span></span>  
  
 <span data-ttu-id="a230c-121">如果單獨使用，`Option Strict`陳述式必須出現在檔案中任何其他程式碼陳述式之前。</span><span class="sxs-lookup"><span data-stu-id="a230c-121">If used, the `Option Strict` statement must appear before any other code statements in a file.</span></span>  
  
 <span data-ttu-id="a230c-122">當您將`Option Strict`至`On`，Visual Basic 會檢查所有的程式設計項目會指定資料類型。</span><span class="sxs-lookup"><span data-stu-id="a230c-122">When you set `Option Strict` to `On`, Visual Basic checks that data types are specified for all programming elements.</span></span> <span data-ttu-id="a230c-123">資料類型可以明確地指定，或使用區域類型推斷來指定。</span><span class="sxs-lookup"><span data-stu-id="a230c-123">Data types can be specified explicitly, or specified by using local type inference.</span></span> <span data-ttu-id="a230c-124">指定資料類型的所有程式設計項目建議使用，原因如下：</span><span class="sxs-lookup"><span data-stu-id="a230c-124">Specifying data types for all your programming elements is recommended, for the following reasons:</span></span>  
  
-   <span data-ttu-id="a230c-125">它可讓您的變數和參數的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="a230c-125">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="a230c-126">這可讓您查看其屬性和其他成員，當您輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="a230c-126">This enables you to see their properties and other members as you type code.</span></span>  
  
-   <span data-ttu-id="a230c-127">它可讓編譯器執行類型檢查。</span><span class="sxs-lookup"><span data-stu-id="a230c-127">It enables the compiler to perform type checking.</span></span> <span data-ttu-id="a230c-128">類型檢查可協助您尋找可以在執行階段失敗，因為型別轉換錯誤的陳述式。</span><span class="sxs-lookup"><span data-stu-id="a230c-128">Type checking helps you find statements that can fail at run time because of type conversion errors.</span></span> <span data-ttu-id="a230c-129">它也可以識別不支援這些方法的物件上方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a230c-129">It also identifies calls to methods on objects that do not support those methods.</span></span>  
  
-   <span data-ttu-id="a230c-130">它能加速程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="a230c-130">It speeds up the execution of code.</span></span> <span data-ttu-id="a230c-131">其中一個原因是，如果您未指定資料類型的程式設計項目，Visual Basic 編譯器將其指派`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="a230c-131">One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type.</span></span> <span data-ttu-id="a230c-132">可能需要編譯的程式碼之間來回轉換`Object`和其他資料類型，這會降低效能。</span><span class="sxs-lookup"><span data-stu-id="a230c-132">Compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="implicit-narrowing-conversion-errors"></a><span data-ttu-id="a230c-133">隱含的縮小轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="a230c-133">Implicit Narrowing Conversion Errors</span></span>  
 <span data-ttu-id="a230c-134">是縮小轉換的隱含資料類型轉換時，就會發生隱含的縮小轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-134">Implicit narrowing conversion errors occur when there is an implicit data type conversion that is a narrowing conversion.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a230c-135">可以將許多資料類型轉換成其他資料型別。</span><span class="sxs-lookup"><span data-stu-id="a230c-135"> can convert many data types to other data types.</span></span> <span data-ttu-id="a230c-136">一種資料類型的值轉換為具有較少的有效位數或容量較小的資料類型時，就可能發生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="a230c-136">Data loss can occur when the value of one data type is converted to a data type that has less precision or a smaller capacity.</span></span> <span data-ttu-id="a230c-137">如果這類縮小轉換會失敗，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-137">A run-time error occurs if such a narrowing conversion fails.</span></span> <span data-ttu-id="a230c-138">`Option Strict`可確保這些縮小轉換的編譯時期通知，以便加以避免。</span><span class="sxs-lookup"><span data-stu-id="a230c-138">`Option Strict` ensures compile-time notification of these narrowing conversions so that you can avoid them.</span></span> <span data-ttu-id="a230c-139">如需詳細資訊，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)和[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="a230c-139">For more information, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) and [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="a230c-140">可能會導致錯誤的轉換會在運算式中包含所發生的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="a230c-140">Conversions that can cause errors include implicit conversions that occur in expressions.</span></span> <span data-ttu-id="a230c-141">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="a230c-141">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="a230c-142">+ 運算子</span><span class="sxs-lookup"><span data-stu-id="a230c-142">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [<span data-ttu-id="a230c-143">+= 運算子</span><span class="sxs-lookup"><span data-stu-id="a230c-143">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [<span data-ttu-id="a230c-144">\ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a230c-144">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [<span data-ttu-id="a230c-145">/ = 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a230c-145">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [<span data-ttu-id="a230c-146">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="a230c-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 <span data-ttu-id="a230c-147">當您使用串連字串[& 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)，所有轉換的字串會被都視為擴展。</span><span class="sxs-lookup"><span data-stu-id="a230c-147">When you concatenate strings by using the [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), all conversions to the strings are considered to be widening.</span></span> <span data-ttu-id="a230c-148">讓這些轉換不會產生隱含縮小轉換錯誤，即使`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="a230c-148">So these conversions do not generate an implicit narrowing conversion error, even if `Option Strict` is on.</span></span>  
  
 <span data-ttu-id="a230c-149">如果有縮小轉換，當您呼叫具有對應的參數不同的資料類型的引數的方法時，導致編譯時間錯誤`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="a230c-149">When you call a method that has an argument that has a data type different from the corresponding parameter, a narrowing conversion causes a compile-time error if `Option Strict` is on.</span></span> <span data-ttu-id="a230c-150">您可以使用擴展轉換或明確轉換，以避免產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-150">You can avoid the compile-time error by using a widening conversion or an explicit conversion.</span></span>  
  
 <span data-ttu-id="a230c-151">隱含的縮小轉換錯誤會在編譯時期轉換中的項目隱藏`For Each…Next`迴圈控制變數的集合。</span><span class="sxs-lookup"><span data-stu-id="a230c-151">Implicit narrowing conversion errors are suppressed at compile-time for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="a230c-152">發生這種情況即使`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="a230c-152">This occurs even if `Option Strict` is on.</span></span> <span data-ttu-id="a230c-153">如需詳細資訊，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a230c-153">For more information, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="late-binding-errors"></a><span data-ttu-id="a230c-154">晚期繫結錯誤</span><span class="sxs-lookup"><span data-stu-id="a230c-154">Late Binding Errors</span></span>  
 <span data-ttu-id="a230c-155">物件晚期繫結指派至屬性或方法宣告為類型的變數時`Object`。</span><span class="sxs-lookup"><span data-stu-id="a230c-155">An object is late bound when it is assigned to a property or method of a variable that is declared to be of type `Object`.</span></span> <span data-ttu-id="a230c-156">如需詳細資訊，請參閱[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a230c-156">For more information, see [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>  
  
## <a name="implicit-object-type-errors"></a><span data-ttu-id="a230c-157">隱含的物件類型錯誤</span><span class="sxs-lookup"><span data-stu-id="a230c-157">Implicit Object Type Errors</span></span>  
 <span data-ttu-id="a230c-158">隱含的物件類型錯誤發生時適當的類型不能是推斷為宣告的變數，因此一種`Object`會推斷而來。</span><span class="sxs-lookup"><span data-stu-id="a230c-158">Implicit object type errors occur when an appropriate type cannot be inferred for a declared variable, so a type of `Object` is inferred.</span></span> <span data-ttu-id="a230c-159">這主要是當您使用時發生`Dim`陳述式來宣告變數，而不使用`As`子句，和`Option Infer`已關閉。</span><span class="sxs-lookup"><span data-stu-id="a230c-159">This primarily occurs when you use a `Dim` statement to declare a variable without using an `As` clause, and `Option Infer` is off.</span></span> <span data-ttu-id="a230c-160">如需詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[Visual Basic 語言規格](../../../visual-basic/reference/language-specification/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a230c-160">For more information, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>  
  
 <span data-ttu-id="a230c-161">方法參數`As`子句是選擇性的如果`Option Strict`已關閉。</span><span class="sxs-lookup"><span data-stu-id="a230c-161">For method parameters, the `As` clause is optional if `Option Strict` is off.</span></span> <span data-ttu-id="a230c-162">不過，如果任何一個參數使用`As`子句，它們都必須使用它。</span><span class="sxs-lookup"><span data-stu-id="a230c-162">However, if any one parameter uses an `As` clause, they all must use it.</span></span> <span data-ttu-id="a230c-163">如果`Option Strict`已開啟，`As`子句是必要的每個參數定義。</span><span class="sxs-lookup"><span data-stu-id="a230c-163">If `Option Strict` is on, the `As` clause is required for every parameter definition.</span></span>  
  
 <span data-ttu-id="a230c-164">如果您宣告變數，而不使用`As`子句並將它設定為`Nothing`，變數會有一種`Object`。</span><span class="sxs-lookup"><span data-stu-id="a230c-164">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="a230c-165">任何編譯時間錯誤，就會發生這種情況下時`Option Strict`上和`Option Infer`上。</span><span class="sxs-lookup"><span data-stu-id="a230c-165">No compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is on.</span></span> <span data-ttu-id="a230c-166">舉例來說，這是`Dim something = Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a230c-166">An example of this is `Dim something = Nothing`.</span></span>  
  
### <a name="default-data-types-and-values"></a><span data-ttu-id="a230c-167">預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="a230c-167">Default Data Types and Values</span></span>  
 <span data-ttu-id="a230c-168">下表描述的指定資料類型和初始設定式中的各種組合結果[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a230c-168">The following table describes the results of various combinations of specifying the data type and initializer in a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
|<span data-ttu-id="a230c-169">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="a230c-169">Data type specified?</span></span>|<span data-ttu-id="a230c-170">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="a230c-170">Initializer specified?</span></span>|<span data-ttu-id="a230c-171">範例</span><span class="sxs-lookup"><span data-stu-id="a230c-171">Example</span></span>|<span data-ttu-id="a230c-172">結果</span><span class="sxs-lookup"><span data-stu-id="a230c-172">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="a230c-173">否</span><span class="sxs-lookup"><span data-stu-id="a230c-173">No</span></span>|<span data-ttu-id="a230c-174">否</span><span class="sxs-lookup"><span data-stu-id="a230c-174">No</span></span>|`Dim qty`|<span data-ttu-id="a230c-175">如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="a230c-175">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="a230c-176">如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-176">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="a230c-177">否</span><span class="sxs-lookup"><span data-stu-id="a230c-177">No</span></span>|<span data-ttu-id="a230c-178">是</span><span class="sxs-lookup"><span data-stu-id="a230c-178">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="a230c-179">如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a230c-179">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="a230c-180">請參閱[區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="a230c-180">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="a230c-181">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a230c-181">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="a230c-182">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-182">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="a230c-183">是</span><span class="sxs-lookup"><span data-stu-id="a230c-183">Yes</span></span>|<span data-ttu-id="a230c-184">否</span><span class="sxs-lookup"><span data-stu-id="a230c-184">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="a230c-185">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="a230c-185">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="a230c-186">如需詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a230c-186">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="a230c-187">是</span><span class="sxs-lookup"><span data-stu-id="a230c-187">Yes</span></span>|<span data-ttu-id="a230c-188">是</span><span class="sxs-lookup"><span data-stu-id="a230c-188">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="a230c-189">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-189">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a><span data-ttu-id="a230c-190">Option Strict 陳述式時不存在</span><span class="sxs-lookup"><span data-stu-id="a230c-190">When an Option Strict Statement Is Not Present</span></span>  
 <span data-ttu-id="a230c-191">如果不包含原始碼`Option Strict`陳述式，**選項嚴格**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="a230c-191">If the source code does not contain an `Option Strict` statement, the **Option strict** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="a230c-192">**編譯網頁**已設定，可提供其他控制產生錯誤的狀況。</span><span class="sxs-lookup"><span data-stu-id="a230c-192">The **Compile Page** has settings that provide additional control over the conditions that generate an error.</span></span>  
  
 <span data-ttu-id="a230c-193">如果您使用命令列編譯器時，您可以使用[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項以指定的設定`Option Strict`。</span><span class="sxs-lookup"><span data-stu-id="a230c-193">If you are using the command-line compiler, you can use the [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option to specify a setting for `Option Strict`.</span></span>  
  
### <a name="to-set-option-strict-in-the-ide"></a><span data-ttu-id="a230c-194">若要在 IDE 中設定 Option Strict</span><span class="sxs-lookup"><span data-stu-id="a230c-194">To set Option Strict in the IDE</span></span>  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  <span data-ttu-id="a230c-195">在方案總管中選取專案。</span><span class="sxs-lookup"><span data-stu-id="a230c-195">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="a230c-196">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a230c-196">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="a230c-197">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="a230c-197">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="a230c-198">在**編譯**索引標籤上，設定中的值**Option Strict**方塊。</span><span class="sxs-lookup"><span data-stu-id="a230c-198">On the **Compile** tab, set the value in the **Option Strict** box.</span></span>  
  
###  <a name="conditions"></a><span data-ttu-id="a230c-199">若要在 IDE 中設定警告組態</span><span class="sxs-lookup"><span data-stu-id="a230c-199">To set warning configurations in the IDE</span></span>  
 <span data-ttu-id="a230c-200">當您使用[編譯的頁面上，專案設計工具 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)而不是`Option Strict`陳述式中，您有其他控制產生錯誤的狀況。</span><span class="sxs-lookup"><span data-stu-id="a230c-200">When you use the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) instead of an `Option Strict` statement, you have additional control over the conditions that generate errors.</span></span> <span data-ttu-id="a230c-201">**警告組態**區段**編譯網頁**的設定會對應至三個條件會造成編譯時間錯誤時`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="a230c-201">The **Warning configurations** section of the **Compile Page** has settings that correspond to the three conditions that cause a compile-time error when `Option Strict` is on.</span></span> <span data-ttu-id="a230c-202">以下是這些設定：</span><span class="sxs-lookup"><span data-stu-id="a230c-202">Following are these settings:</span></span>  
  
-   <span data-ttu-id="a230c-203">**隱含轉換**</span><span class="sxs-lookup"><span data-stu-id="a230c-203">**Implicit conversion**</span></span>  
  
-   <span data-ttu-id="a230c-204">**晚期繫結，執行階段時呼叫可能失敗**</span><span class="sxs-lookup"><span data-stu-id="a230c-204">**Late binding; call could fail at run time**</span></span>  
  
-   <span data-ttu-id="a230c-205">**隱含類型。假設是 object**</span><span class="sxs-lookup"><span data-stu-id="a230c-205">**Implicit type; object assumed**</span></span>  
  
 <span data-ttu-id="a230c-206">當您將**Option Strict**至**上**，這三個這些警告的組態設定會設定為**錯誤**。</span><span class="sxs-lookup"><span data-stu-id="a230c-206">When you set **Option Strict** to **On**, all three of these warning configuration settings are set to **Error**.</span></span> <span data-ttu-id="a230c-207">當您將**Option Strict**至**關閉**，所有三項設定會設定為**無**。</span><span class="sxs-lookup"><span data-stu-id="a230c-207">When you set **Option Strict** to **Off**, all three settings are set to **None**.</span></span>  
  
 <span data-ttu-id="a230c-208">您可以個別變更每個警告的組態設定為**無**，**警告**，或**錯誤**。</span><span class="sxs-lookup"><span data-stu-id="a230c-208">You can individually change each warning configuration setting to **None**, **Warning**, or **Error**.</span></span> <span data-ttu-id="a230c-209">如果所有三個警告的組態設定會設定為**錯誤**，`On`會出現在`Option strict`方塊。</span><span class="sxs-lookup"><span data-stu-id="a230c-209">If all three warning configuration settings are set to **Error**, `On` appears in the `Option strict` box.</span></span> <span data-ttu-id="a230c-210">如果這三個設定為**無**，`Off`出現在此方塊。</span><span class="sxs-lookup"><span data-stu-id="a230c-210">If all three are set to **None**, `Off` appears in this box.</span></span> <span data-ttu-id="a230c-211">這些設定，任何其他組合**（自訂）**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="a230c-211">For any other combination of these settings, **(custom)** appears.</span></span>  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a><span data-ttu-id="a230c-212">若要設定 Option Strict 預設設定為新專案</span><span class="sxs-lookup"><span data-stu-id="a230c-212">To set the Option Strict default setting for new projects</span></span>  
 <span data-ttu-id="a230c-213">當您建立專案， **Option Strict**上設定**編譯** 索引標籤設為**Option Strict**中設定**選項**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a230c-213">When you create a project, the **Option Strict** setting on the **Compile** tab is set to the **Option Strict** setting in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="a230c-214">若要設定`Option Strict`在此對話方塊，請在**工具**功能表上，按一下**選項**。</span><span class="sxs-lookup"><span data-stu-id="a230c-214">To set `Option Strict` in this dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="a230c-215">在**選項**對話方塊方塊中，展開 **專案和方案**，然後按一下  **VB 預設值**。</span><span class="sxs-lookup"><span data-stu-id="a230c-215">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="a230c-216">中的初始預設設定**VB 預設值**是`Off`。</span><span class="sxs-lookup"><span data-stu-id="a230c-216">The initial default setting in **VB Defaults** is `Off`.</span></span>  
  
### <a name="to-set-option-strict-on-the-command-line"></a><span data-ttu-id="a230c-217">若要在命令列上設定 Option Strict</span><span class="sxs-lookup"><span data-stu-id="a230c-217">To set Option Strict on the command line</span></span>  
 <span data-ttu-id="a230c-218">包含[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項在**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="a230c-218">Include the [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a230c-219">範例</span><span class="sxs-lookup"><span data-stu-id="a230c-219">Example</span></span>  
 <span data-ttu-id="a230c-220">下列範例示範隱含類型轉換縮小轉換，所造成的編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-220">The following examples demonstrate compile-time errors caused by implicit type conversions that are narrowing conversions.</span></span> <span data-ttu-id="a230c-221">這類錯誤對應於**隱含轉換**條件上**編譯網頁**。</span><span class="sxs-lookup"><span data-stu-id="a230c-221">This category of errors corresponds to the **Implicit conversion** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="a230c-222">範例</span><span class="sxs-lookup"><span data-stu-id="a230c-222">Example</span></span>  
 <span data-ttu-id="a230c-223">下列範例會示範晚期繫結所造成的編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="a230c-223">The following example demonstrates a compile-time error caused by late binding.</span></span> <span data-ttu-id="a230c-224">這類錯誤對應於**最遲繫結，在執行階段無法呼叫**條件上**編譯網頁**。</span><span class="sxs-lookup"><span data-stu-id="a230c-224">This category of errors corresponds to the **Late binding; call could fail at run time** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a230c-225">範例</span><span class="sxs-lookup"><span data-stu-id="a230c-225">Example</span></span>  
 <span data-ttu-id="a230c-226">下列範例示範具有隱含的類型宣告的變數所造成的錯誤`Object`。</span><span class="sxs-lookup"><span data-stu-id="a230c-226">The following examples demonstrate errors caused by variables that are declared with an implicit type of `Object`.</span></span> <span data-ttu-id="a230c-227">這類錯誤對應於**隱含的類型; 假設是 object**條件上**編譯網頁**。</span><span class="sxs-lookup"><span data-stu-id="a230c-227">This category of errors corresponds to the **Implicit type; object assumed** condition on the **Compile Page**.</span></span>  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a230c-228">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a230c-228">See Also</span></span>  
 [<span data-ttu-id="a230c-229">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="a230c-229">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="a230c-230">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="a230c-230">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="a230c-231">專案設計工具、編譯頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a230c-231">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="a230c-232">Option Explicit 陳述式</span><span class="sxs-lookup"><span data-stu-id="a230c-232">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="a230c-233">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="a230c-233">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="a230c-234">如何：存取物件的成員</span><span class="sxs-lookup"><span data-stu-id="a230c-234">How to: Access Members of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [<span data-ttu-id="a230c-235">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="a230c-235">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="a230c-236">寬鬆委派轉換</span><span class="sxs-lookup"><span data-stu-id="a230c-236">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="a230c-237">Office 方案中的晚期繫結</span><span class="sxs-lookup"><span data-stu-id="a230c-237">Late Binding in Office Solutions</span></span>](https://msdn.microsoft.com/library/3xxe951d)  
 [<span data-ttu-id="a230c-238">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="a230c-238">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="a230c-239">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="a230c-239">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
