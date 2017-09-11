---
title: "在 Visual Basic 中的算術運算子 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators
- bit-shift operators
- zero, division by zero
- operators [Visual Basic], arithmetic
- division, by zero
- Visual Basic code, operators
- arithmetic operators, about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: 20
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
ms.openlocfilehash: e80e7950abe035efe5294974937589a1af40f17c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="arithmetic-operators-in-visual-basic"></a><span data-ttu-id="23944-102">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="23944-102">Arithmetic Operators in Visual Basic</span></span>
<span data-ttu-id="23944-103">算術運算子用來執行許多熟悉的算術作業涉及的常值、 變數、 其他運算式、 函式和屬性呼叫和常數所代表的數值計算。</span><span class="sxs-lookup"><span data-stu-id="23944-103">Arithmetic operators are used to perform many of the familiar arithmetic operations that involve the calculation of numeric values represented by literals, variables, other expressions, function and property calls, and constants.</span></span> <span data-ttu-id="23944-104">搭配算術運算子也分類為位元移位運算子會在運算元的個別位元的層級執行動作，並向左或向右移位的位元模式。</span><span class="sxs-lookup"><span data-stu-id="23944-104">Also classified with arithmetic operators are the bit-shift operators, which act at the level of the individual bits of the operands and shift their bit patterns to the left or right.</span></span>  
  
