---
title: "Option Strict 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Strict
- vb.OptionStrict
dev_langs:
- VB
helpviewer_keywords:
- Strict keyword
- Option Strict statement
- conversions, implicit
- late binding
- implicit conversions
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
caps.latest.revision: 49
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 055565082757318334e89410d12ed7067e5814cb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="option-strict-statement"></a><span data-ttu-id="eed19-102">Long</span><span class="sxs-lookup"><span data-stu-id="eed19-102">Option Strict Statement</span></span>
<span data-ttu-id="eed19-103">隱含資料型別將轉換限制為只有擴展轉換不允許晚期繫結，不允許隱含型別，而產生的`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="eed19-103">Restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed19-104">語法</span><span class="sxs-lookup"><span data-stu-id="eed19-104">Syntax</span></span>  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="eed19-105">組件</span><span class="sxs-lookup"><span data-stu-id="eed19-105">Parts</span></span>  
  
|<span data-ttu-id="eed19-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="eed19-106">Term</span></span>|<span data-ttu-id="eed19-107">定義</span><span class="sxs-lookup"><span data-stu-id="eed19-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="eed19-108">選擇項。</span><span class="sxs-lookup"><span data-stu-id="eed19-108">Optional.</span></span> <span data-ttu-id="eed19-109">可讓`Option Strict`檢查。</span><span class="sxs-lookup"><span data-stu-id="eed19-109">Enables `Option Strict` checking.</span></span>|  
|`Off`|<span data-ttu-id="eed19-110">選擇項。</span><span class="sxs-lookup"><span data-stu-id="eed19-110">Optional.</span></span> <span data-ttu-id="eed19-111">停用`Option Strict`檢查。</span><span class="sxs-lookup"><span data-stu-id="eed19-111">Disables `Option Strict` checking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eed19-112">備註</span><span class="sxs-lookup"><span data-stu-id="eed19-112">Remarks</span></span>  
 <span data-ttu-id="eed19-113">當`Option Strict On`或`Option Strict`會出現在檔案中，在下列情況會造成編譯時期錯誤︰</span><span class="sxs-lookup"><span data-stu-id="eed19-113">When `Option Strict On` or `Option Strict` appears in a file, the following conditions cause a compile-time error:</span></span>  
  
-   <span data-ttu-id="eed19-114">隱含的縮小轉換</span><span class="sxs-lookup"><span data-stu-id="eed19-114">Implicit narrowing conversions</span></span>  
  
-   <span data-ttu-id="eed19-115">晚期繫結</span><span class="sxs-lookup"><span data-stu-id="eed19-115">Late binding</span></span>  
  
-   <span data-ttu-id="eed19-116">隱含型別，而產生的`Object`類型</span><span class="sxs-lookup"><span data-stu-id="eed19-116">Implicit typing that results in an `Object` type</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eed19-117">您可以設定的警告組態中[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，有三種設定對應至三個條件會造成編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-117">In the warning configurations that you can set on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic), there are three settings that correspond to the three conditions that cause a compile-time error.</span></span> <span data-ttu-id="eed19-118">如需如何使用這些設定資訊，請參閱[在 IDE 中設定警告組態](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)稍後在本主題中。</span><span class="sxs-lookup"><span data-stu-id="eed19-118">For information about how to use these settings, see [To set warning configurations in the IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) later in this topic.</span></span>  
  
 <span data-ttu-id="eed19-119">`Option Strict Off`陳述式關閉 錯誤和警告檢查所有的三個條件，即使相關聯的 IDE 設定指定要開啟這些錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="eed19-119">The `Option Strict Off` statement turns off error and warning checking for all three conditions, even if the associated IDE settings specify to turn on these errors or warnings.</span></span> <span data-ttu-id="eed19-120">`Option Strict On`陳述式會開啟錯誤和警告檢查所有的三個條件，即使相關聯的 IDE 設定指定要關閉這些錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="eed19-120">The `Option Strict On` statement turns on error and warning checking for all three conditions, even if the associated IDE settings specify to turn off these errors or warnings.</span></span>  
  
 <span data-ttu-id="eed19-121">如果使用`Option Strict`陳述式必須出現在檔案中任何其他程式碼陳述式之前。</span><span class="sxs-lookup"><span data-stu-id="eed19-121">If used, the `Option Strict` statement must appear before any other code statements in a file.</span></span>  
  
 <span data-ttu-id="eed19-122">當您設定`Option Strict`至`On`，Visual Basic 會檢查資料型別會指定針對所有的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="eed19-122">When you set `Option Strict` to `On`, Visual Basic checks that data types are specified for all programming elements.</span></span> <span data-ttu-id="eed19-123">資料類型可以明確地指定，或使用區域型別推斷來指定。</span><span class="sxs-lookup"><span data-stu-id="eed19-123">Data types can be specified explicitly, or specified by using local type inference.</span></span> <span data-ttu-id="eed19-124">指定的所有程式設計項目資料型別建議，原因如下︰</span><span class="sxs-lookup"><span data-stu-id="eed19-124">Specifying data types for all your programming elements is recommended, for the following reasons:</span></span>  
  
-   <span data-ttu-id="eed19-125">它可讓您的變數和參數的 IntelliSense 支援。</span><span class="sxs-lookup"><span data-stu-id="eed19-125">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="eed19-126">這可讓您查看其屬性和其他成員，當您輸入程式碼。</span><span class="sxs-lookup"><span data-stu-id="eed19-126">This enables you to see their properties and other members as you type code.</span></span>  
  
-   <span data-ttu-id="eed19-127">它可讓編譯器執行類型檢查。</span><span class="sxs-lookup"><span data-stu-id="eed19-127">It enables the compiler to perform type checking.</span></span> <span data-ttu-id="eed19-128">型別檢查，可協助您找出可以在執行階段失敗，因為型別轉換錯誤的陳述式。</span><span class="sxs-lookup"><span data-stu-id="eed19-128">Type checking helps you find statements that can fail at run time because of type conversion errors.</span></span> <span data-ttu-id="eed19-129">它也會識別不支援這些方法的物件上方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="eed19-129">It also identifies calls to methods on objects that do not support those methods.</span></span>  
  
-   <span data-ttu-id="eed19-130">它能加速程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="eed19-130">It speeds up the execution of code.</span></span> <span data-ttu-id="eed19-131">一個理由是，如果您未指定資料類型的程式設計項目，則 Visual Basic 編譯器將其指派`Object`型別。</span><span class="sxs-lookup"><span data-stu-id="eed19-131">One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type.</span></span> <span data-ttu-id="eed19-132">可能需要編譯的程式碼之間來回轉換`Object`和其他資料類型，這會降低效能。</span><span class="sxs-lookup"><span data-stu-id="eed19-132">Compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="implicit-narrowing-conversion-errors"></a><span data-ttu-id="eed19-133">隱含的縮小轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="eed19-133">Implicit Narrowing Conversion Errors</span></span>  
 <span data-ttu-id="eed19-134">縮小轉換的隱含資料類型轉換時，就會發生隱含的縮小轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-134">Implicit narrowing conversion errors occur when there is an implicit data type conversion that is a narrowing conversion.</span></span>  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="eed19-135">可以將許多資料型別轉換成其他資料型別。</span><span class="sxs-lookup"><span data-stu-id="eed19-135"> can convert many data types to other data types.</span></span> <span data-ttu-id="eed19-136">一種資料類型的值轉換為具有較少的有效位數或容量較小的資料類型時，可能發生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="eed19-136">Data loss can occur when the value of one data type is converted to a data type that has less precision or a smaller capacity.</span></span> <span data-ttu-id="eed19-137">如果縮小轉換失敗，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-137">A run-time error occurs if such a narrowing conversion fails.</span></span> <span data-ttu-id="eed19-138">`Option Strict`可確保這些縮小轉換的編譯時期通知，好讓您可以避免它們。</span><span class="sxs-lookup"><span data-stu-id="eed19-138">`Option Strict` ensures compile-time notification of these narrowing conversions so that you can avoid them.</span></span> <span data-ttu-id="eed19-139">如需詳細資訊，請參閱[隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)和[擴大和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="eed19-139">For more information, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) and [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="eed19-140">可能會導致錯誤的轉換會在運算式中包含所發生的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="eed19-140">Conversions that can cause errors include implicit conversions that occur in expressions.</span></span> <span data-ttu-id="eed19-141">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="eed19-141">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="eed19-142">+ 運算子</span><span class="sxs-lookup"><span data-stu-id="eed19-142">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [<span data-ttu-id="eed19-143">+= 運算子</span><span class="sxs-lookup"><span data-stu-id="eed19-143">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [<span data-ttu-id="eed19-144">\ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eed19-144">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [<span data-ttu-id="eed19-145">/ = 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eed19-145">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [<span data-ttu-id="eed19-146">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="eed19-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 <span data-ttu-id="eed19-147">當您使用串連字串[i 運算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)，所有轉換成字串會被都視為擴展。</span><span class="sxs-lookup"><span data-stu-id="eed19-147">When you concatenate strings by using the [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), all conversions to the strings are considered to be widening.</span></span> <span data-ttu-id="eed19-148">因此這些轉換不會產生隱含的縮小轉換錯誤，即使`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="eed19-148">So these conversions do not generate an implicit narrowing conversion error, even if `Option Strict` is on.</span></span>  
  
 <span data-ttu-id="eed19-149">如果縮小轉換，當您呼叫具有對應的參數與不同的資料類型的引數的方法時，會導致編譯時期錯誤`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="eed19-149">When you call a method that has an argument that has a data type different from the corresponding parameter, a narrowing conversion causes a compile-time error if `Option Strict` is on.</span></span> <span data-ttu-id="eed19-150">您可以使用擴展轉換或明確的轉換，以避免產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-150">You can avoid the compile-time error by using a widening conversion or an explicit conversion.</span></span>  
  
 <span data-ttu-id="eed19-151">隱含的縮小轉換錯誤會隱藏在編譯階段進行中的項目轉換`For Each…Next`迴圈控制變數的集合。</span><span class="sxs-lookup"><span data-stu-id="eed19-151">Implicit narrowing conversion errors are suppressed at compile-time for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="eed19-152">發生這種情況即使`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="eed19-152">This occurs even if `Option Strict` is on.</span></span> <span data-ttu-id="eed19-153">如需詳細資訊，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eed19-153">For more information, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="late-binding-errors"></a><span data-ttu-id="eed19-154">晚期繫結錯誤</span><span class="sxs-lookup"><span data-stu-id="eed19-154">Late Binding Errors</span></span>  
 <span data-ttu-id="eed19-155">物件晚期繫結指派至屬性或方法的宣告類型的變數時`Object`。</span><span class="sxs-lookup"><span data-stu-id="eed19-155">An object is late bound when it is assigned to a property or method of a variable that is declared to be of type `Object`.</span></span> <span data-ttu-id="eed19-156">如需詳細資訊，請參閱[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。</span><span class="sxs-lookup"><span data-stu-id="eed19-156">For more information, see [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>  
  
## <a name="implicit-object-type-errors"></a><span data-ttu-id="eed19-157">隱含的物件類型的錯誤</span><span class="sxs-lookup"><span data-stu-id="eed19-157">Implicit Object Type Errors</span></span>  
 <span data-ttu-id="eed19-158">隱含的物件類型的錯誤發生時適當的型別無法推斷為宣告的變數，因此一種`Object`會推斷而來。</span><span class="sxs-lookup"><span data-stu-id="eed19-158">Implicit object type errors occur when an appropriate type cannot be inferred for a declared variable, so a type of `Object` is inferred.</span></span> <span data-ttu-id="eed19-159">這主要是發生在您使用`Dim`陳述式來宣告變數，而不需使用`As`子句和`Option Infer`已關閉。</span><span class="sxs-lookup"><span data-stu-id="eed19-159">This primarily occurs when you use a `Dim` statement to declare a variable without using an `As` clause, and `Option Infer` is off.</span></span> <span data-ttu-id="eed19-160">如需詳細資訊，請參閱[Option Infer 陳述式](../../../visual-basic/language-reference/statements/option-infer-statement.md)和[Visual Basic 語言規格](../../../visual-basic/reference/language-specification.md)。</span><span class="sxs-lookup"><span data-stu-id="eed19-160">For more information, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md).</span></span>  
  
 <span data-ttu-id="eed19-161">方法參數`As`子句是選擇性的如果`Option Strict`已關閉。</span><span class="sxs-lookup"><span data-stu-id="eed19-161">For method parameters, the `As` clause is optional if `Option Strict` is off.</span></span> <span data-ttu-id="eed19-162">不過，如果任何一個參數使用`As`子句，它們都必須使用它。</span><span class="sxs-lookup"><span data-stu-id="eed19-162">However, if any one parameter uses an `As` clause, they all must use it.</span></span> <span data-ttu-id="eed19-163">如果`Option Strict`，`As`子句是針對每個參數定義必要的。</span><span class="sxs-lookup"><span data-stu-id="eed19-163">If `Option Strict` is on, the `As` clause is required for every parameter definition.</span></span>  
  
 <span data-ttu-id="eed19-164">如果您宣告變數，而不需使用`As`子句，將它設定為`Nothing`，變數有一種`Object`。</span><span class="sxs-lookup"><span data-stu-id="eed19-164">If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`.</span></span> <span data-ttu-id="eed19-165">在此情況下發生編譯時期錯誤時`Option Strict`上和`Option Infer`上。</span><span class="sxs-lookup"><span data-stu-id="eed19-165">No compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is on.</span></span> <span data-ttu-id="eed19-166">這個範例是`Dim something = Nothing`。</span><span class="sxs-lookup"><span data-stu-id="eed19-166">An example of this is `Dim something = Nothing`.</span></span>  
  
### <a name="default-data-types-and-values"></a><span data-ttu-id="eed19-167">預設資料類型和值</span><span class="sxs-lookup"><span data-stu-id="eed19-167">Default Data Types and Values</span></span>  
 <span data-ttu-id="eed19-168">下表描述的指定資料類型和初始設定式中的各種組合結果[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eed19-168">The following table describes the results of various combinations of specifying the data type and initializer in a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
|<span data-ttu-id="eed19-169">指定了資料類型？</span><span class="sxs-lookup"><span data-stu-id="eed19-169">Data type specified?</span></span>|<span data-ttu-id="eed19-170">指定了初始設定式？</span><span class="sxs-lookup"><span data-stu-id="eed19-170">Initializer specified?</span></span>|<span data-ttu-id="eed19-171">範例</span><span class="sxs-lookup"><span data-stu-id="eed19-171">Example</span></span>|<span data-ttu-id="eed19-172">結果</span><span class="sxs-lookup"><span data-stu-id="eed19-172">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="eed19-173">否</span><span class="sxs-lookup"><span data-stu-id="eed19-173">No</span></span>|<span data-ttu-id="eed19-174">否</span><span class="sxs-lookup"><span data-stu-id="eed19-174">No</span></span>|`Dim qty`|<span data-ttu-id="eed19-175">如果 `Option Strict` 已關閉 (預設值)，此變數會設定為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="eed19-175">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="eed19-176">如果 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-176">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="eed19-177">否</span><span class="sxs-lookup"><span data-stu-id="eed19-177">No</span></span>|<span data-ttu-id="eed19-178">是</span><span class="sxs-lookup"><span data-stu-id="eed19-178">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="eed19-179">如果 `Option Infer` 已開啟 (預設值)，此變數會採用初始設定式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="eed19-179">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="eed19-180">請參閱[區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="eed19-180">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="eed19-181">如果 `Option Infer` 已關閉，且 `Option Strict` 也已關閉，此變數會採用 `Object` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="eed19-181">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="eed19-182">如果 `Option Infer` 已關閉，但是 `Option Strict` 已開啟，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-182">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="eed19-183">是</span><span class="sxs-lookup"><span data-stu-id="eed19-183">Yes</span></span>|<span data-ttu-id="eed19-184">否</span><span class="sxs-lookup"><span data-stu-id="eed19-184">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="eed19-185">變數會初始化為資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="eed19-185">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="eed19-186">如需詳細資訊，請參閱[Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eed19-186">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="eed19-187">是</span><span class="sxs-lookup"><span data-stu-id="eed19-187">Yes</span></span>|<span data-ttu-id="eed19-188">是</span><span class="sxs-lookup"><span data-stu-id="eed19-188">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="eed19-189">如果初始設定式的資料類型無法轉換成指定的資料類型，就會發生編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-189">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a><span data-ttu-id="eed19-190">當 Option Strict 陳述式不存在</span><span class="sxs-lookup"><span data-stu-id="eed19-190">When an Option Strict Statement Is Not Present</span></span>  
 <span data-ttu-id="eed19-191">如果原始程式碼不包含`Option Strict`陳述式， **Option strict**上設定[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)用。</span><span class="sxs-lookup"><span data-stu-id="eed19-191">If the source code does not contain an `Option Strict` statement, the **Option strict** setting on the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="eed19-192">**編譯頁面**有提供產生錯誤之條件的額外控制的設定。</span><span class="sxs-lookup"><span data-stu-id="eed19-192">The **Compile Page** has settings that provide additional control over the conditions that generate an error.</span></span>  
  
 <span data-ttu-id="eed19-193">如果您使用命令列編譯器，您可以使用[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項以指定的設定`Option Strict`。</span><span class="sxs-lookup"><span data-stu-id="eed19-193">If you are using the command-line compiler, you can use the [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option to specify a setting for `Option Strict`.</span></span>  
  
### <a name="to-set-option-strict-in-the-ide"></a><span data-ttu-id="eed19-194">若要在 IDE 中設定 Option Strict</span><span class="sxs-lookup"><span data-stu-id="eed19-194">To set Option Strict in the IDE</span></span>  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
1.  <span data-ttu-id="eed19-195">在**方案總管 中**，選取專案。</span><span class="sxs-lookup"><span data-stu-id="eed19-195">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="eed19-196">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="eed19-196">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="eed19-197">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="eed19-197">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="eed19-198">在**編譯**索引標籤上，在設定的值**Option Strict**方塊。</span><span class="sxs-lookup"><span data-stu-id="eed19-198">On the **Compile** tab, set the value in the **Option Strict** box.</span></span>  
  
###  <span data-ttu-id="eed19-199"><a name="conditions"></a>在 IDE 中設定警告組態</span><span class="sxs-lookup"><span data-stu-id="eed19-199"><a name="conditions"></a> To set warning configurations in the IDE</span></span>  
 <span data-ttu-id="eed19-200">當您使用[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)而不是`Option Strict`陳述式中，您有其他控制項，會產生錯誤的狀況。</span><span class="sxs-lookup"><span data-stu-id="eed19-200">When you use the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) instead of an `Option Strict` statement, you have additional control over the conditions that generate errors.</span></span> <span data-ttu-id="eed19-201">**警告組態**區段**編譯頁面**已設定會對應到三個條件會造成編譯時期錯誤時`Option Strict`上。</span><span class="sxs-lookup"><span data-stu-id="eed19-201">The **Warning configurations** section of the **Compile Page** has settings that correspond to the three conditions that cause a compile-time error when `Option Strict` is on.</span></span> <span data-ttu-id="eed19-202">以下是這些設定︰</span><span class="sxs-lookup"><span data-stu-id="eed19-202">Following are these settings:</span></span>  
  
-   <span data-ttu-id="eed19-203">**隱含轉換**</span><span class="sxs-lookup"><span data-stu-id="eed19-203">**Implicit conversion**</span></span>  
  
-   <span data-ttu-id="eed19-204">**晚期繫結。呼叫可能會在執行階段失敗**</span><span class="sxs-lookup"><span data-stu-id="eed19-204">**Late binding; call could fail at run time**</span></span>  
  
-   <span data-ttu-id="eed19-205">**隱含型別。假設是物件**</span><span class="sxs-lookup"><span data-stu-id="eed19-205">**Implicit type; object assumed**</span></span>  
  
 <span data-ttu-id="eed19-206">當您設定**Option Strict**至**上**，這三個以上的警告組態設定會設定為**錯誤**。</span><span class="sxs-lookup"><span data-stu-id="eed19-206">When you set **Option Strict** to **On**, all three of these warning configuration settings are set to **Error**.</span></span> <span data-ttu-id="eed19-207">當您設定**Option Strict**至**關閉**，所有三項設定會設定為**無**。</span><span class="sxs-lookup"><span data-stu-id="eed19-207">When you set **Option Strict** to **Off**, all three settings are set to **None**.</span></span>  
  
 <span data-ttu-id="eed19-208">您可以個別變更每個警告組態設定**無**，**警告**，或**錯誤**。</span><span class="sxs-lookup"><span data-stu-id="eed19-208">You can individually change each warning configuration setting to **None**, **Warning**, or **Error**.</span></span> <span data-ttu-id="eed19-209">如果所有三個警告組態設定會設定為**錯誤**，`On`會出現在`Option strict`方塊。</span><span class="sxs-lookup"><span data-stu-id="eed19-209">If all three warning configuration settings are set to **Error**, `On` appears in the `Option strict` box.</span></span> <span data-ttu-id="eed19-210">如果這三個設為**無**，`Off`出現在此方塊。</span><span class="sxs-lookup"><span data-stu-id="eed19-210">If all three are set to **None**, `Off` appears in this box.</span></span> <span data-ttu-id="eed19-211">這些設定的任何其他組合**（自訂）**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="eed19-211">For any other combination of these settings, **(custom)** appears.</span></span>  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a><span data-ttu-id="eed19-212">若要設定新專案的 Option Strict 預設設定</span><span class="sxs-lookup"><span data-stu-id="eed19-212">To set the Option Strict default setting for new projects</span></span>  
 <span data-ttu-id="eed19-213">當您建立專案， **Option Strict**上設定**編譯** 索引標籤設為**Option Strict**中設定**選項**對話方塊。</span><span class="sxs-lookup"><span data-stu-id="eed19-213">When you create a project, the **Option Strict** setting on the **Compile** tab is set to the **Option Strict** setting in the **Options** dialog box.</span></span>  
  
 <span data-ttu-id="eed19-214">若要設定`Option Strict`在這個對話方塊中，在**工具** 功能表上，按一下**選項**。</span><span class="sxs-lookup"><span data-stu-id="eed19-214">To set `Option Strict` in this dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="eed19-215">在**選項**對話方塊方塊中，展開**專案和方案**，然後按一下  **VB 預設值**。</span><span class="sxs-lookup"><span data-stu-id="eed19-215">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="eed19-216">中的初始預設設定**VB 預設值**是`Off`。</span><span class="sxs-lookup"><span data-stu-id="eed19-216">The initial default setting in **VB Defaults** is `Off`.</span></span>  
  
### <a name="to-set-option-strict-on-the-command-line"></a><span data-ttu-id="eed19-217">若要命令列上設定 Option Strict</span><span class="sxs-lookup"><span data-stu-id="eed19-217">To set Option Strict on the command line</span></span>  
 <span data-ttu-id="eed19-218">包含[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項，在**vbc**命令。</span><span class="sxs-lookup"><span data-stu-id="eed19-218">Include the [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed19-219">範例</span><span class="sxs-lookup"><span data-stu-id="eed19-219">Example</span></span>  
 <span data-ttu-id="eed19-220">下列範例將示範會縮小轉換的隱含型別轉換所造成的編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-220">The following examples demonstrate compile-time errors caused by implicit type conversions that are narrowing conversions.</span></span> <span data-ttu-id="eed19-221">這類錯誤對應於**隱含轉換**條件**編譯頁面**。</span><span class="sxs-lookup"><span data-stu-id="eed19-221">This category of errors corresponds to the **Implicit conversion** condition on the **Compile Page**.</span></span>  
  
 <span data-ttu-id="eed19-222">[!code-vb[VbVbalrStatements #&161;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="eed19-222">[!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed19-223">範例</span><span class="sxs-lookup"><span data-stu-id="eed19-223">Example</span></span>  
 <span data-ttu-id="eed19-224">下列範例將示範造成晚期繫結的編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="eed19-224">The following example demonstrates a compile-time error caused by late binding.</span></span> <span data-ttu-id="eed19-225">這類錯誤對應於**05 繫結; 呼叫無法在執行階段失敗**條件**編譯頁面**。</span><span class="sxs-lookup"><span data-stu-id="eed19-225">This category of errors corresponds to the **Late binding; call could fail at run time** condition on the **Compile Page**.</span></span>  
  
 <span data-ttu-id="eed19-226">[!code-vb[VbVbalrStatements #&162;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="eed19-226">[!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed19-227">範例</span><span class="sxs-lookup"><span data-stu-id="eed19-227">Example</span></span>  
 <span data-ttu-id="eed19-228">下列範例示範的隱含型別宣告的變數所造成的錯誤`Object`。</span><span class="sxs-lookup"><span data-stu-id="eed19-228">The following examples demonstrate errors caused by variables that are declared with an implicit type of `Object`.</span></span> <span data-ttu-id="eed19-229">這類錯誤對應於**隱含型別，假設是物件**條件**編譯頁面**。</span><span class="sxs-lookup"><span data-stu-id="eed19-229">This category of errors corresponds to the **Implicit type; object assumed** condition on the **Compile Page**.</span></span>  
  
 <span data-ttu-id="eed19-230">[!code-vb[VbVbalrStatements #&163;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="eed19-230">[!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="eed19-231">[!code-vb[VbVbalrStatements #&164;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="eed19-231">[!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed19-232">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eed19-232">See Also</span></span>  
 <span data-ttu-id="eed19-233">[擴展和縮小轉換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-233">[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="eed19-234"> [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-234"> [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="eed19-235"> [專案設計工具、編譯頁 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="eed19-235"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="eed19-236"> [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-236"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="eed19-237"> [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-237"> [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="eed19-238"> [如何︰ 存取物件的成員](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-238"> [How to: Access Members of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md) </span></span>  
<span data-ttu-id="eed19-239"> [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-239"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="eed19-240"> [寬鬆的委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-240"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span></span>  
<span data-ttu-id="eed19-241"> [在 Office 方案中的晚期繫結](https://msdn.microsoft.com/library/3xxe951d) </span><span class="sxs-lookup"><span data-stu-id="eed19-241"> [Late Binding in Office Solutions](https://msdn.microsoft.com/library/3xxe951d) </span></span>  
<span data-ttu-id="eed19-242"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span><span class="sxs-lookup"><span data-stu-id="eed19-242"> [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) </span></span>  
<span data-ttu-id="eed19-243"> [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span><span class="sxs-lookup"><span data-stu-id="eed19-243"> [Visual Basic Defaults, Projects, Options Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)</span></span>
