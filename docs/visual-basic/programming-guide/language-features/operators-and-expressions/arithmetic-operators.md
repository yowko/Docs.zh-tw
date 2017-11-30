---
title: "Visual Basic 的算術運算子"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7fec98c38eebc34a0f84e051dc7c0914f537418f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operators-in-visual-basic"></a><span data-ttu-id="41c46-102">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="41c46-102">Arithmetic Operators in Visual Basic</span></span>
<span data-ttu-id="41c46-103">算術運算子可用來執行許多熟悉的算術運算涉及數值常值、 變數、 其他運算式、 函式和屬性呼叫和常數所代表的計算。</span><span class="sxs-lookup"><span data-stu-id="41c46-103">Arithmetic operators are used to perform many of the familiar arithmetic operations that involve the calculation of numeric values represented by literals, variables, other expressions, function and property calls, and constants.</span></span> <span data-ttu-id="41c46-104">搭配算術運算子也分類為位元移位運算子會在一個運算元的個別位元層級執行動作，並向左或向右移位的位元模式。</span><span class="sxs-lookup"><span data-stu-id="41c46-104">Also classified with arithmetic operators are the bit-shift operators, which act at the level of the individual bits of the operands and shift their bit patterns to the left or right.</span></span>  
  
## <a name="arithmetic-operations"></a><span data-ttu-id="41c46-105">算術運算</span><span class="sxs-lookup"><span data-stu-id="41c46-105">Arithmetic Operations</span></span>  
 <span data-ttu-id="41c46-106">您可以搭配運算式中加入兩個值[+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)，或從另一個具有減去[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，如下列範例會示範。</span><span class="sxs-lookup"><span data-stu-id="41c46-106">You can add two values in an expression together with the [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md), or subtract one from another with the [- Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 <span data-ttu-id="41c46-107">也會使用否定[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，但只有一個運算元，如下列範例示範。</span><span class="sxs-lookup"><span data-stu-id="41c46-107">Negation also uses the [- Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), but with only one operand, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 <span data-ttu-id="41c46-108">使用乘法和除法[* 運算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)和[/ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)分別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="41c46-108">Multiplication and division use the [* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) and [/ Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectively, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 <span data-ttu-id="41c46-109">會使用指數[^ 運算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="41c46-109">Exponentiation uses the [^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 <span data-ttu-id="41c46-110">整數除法場所使用[\ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="41c46-110">Integer division is carried out using the [\ Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span> <span data-ttu-id="41c46-111">整數除法傳回商數，也就是代表次數的整數除數分成數個而不考慮任何餘數被除數。</span><span class="sxs-lookup"><span data-stu-id="41c46-111">Integer division returns the quotient, that is, the integer that represents the number of times the divisor can divide into the dividend without consideration of any remainder.</span></span> <span data-ttu-id="41c46-112">被除數和除數必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，和`ULong`) 為此運算子。</span><span class="sxs-lookup"><span data-stu-id="41c46-112">Both the divisor and the dividend must be integral types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, and `ULong`) for this operator.</span></span> <span data-ttu-id="41c46-113">所有其他類型必須先轉換成整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="41c46-113">All other types must be converted to an integral type first.</span></span> <span data-ttu-id="41c46-114">下列範例會示範整數除法。</span><span class="sxs-lookup"><span data-stu-id="41c46-114">The following example demonstrates integer division.</span></span>  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 <span data-ttu-id="41c46-115">使用執行算術模數[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="41c46-115">Modulus arithmetic is performed using the [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="41c46-116">這個運算子傳回餘數對被除數除以除數之後的整數類資料的次數。</span><span class="sxs-lookup"><span data-stu-id="41c46-116">This operator returns the remainder after dividing the divisor into the dividend an integral number of times.</span></span> <span data-ttu-id="41c46-117">如果除數與被除數都是整數類資料類型，傳回的值是整數。</span><span class="sxs-lookup"><span data-stu-id="41c46-117">If both divisor and dividend are integral types, the returned value is integral.</span></span> <span data-ttu-id="41c46-118">如果除數與被除數浮點型別，傳回的值也是浮點數。</span><span class="sxs-lookup"><span data-stu-id="41c46-118">If divisor and dividend are floating-point types, the returned value is also floating-point.</span></span> <span data-ttu-id="41c46-119">下列範例將示範這個行為。</span><span class="sxs-lookup"><span data-stu-id="41c46-119">The following example demonstrates this behavior.</span></span>  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a><span data-ttu-id="41c46-120">嘗試的除以零</span><span class="sxs-lookup"><span data-stu-id="41c46-120">Attempted Division by Zero</span></span>  
 <span data-ttu-id="41c46-121">除數為零會有不同的結果，根據相關的資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="41c46-121">Division by zero has different results depending on the data types involved.</span></span> <span data-ttu-id="41c46-122">整數類資料劃分 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`)、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]會擲回<xref:System.DivideByZeroException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41c46-122">In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="41c46-123">在除法運算`Decimal`或`Single`資料型別，[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]也會擲回<xref:System.DivideByZeroException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41c46-123">In division operations on the `Decimal` or `Single` data type, the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] also throws a <xref:System.DivideByZeroException> exception.</span></span>  
  
 <span data-ttu-id="41c46-124">涉及浮點劃分`Double`資料型別，擲回任何例外狀況，且結果為該類別的成員代表<xref:System.Double.NaN>， <xref:System.Double.PositiveInfinity>，或<xref:System.Double.NegativeInfinity>，端視被除數。</span><span class="sxs-lookup"><span data-stu-id="41c46-124">In floating-point divisions involving the `Double` data type, no exception is thrown, and the result is the class member representing <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, or <xref:System.Double.NegativeInfinity>, depending on the dividend.</span></span> <span data-ttu-id="41c46-125">下表摘要說明不同的結果的嘗試將`Double`除以零的值。</span><span class="sxs-lookup"><span data-stu-id="41c46-125">The following table summarizes the various results of attempting to divide a `Double` value by zero.</span></span>  
  
|<span data-ttu-id="41c46-126">被除數資料類型</span><span class="sxs-lookup"><span data-stu-id="41c46-126">Dividend data type</span></span>|<span data-ttu-id="41c46-127">除數資料型別</span><span class="sxs-lookup"><span data-stu-id="41c46-127">Divisor data type</span></span>|<span data-ttu-id="41c46-128">被除數的值</span><span class="sxs-lookup"><span data-stu-id="41c46-128">Dividend value</span></span>|<span data-ttu-id="41c46-129">結果</span><span class="sxs-lookup"><span data-stu-id="41c46-129">Result</span></span>|  
|---|---|---|---|  
|`Double`|`Double`|<span data-ttu-id="41c46-130">0</span><span class="sxs-lookup"><span data-stu-id="41c46-130">0</span></span>|<span data-ttu-id="41c46-131"><xref:System.Double.NaN>（不是以數學方式定義數字）</span><span class="sxs-lookup"><span data-stu-id="41c46-131"><xref:System.Double.NaN> (not a mathematically defined number)</span></span>|  
|`Double`|`Double`|<span data-ttu-id="41c46-132">> 0</span><span class="sxs-lookup"><span data-stu-id="41c46-132">> 0</span></span>|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|<span data-ttu-id="41c46-133">\< 0</span><span class="sxs-lookup"><span data-stu-id="41c46-133">\< 0</span></span>|<xref:System.Double.NegativeInfinity>|  
  
 <span data-ttu-id="41c46-134">當您攔截<xref:System.DivideByZeroException>例外狀況，您可以使用其成員可協助您處理它。</span><span class="sxs-lookup"><span data-stu-id="41c46-134">When you catch a <xref:System.DivideByZeroException> exception, you can use its members to help you handle it.</span></span> <span data-ttu-id="41c46-135">例如，<xref:System.Exception.Message%2A>屬性會保留例外狀況的訊息文字。</span><span class="sxs-lookup"><span data-stu-id="41c46-135">For example, the <xref:System.Exception.Message%2A> property holds the message text for the exception.</span></span> <span data-ttu-id="41c46-136">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="41c46-136">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="bit-shift-operations"></a><span data-ttu-id="41c46-137">位元移位作業</span><span class="sxs-lookup"><span data-stu-id="41c46-137">Bit-Shift Operations</span></span>  
 <span data-ttu-id="41c46-138">位元移位作業位元模式上執行算術的位移。</span><span class="sxs-lookup"><span data-stu-id="41c46-138">A bit-shift operation performs an arithmetic shift on a bit pattern.</span></span> <span data-ttu-id="41c46-139">模式包含在左邊的運算元中，而右運算元指定的位置模式移位的數目。</span><span class="sxs-lookup"><span data-stu-id="41c46-139">The pattern is contained in the operand on the left, while the operand on the right specifies the number of positions to shift the pattern.</span></span> <span data-ttu-id="41c46-140">您可以將模式移位至右側[>> 運算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)或左側[<< 運算子](../../../../visual-basic/language-reference/operators/left-shift-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="41c46-140">You can shift the pattern to the right with the [>> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) or to the left with the [<< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md).</span></span>  
  
 <span data-ttu-id="41c46-141">模式運算元的資料類型必須是`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`。</span><span class="sxs-lookup"><span data-stu-id="41c46-141">The data type of the pattern operand must be `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`.</span></span> <span data-ttu-id="41c46-142">移位量運算元的資料類型必須是`Integer`或必須擴展為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="41c46-142">The data type of the shift amount operand must be `Integer` or must widen to `Integer`.</span></span>  
  
 <span data-ttu-id="41c46-143">算術排班不是循環，這表示移出結果的一個 end 的位元會重新引入的另一端。</span><span class="sxs-lookup"><span data-stu-id="41c46-143">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="41c46-144">移位空出的位元位置設定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="41c46-144">The bit positions vacated by a shift are set as follows:</span></span>  
  
-   <span data-ttu-id="41c46-145">0 代表算術左移位</span><span class="sxs-lookup"><span data-stu-id="41c46-145">0 for an arithmetic left shift</span></span>  
  
-   <span data-ttu-id="41c46-146">0 為正數的算術右移位的</span><span class="sxs-lookup"><span data-stu-id="41c46-146">0 for an arithmetic right shift of a positive number</span></span>  
  
-   <span data-ttu-id="41c46-147">0 代表不帶正負號的資料類型的算術右移位 (`Byte`， `UShort`， `UInteger`， `ULong`)</span><span class="sxs-lookup"><span data-stu-id="41c46-147">0 for an arithmetic right shift of an unsigned data type (`Byte`, `UShort`, `UInteger`, `ULong`)</span></span>  
  
-   <span data-ttu-id="41c46-148">1 是負數值的算術右移位 (`SByte`， `Short`， `Integer`，或`Long`)</span><span class="sxs-lookup"><span data-stu-id="41c46-148">1 for an arithmetic right shift of a negative number (`SByte`, `Short`, `Integer`, or `Long`)</span></span>  
  
 <span data-ttu-id="41c46-149">下列範例會轉移`Integer`值 left 和 right。</span><span class="sxs-lookup"><span data-stu-id="41c46-149">The following example shifts an `Integer` value both left and right.</span></span>  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 <span data-ttu-id="41c46-150">算術移位不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="41c46-150">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="41c46-151">位元運算</span><span class="sxs-lookup"><span data-stu-id="41c46-151">Bitwise Operations</span></span>  
 <span data-ttu-id="41c46-152">邏輯運算子，除了`Not`， `Or`， `And`，和`Xor`也執行位元的算術運算，使用數字值時。</span><span class="sxs-lookup"><span data-stu-id="41c46-152">In addition to being logical operators, `Not`, `Or`, `And`, and `Xor` also perform bitwise arithmetic when used on numeric values.</span></span> <span data-ttu-id="41c46-153">如需詳細資訊，請參閱 < 位元作業 >[邏輯和位元 Visual Basic 中的運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="41c46-153">For more information, see "Bitwise Operations" in [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).</span></span>  
  
## <a name="type-safety"></a><span data-ttu-id="41c46-154">型別安全</span><span class="sxs-lookup"><span data-stu-id="41c46-154">Type Safety</span></span>  
 <span data-ttu-id="41c46-155">運算元通常應該是相同的型別。</span><span class="sxs-lookup"><span data-stu-id="41c46-155">Operands should normally be of the same type.</span></span> <span data-ttu-id="41c46-156">例如，如果您要加入`Integer`變數時，您應該將它加入另一個`Integer`變數，而且您應該將結果指派給類型的變數`Integer`以及。</span><span class="sxs-lookup"><span data-stu-id="41c46-156">For example, if you are doing addition with an `Integer` variable, you should add it to another `Integer` variable, and you should assign the result to a variable of type `Integer` as well.</span></span>  
  
 <span data-ttu-id="41c46-157">一種方式以確保好的型別安全程式碼撰寫的作法是使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="41c46-157">One way to ensure good type-safe coding practice is to use the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="41c46-158">如果您設定`Option Strict On`，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]會自動執行*型別安全*轉換。</span><span class="sxs-lookup"><span data-stu-id="41c46-158">If you set `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically performs *type-safe* conversions.</span></span> <span data-ttu-id="41c46-159">例如，如果您嘗試新增`Integer`變數設為`Double`變數和指派值`Double`變數時，作業正常執行，因為`Integer`值可以轉換成`Double`而不會遺失資料。</span><span class="sxs-lookup"><span data-stu-id="41c46-159">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to a `Double` variable, the operation proceeds normally, because an `Integer` value can be converted to `Double` without loss of data.</span></span> <span data-ttu-id="41c46-160">類型安全的轉換，相反地，會造成編譯器錯誤與`Option Strict On`。</span><span class="sxs-lookup"><span data-stu-id="41c46-160">Type-unsafe conversions, on the other hand, cause a compiler error with `Option Strict On`.</span></span> <span data-ttu-id="41c46-161">比方說，如果您嘗試新增`Integer`變數設為`Double`變數和指派值`Integer`變數，則編譯器會產生錯誤，因為`Double`變數無法以隱含方式轉換為類型`Integer`。</span><span class="sxs-lookup"><span data-stu-id="41c46-161">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to an `Integer` variable, a compiler error results, because a `Double` variable cannot be implicitly converted to type `Integer`.</span></span>  
  
 <span data-ttu-id="41c46-162">如果您設定`Option Strict Off`，不過[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]允許隱含的縮小轉換，才能進行應用程式，雖然它們可能會導致非預期的資料或精確度遺失。</span><span class="sxs-lookup"><span data-stu-id="41c46-162">If you set `Option Strict Off`, however, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] allows implicit narrowing conversions to take place, although they can result in the unexpected loss of data or precision.</span></span> <span data-ttu-id="41c46-163">基於這個理由，我們建議您改用`Option Strict On`寫入實際執行程式碼時。</span><span class="sxs-lookup"><span data-stu-id="41c46-163">For this reason, we recommend that you use `Option Strict On` when writing production code.</span></span> <span data-ttu-id="41c46-164">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="41c46-164">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c46-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41c46-165">See Also</span></span>  
 [<span data-ttu-id="41c46-166">算術運算子</span><span class="sxs-lookup"><span data-stu-id="41c46-166">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="41c46-167">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="41c46-167">Bit Shift Operators</span></span>](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="41c46-168">在 Visual Basic 中的比較運算子</span><span class="sxs-lookup"><span data-stu-id="41c46-168">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="41c46-169">在 Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="41c46-169">Concatenation Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [<span data-ttu-id="41c46-170">在 Visual Basic 中的邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="41c46-170">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="41c46-171">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="41c46-171">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