## <a name="arithmetic-operations"></a><span data-ttu-id="23944-105">算術運算</span><span class="sxs-lookup"><span data-stu-id="23944-105">Arithmetic Operations</span></span>  
 <span data-ttu-id="23944-106">一起使用的運算式中，您可以加入兩個值[+ 運算子](../../../../visual-basic/language-reference/operators/addition-operator.md)，或從另一個具有減去[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="23944-106">You can add two values in an expression together with the [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md), or subtract one from another with the [- Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), as the following example demonstrates.</span></span>  
  
 <span data-ttu-id="23944-107">[!code-vb[VbVbalrOperators #&57;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-107">[!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]</span></span>  
  
 <span data-ttu-id="23944-108">也會使用負[-運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，但只有一個運算元，如下列範例示範。</span><span class="sxs-lookup"><span data-stu-id="23944-108">Negation also uses the [- Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), but with only one operand, as the following example demonstrates.</span></span>  
  
 <span data-ttu-id="23944-109">[!code-vb[VbVbalrOperators #&58;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-109">[!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]</span></span>  
  
 <span data-ttu-id="23944-110">乘法和除法使用[* 運算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)和[/ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)分別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="23944-110">Multiplication and division use the [* Operator](../../../../visual-basic/language-reference/operators/multiplication-operator.md) and [/ Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respectively, as the following example demonstrates.</span></span>  
  
 <span data-ttu-id="23944-111">[!code-vb[VbVbalrOperators #&59;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-111">[!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]</span></span>  
  
 <span data-ttu-id="23944-112">乘冪使用[^ 運算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="23944-112">Exponentiation uses the [^ Operator](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), as the following example demonstrates.</span></span>  
  
 <span data-ttu-id="23944-113">[!code-vb[VbVbalrOperators #&60;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-113">[!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]</span></span>  
  
 <span data-ttu-id="23944-114">整數除法場所使用[\ 運算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="23944-114">Integer division is carried out using the [\ Operator (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span> <span data-ttu-id="23944-115">整數除法傳回商數，也就是代表次數的整數除數分成數個而不考慮任何餘數被除數。</span><span class="sxs-lookup"><span data-stu-id="23944-115">Integer division returns the quotient, that is, the integer that represents the number of times the divisor can divide into the dividend without consideration of any remainder.</span></span> <span data-ttu-id="23944-116">除數與被除數必須是整數類資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，和`ULong`) 這個運算子。</span><span class="sxs-lookup"><span data-stu-id="23944-116">Both the divisor and the dividend must be integral types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, and `ULong`) for this operator.</span></span> <span data-ttu-id="23944-117">所有其他型別必須先轉換成整數型別。</span><span class="sxs-lookup"><span data-stu-id="23944-117">All other types must be converted to an integral type first.</span></span> <span data-ttu-id="23944-118">下列範例將示範整數除法。</span><span class="sxs-lookup"><span data-stu-id="23944-118">The following example demonstrates integer division.</span></span>  
  
 <span data-ttu-id="23944-119">[!code-vb[VbVbalrOperators #&61;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-119">[!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]</span></span>  
  
 <span data-ttu-id="23944-120">使用執行模數算術[Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="23944-120">Modulus arithmetic is performed using the [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="23944-121">這個運算子會傳回其餘部分對被除數除以除數後的次數的整數。</span><span class="sxs-lookup"><span data-stu-id="23944-121">This operator returns the remainder after dividing the divisor into the dividend an integral number of times.</span></span> <span data-ttu-id="23944-122">如果除數與被除數是整數類資料類型，傳回的值是整數類資料。</span><span class="sxs-lookup"><span data-stu-id="23944-122">If both divisor and dividend are integral types, the returned value is integral.</span></span> <span data-ttu-id="23944-123">如果除數與被除數浮點型別，傳回的值也是浮點數。</span><span class="sxs-lookup"><span data-stu-id="23944-123">If divisor and dividend are floating-point types, the returned value is also floating-point.</span></span> <span data-ttu-id="23944-124">下列範例將示範這個行為。</span><span class="sxs-lookup"><span data-stu-id="23944-124">The following example demonstrates this behavior.</span></span>  
  
 <span data-ttu-id="23944-125">[!code-vb[VbVbalrOperators #&62;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-125">[!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]</span></span>  
  
 <span data-ttu-id="23944-126">[!code-vb[VbVbalrOperators #&63;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-126">[!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]</span></span>  
  
### <a name="attempted-division-by-zero"></a><span data-ttu-id="23944-127">嘗試的除以零</span><span class="sxs-lookup"><span data-stu-id="23944-127">Attempted Division by Zero</span></span>  
 <span data-ttu-id="23944-128">除數為零會有不同的結果，視所涉及的資料類型而定。</span><span class="sxs-lookup"><span data-stu-id="23944-128">Division by zero has different results depending on the data types involved.</span></span> <span data-ttu-id="23944-129">In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] throws a <xref:System.DivideByZeroException> exception.</xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="23944-129">In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="23944-130">在除法運算`Decimal`或`Single`資料型別，[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]也會擲回<xref:System.DivideByZeroException>例外狀況。</xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="23944-130">In division operations on the `Decimal` or `Single` data type, the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] also throws a <xref:System.DivideByZeroException> exception.</span></span>  
  
 <span data-ttu-id="23944-131">涉及浮點劃分`Double`資料型別，擲回任何例外狀況，且結果為類別成員代表<xref:System.Double.NaN>， <xref:System.Double.PositiveInfinity>，或<xref:System.Double.NegativeInfinity>，根據被除數。</xref:System.Double.NegativeInfinity> </xref:System.Double.PositiveInfinity> </xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="23944-131">In floating-point divisions involving the `Double` data type, no exception is thrown, and the result is the class member representing <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, or <xref:System.Double.NegativeInfinity>, depending on the dividend.</span></span> <span data-ttu-id="23944-132">下表摘要說明不同的結果的嘗試將`Double`除以零的值。</span><span class="sxs-lookup"><span data-stu-id="23944-132">The following table summarizes the various results of attempting to divide a `Double` value by zero.</span></span>  
  
|<span data-ttu-id="23944-133">被除數資料型別</span><span class="sxs-lookup"><span data-stu-id="23944-133">Dividend data type</span></span>|<span data-ttu-id="23944-134">除數資料型別</span><span class="sxs-lookup"><span data-stu-id="23944-134">Divisor data type</span></span>|<span data-ttu-id="23944-135">被除數的值</span><span class="sxs-lookup"><span data-stu-id="23944-135">Dividend value</span></span>|<span data-ttu-id="23944-136">結果</span><span class="sxs-lookup"><span data-stu-id="23944-136">Result</span></span>|  
|---|---|---|---|  
|`Double`|`Double`|<span data-ttu-id="23944-137">0</span><span class="sxs-lookup"><span data-stu-id="23944-137">0</span></span>|<span data-ttu-id="23944-138"><xref:System.Double.NaN>（不是以數學方式定義數字）</xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="23944-138"><xref:System.Double.NaN> (not a mathematically defined number)</span></span>|  
|`Double`|`Double`|<span data-ttu-id="23944-139">> 0</span><span class="sxs-lookup"><span data-stu-id="23944-139">> 0</span></span>|<span data-ttu-id="23944-140"><xref:System.Double.PositiveInfinity></xref:System.Double.PositiveInfinity></span><span class="sxs-lookup"><span data-stu-id="23944-140"><xref:System.Double.PositiveInfinity></span></span>|  
|`Double`|`Double`|<span data-ttu-id="23944-141">\< 0</span><span class="sxs-lookup"><span data-stu-id="23944-141">\< 0</span></span>|<span data-ttu-id="23944-142"><xref:System.Double.NegativeInfinity></xref:System.Double.NegativeInfinity></span><span class="sxs-lookup"><span data-stu-id="23944-142"><xref:System.Double.NegativeInfinity></span></span>|  
  
 <span data-ttu-id="23944-143">當您攔截<xref:System.DivideByZeroException>例外狀況，您可以使用其成員，以協助您處理它。</xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="23944-143">When you catch a <xref:System.DivideByZeroException> exception, you can use its members to help you handle it.</span></span> <span data-ttu-id="23944-144">例如，<xref:System.Exception.Message%2A>屬性會保留例外狀況的訊息文字。</xref:System.Exception.Message%2A></span><span class="sxs-lookup"><span data-stu-id="23944-144">For example, the <xref:System.Exception.Message%2A> property holds the message text for the exception.</span></span> <span data-ttu-id="23944-145">如需詳細資訊，請參閱[試...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="23944-145">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="bit-shift-operations"></a><span data-ttu-id="23944-146">位元移位作業</span><span class="sxs-lookup"><span data-stu-id="23944-146">Bit-Shift Operations</span></span>  
 <span data-ttu-id="23944-147">位元移位作業執行算術移位的位元模式上。</span><span class="sxs-lookup"><span data-stu-id="23944-147">A bit-shift operation performs an arithmetic shift on a bit pattern.</span></span> <span data-ttu-id="23944-148">模式中左邊的運算元，而右運算元所指定的位置模式移位的數目。</span><span class="sxs-lookup"><span data-stu-id="23944-148">The pattern is contained in the operand on the left, while the operand on the right specifies the number of positions to shift the pattern.</span></span> <span data-ttu-id="23944-149">您可以將模式移位至右側[>> 運算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)或向左與[ <> </> ](../../../../visual-basic/language-reference/operators/left-shift-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="23944-149">You can shift the pattern to the right with the [>> Operator](../../../../visual-basic/language-reference/operators/right-shift-operator.md) or to the left with the [<< Operator](../../../../visual-basic/language-reference/operators/left-shift-operator.md).</span></span>  
  
 <span data-ttu-id="23944-150">模式運算元的資料型別必須是`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`。</span><span class="sxs-lookup"><span data-stu-id="23944-150">The data type of the pattern operand must be `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`.</span></span> <span data-ttu-id="23944-151">Shift 量運算元的資料型別必須是`Integer`或必須擴展為`Integer`。</span><span class="sxs-lookup"><span data-stu-id="23944-151">The data type of the shift amount operand must be `Integer` or must widen to `Integer`.</span></span>  
  
 <span data-ttu-id="23944-152">算術移位不是循環，這表示移出某一端之結果的位元會重新引入另一端。</span><span class="sxs-lookup"><span data-stu-id="23944-152">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="23944-153">移位空出的位元位置會設定，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="23944-153">The bit positions vacated by a shift are set as follows:</span></span>  
  
-   <span data-ttu-id="23944-154">0 表示算術左移位</span><span class="sxs-lookup"><span data-stu-id="23944-154">0 for an arithmetic left shift</span></span>  
  
-   <span data-ttu-id="23944-155">0 為正數的算術右移位的</span><span class="sxs-lookup"><span data-stu-id="23944-155">0 for an arithmetic right shift of a positive number</span></span>  
  
-   <span data-ttu-id="23944-156">0 代表不帶正負號的資料類型的算術右移位 (`Byte`， `UShort`， `UInteger`， `ULong`)</span><span class="sxs-lookup"><span data-stu-id="23944-156">0 for an arithmetic right shift of an unsigned data type (`Byte`, `UShort`, `UInteger`, `ULong`)</span></span>  
  
-   <span data-ttu-id="23944-157">1 是負數值的算術右移位 (`SByte`， `Short`， `Integer`，或`Long`)</span><span class="sxs-lookup"><span data-stu-id="23944-157">1 for an arithmetic right shift of a negative number (`SByte`, `Short`, `Integer`, or `Long`)</span></span>  
  
 <span data-ttu-id="23944-158">下列範例會轉移`Integer`左和右值。</span><span class="sxs-lookup"><span data-stu-id="23944-158">The following example shifts an `Integer` value both left and right.</span></span>  
  
 <span data-ttu-id="23944-159">[!code-vb[VbVbalrOperators #&64;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="23944-159">[!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]</span></span>  
  
 <span data-ttu-id="23944-160">算術移位不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="23944-160">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="23944-161">位元運算</span><span class="sxs-lookup"><span data-stu-id="23944-161">Bitwise Operations</span></span>  
 <span data-ttu-id="23944-162">除了做為邏輯運算子， `Not`， `Or`， `And`，和`Xor`也會執行位元算術時使用數字值。</span><span class="sxs-lookup"><span data-stu-id="23944-162">In addition to being logical operators, `Not`, `Or`, `And`, and `Xor` also perform bitwise arithmetic when used on numeric values.</span></span> <span data-ttu-id="23944-163">如需詳細資訊，請參閱 < 位元作業 」[邏輯和位元 Visual Basic 中的運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="23944-163">For more information, see "Bitwise Operations" in [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).</span></span>  
  
## <a name="type-safety"></a><span data-ttu-id="23944-164">型別安全</span><span class="sxs-lookup"><span data-stu-id="23944-164">Type Safety</span></span>  
 <span data-ttu-id="23944-165">運算元通常應屬於相同的型別。</span><span class="sxs-lookup"><span data-stu-id="23944-165">Operands should normally be of the same type.</span></span> <span data-ttu-id="23944-166">例如，如果您要加入`Integer`變數時，您應該將它加入至另一個`Integer`變數，而且您應該將結果指派給類型的變數`Integer`以及。</span><span class="sxs-lookup"><span data-stu-id="23944-166">For example, if you are doing addition with an `Integer` variable, you should add it to another `Integer` variable, and you should assign the result to a variable of type `Integer` as well.</span></span>  
  
 <span data-ttu-id="23944-167">其中一種確保良好的型別安全程式碼撰寫練習是使用[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="23944-167">One way to ensure good type-safe coding practice is to use the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="23944-168">如果您設定`Option Strict On`，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]會自動執行*型別安全*轉換。</span><span class="sxs-lookup"><span data-stu-id="23944-168">If you set `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically performs *type-safe* conversions.</span></span> <span data-ttu-id="23944-169">例如，如果您嘗試新增`Integer`變數`Double`變數並指派的值`Double`變數時，作業正常執行，因為`Integer`值可以轉換成`Double`而不會遺失資料。</span><span class="sxs-lookup"><span data-stu-id="23944-169">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to a `Double` variable, the operation proceeds normally, because an `Integer` value can be converted to `Double` without loss of data.</span></span> <span data-ttu-id="23944-170">型別不安全的轉換，相反地，會造成編譯器錯誤與`Option Strict On`。</span><span class="sxs-lookup"><span data-stu-id="23944-170">Type-unsafe conversions, on the other hand, cause a compiler error with `Option Strict On`.</span></span> <span data-ttu-id="23944-171">例如，如果您嘗試新增`Integer`變數`Double`變數並指派的值`Integer`變數時，會產生編譯器錯誤，因為`Double`變數無法以隱含方式轉換成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="23944-171">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to an `Integer` variable, a compiler error results, because a `Double` variable cannot be implicitly converted to type `Integer`.</span></span>  
  
 <span data-ttu-id="23944-172">如果您設定`Option Strict Off`，不過[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]允許生效，隱含的縮小轉換，但它們可能會導致非預期的資料或精確度遺失。</span><span class="sxs-lookup"><span data-stu-id="23944-172">If you set `Option Strict Off`, however, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] allows implicit narrowing conversions to take place, although they can result in the unexpected loss of data or precision.</span></span> <span data-ttu-id="23944-173">基於這個理由，我們建議您改用`Option Strict On`撰寫實際執行程式碼時。</span><span class="sxs-lookup"><span data-stu-id="23944-173">For this reason, we recommend that you use `Option Strict On` when writing production code.</span></span> <span data-ttu-id="23944-174">如需詳細資訊，請參閱[擴大和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="23944-174">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23944-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23944-175">See Also</span></span>  
 <span data-ttu-id="23944-176">[算術運算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="23944-176">[Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="23944-177"> [位元移位運算子](../../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span><span class="sxs-lookup"><span data-stu-id="23944-177"> [Bit Shift Operators](../../../../visual-basic/language-reference/operators/bit-shift-operators.md) </span></span>  
<span data-ttu-id="23944-178"> [在 Visual Basic 中的比較運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="23944-178"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="23944-179"> [在 Visual Basic 中的串連運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="23944-179"> [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span></span>  
<span data-ttu-id="23944-180"> [在 Visual Basic 中的邏輯和位元運算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="23944-180"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span></span>  
<span data-ttu-id="23944-181"> [有效的運算子組合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span><span class="sxs-lookup"><span data-stu-id="23944-181"> [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span></span>
