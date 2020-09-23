---
title: 算術運算子
ms.date: 07/20/2015
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
ms.openlocfilehash: 023e479736285aa2d04509e05f49fe930cb4721d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090075"
---
# <a name="arithmetic-operators-in-visual-basic"></a><span data-ttu-id="b633b-102">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="b633b-102">Arithmetic Operators in Visual Basic</span></span>

<span data-ttu-id="b633b-103">算術運算子用來執行許多常見的算數運算，這些運算牽涉到以常值、變數、其他運算式、函數和屬性呼叫和常數所表示的數值計算。</span><span class="sxs-lookup"><span data-stu-id="b633b-103">Arithmetic operators are used to perform many of the familiar arithmetic operations that involve the calculation of numeric values represented by literals, variables, other expressions, function and property calls, and constants.</span></span> <span data-ttu-id="b633b-104">此外，以算術運算子分類的是位移位運算子，可在運算元的個別位層級上運作，並將其位模式向左或向右移動。</span><span class="sxs-lookup"><span data-stu-id="b633b-104">Also classified with arithmetic operators are the bit-shift operators, which act at the level of the individual bits of the operands and shift their bit patterns to the left or right.</span></span>  
  
## <a name="arithmetic-operations"></a><span data-ttu-id="b633b-105">算術運算</span><span class="sxs-lookup"><span data-stu-id="b633b-105">Arithmetic Operations</span></span>  

 <span data-ttu-id="b633b-106">您可以在運算式中加入兩個值，並加上 [+ 運算子](../../../language-reference/operators/addition-operator.md)，或從另一個值減去另一個值 [ (Visual Basic) ](../../../language-reference/operators/subtraction-operator.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b633b-106">You can add two values in an expression together with the [+ Operator](../../../language-reference/operators/addition-operator.md), or subtract one from another with the [- Operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 <span data-ttu-id="b633b-107">否定也會使用 [-運算子 (Visual Basic) ](../../../language-reference/operators/subtraction-operator.md)，但只有一個運算元，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b633b-107">Negation also uses the [- Operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), but with only one operand, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 <span data-ttu-id="b633b-108">乘法和除法分別使用 [\* 運算子](../../../language-reference/operators/multiplication-operator.md) 和 [/運算子 (Visual Basic) ](../../../language-reference/operators/floating-point-division-operator.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b633b-108">Multiplication and division use the [\* Operator](../../../language-reference/operators/multiplication-operator.md) and [/ Operator (Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md), respectively, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 <span data-ttu-id="b633b-109">乘冪會使用 [^ 運算子](../../../language-reference/operators/exponentiation-operator.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b633b-109">Exponentiation uses the [^ Operator](../../../language-reference/operators/exponentiation-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 <span data-ttu-id="b633b-110">使用 [\ 運算子 (Visual Basic) ](../../../language-reference/operators/integer-division-operator.md)來執行整數除法。</span><span class="sxs-lookup"><span data-stu-id="b633b-110">Integer division is carried out using the [\ Operator (Visual Basic)](../../../language-reference/operators/integer-division-operator.md).</span></span> <span data-ttu-id="b633b-111">整數除法會傳回商，也就是代表除數可以分成被除數的整數數目，而不考慮任何餘數。</span><span class="sxs-lookup"><span data-stu-id="b633b-111">Integer division returns the quotient, that is, the integer that represents the number of times the divisor can divide into the dividend without consideration of any remainder.</span></span> <span data-ttu-id="b633b-112">除數和被除數都必須是整數類資料類型 (`SByte` 、、、、、、 `Byte` `Short` `UShort` `Integer` `UInteger` `Long` 和 `ULong`) 此運算子。</span><span class="sxs-lookup"><span data-stu-id="b633b-112">Both the divisor and the dividend must be integral types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, and `ULong`) for this operator.</span></span> <span data-ttu-id="b633b-113">所有其他類型都必須先轉換成整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="b633b-113">All other types must be converted to an integral type first.</span></span> <span data-ttu-id="b633b-114">下列範例示範整數除法。</span><span class="sxs-lookup"><span data-stu-id="b633b-114">The following example demonstrates integer division.</span></span>  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 <span data-ttu-id="b633b-115">模數算術是使用 [Mod 運算子](../../../language-reference/operators/mod-operator.md)來執行。</span><span class="sxs-lookup"><span data-stu-id="b633b-115">Modulus arithmetic is performed using the [Mod Operator](../../../language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="b633b-116">這個運算子會傳回除數除以整數次之後的餘數。</span><span class="sxs-lookup"><span data-stu-id="b633b-116">This operator returns the remainder after dividing the divisor into the dividend an integral number of times.</span></span> <span data-ttu-id="b633b-117">如果除數和被除數都是整數類資料類型，則傳回的值為整數。</span><span class="sxs-lookup"><span data-stu-id="b633b-117">If both divisor and dividend are integral types, the returned value is integral.</span></span> <span data-ttu-id="b633b-118">如果除數和被除數為浮點數型別，則傳回的值也是浮點類型。</span><span class="sxs-lookup"><span data-stu-id="b633b-118">If divisor and dividend are floating-point types, the returned value is also floating-point.</span></span> <span data-ttu-id="b633b-119">下列範例示範此行為。</span><span class="sxs-lookup"><span data-stu-id="b633b-119">The following example demonstrates this behavior.</span></span>  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a><span data-ttu-id="b633b-120">嘗試除以零</span><span class="sxs-lookup"><span data-stu-id="b633b-120">Attempted Division by Zero</span></span>  

 <span data-ttu-id="b633b-121">根據相關的資料類型而定，零除有不同的結果。</span><span class="sxs-lookup"><span data-stu-id="b633b-121">Division by zero has different results depending on the data types involved.</span></span> <span data-ttu-id="b633b-122">在整數片段 (`SByte` 、 `Byte` 、 `Short` 、、、、 `UShort` `Integer`) 中 `UInteger` `Long` `ULong` ，.NET Framework <xref:System.DivideByZeroException> 會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b633b-122">In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the .NET Framework throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="b633b-123">在或資料類型的除法運算中 `Decimal` `Single` ，.NET Framework 也會擲回 <xref:System.DivideByZeroException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b633b-123">In division operations on the `Decimal` or `Single` data type, the .NET Framework also throws a <xref:System.DivideByZeroException> exception.</span></span>  
  
 <span data-ttu-id="b633b-124">在涉及資料類型的浮點除法中 `Double` ，不會擲回例外狀況，而且結果會是代表、或的類別成員，視被除數而定 <xref:System.Double.NaN> <xref:System.Double.PositiveInfinity> <xref:System.Double.NegativeInfinity> 。</span><span class="sxs-lookup"><span data-stu-id="b633b-124">In floating-point divisions involving the `Double` data type, no exception is thrown, and the result is the class member representing <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, or <xref:System.Double.NegativeInfinity>, depending on the dividend.</span></span> <span data-ttu-id="b633b-125">下表摘要說明嘗試將值除以零的各種結果 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="b633b-125">The following table summarizes the various results of attempting to divide a `Double` value by zero.</span></span>  
  
|<span data-ttu-id="b633b-126">被除數的資料類型</span><span class="sxs-lookup"><span data-stu-id="b633b-126">Dividend data type</span></span>|<span data-ttu-id="b633b-127">除數資料類型</span><span class="sxs-lookup"><span data-stu-id="b633b-127">Divisor data type</span></span>|<span data-ttu-id="b633b-128">被除數值</span><span class="sxs-lookup"><span data-stu-id="b633b-128">Dividend value</span></span>|<span data-ttu-id="b633b-129">結果</span><span class="sxs-lookup"><span data-stu-id="b633b-129">Result</span></span>|  
|---|---|---|---|  
|`Double`|`Double`|<span data-ttu-id="b633b-130">0</span><span class="sxs-lookup"><span data-stu-id="b633b-130">0</span></span>|<span data-ttu-id="b633b-131"><xref:System.Double.NaN> (不是以數學方式定義的數位) </span><span class="sxs-lookup"><span data-stu-id="b633b-131"><xref:System.Double.NaN> (not a mathematically defined number)</span></span>|  
|`Double`|`Double`|<span data-ttu-id="b633b-132">> 0</span><span class="sxs-lookup"><span data-stu-id="b633b-132">> 0</span></span>|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|<span data-ttu-id="b633b-133">\< 0</span><span class="sxs-lookup"><span data-stu-id="b633b-133">\< 0</span></span>|<xref:System.Double.NegativeInfinity>|  
  
 <span data-ttu-id="b633b-134">當您攔截例外狀況時 <xref:System.DivideByZeroException> ，您可以使用它的成員來協助您處理它。</span><span class="sxs-lookup"><span data-stu-id="b633b-134">When you catch a <xref:System.DivideByZeroException> exception, you can use its members to help you handle it.</span></span> <span data-ttu-id="b633b-135">例如，屬性會 <xref:System.Exception.Message%2A> 保存例外狀況的郵件內文。</span><span class="sxs-lookup"><span data-stu-id="b633b-135">For example, the <xref:System.Exception.Message%2A> property holds the message text for the exception.</span></span> <span data-ttu-id="b633b-136">如需詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b633b-136">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="bit-shift-operations"></a><span data-ttu-id="b633b-137">位移位作業</span><span class="sxs-lookup"><span data-stu-id="b633b-137">Bit-Shift Operations</span></span>  

 <span data-ttu-id="b633b-138">位移位運算會在位模式上執行算術移位。</span><span class="sxs-lookup"><span data-stu-id="b633b-138">A bit-shift operation performs an arithmetic shift on a bit pattern.</span></span> <span data-ttu-id="b633b-139">此模式包含在左邊的運算元中，而右邊的運算元則指定要移位模式的位置數目。</span><span class="sxs-lookup"><span data-stu-id="b633b-139">The pattern is contained in the operand on the left, while the operand on the right specifies the number of positions to shift the pattern.</span></span> <span data-ttu-id="b633b-140">您可以使用 [>> 運算子](../../../language-reference/operators/right-shift-operator.md) 或左邊加上 [<< 運算子](../../../language-reference/operators/left-shift-operator.md)，將模式向右移動。</span><span class="sxs-lookup"><span data-stu-id="b633b-140">You can shift the pattern to the right with the [>> Operator](../../../language-reference/operators/right-shift-operator.md) or to the left with the [<< Operator](../../../language-reference/operators/left-shift-operator.md).</span></span>  
  
 <span data-ttu-id="b633b-141">模式運算元的資料類型必須是 `SByte` 、 `Byte` 、 `Short` 、、、 `UShort` `Integer` `UInteger` 、 `Long` 或 `ULong` 。</span><span class="sxs-lookup"><span data-stu-id="b633b-141">The data type of the pattern operand must be `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`.</span></span> <span data-ttu-id="b633b-142">移位量運算元的資料類型必須是 `Integer` 或必須擴展至 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="b633b-142">The data type of the shift amount operand must be `Integer` or must widen to `Integer`.</span></span>  
  
 <span data-ttu-id="b633b-143">算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。</span><span class="sxs-lookup"><span data-stu-id="b633b-143">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b633b-144">由 shift 空出的位位置會設定如下：</span><span class="sxs-lookup"><span data-stu-id="b633b-144">The bit positions vacated by a shift are set as follows:</span></span>  
  
- <span data-ttu-id="b633b-145">0用於算術左移位</span><span class="sxs-lookup"><span data-stu-id="b633b-145">0 for an arithmetic left shift</span></span>  
  
- <span data-ttu-id="b633b-146">0代表正數位的算術右移位</span><span class="sxs-lookup"><span data-stu-id="b633b-146">0 for an arithmetic right shift of a positive number</span></span>  
  
- <span data-ttu-id="b633b-147">0代表不帶正負號資料類型的算術右移（不帶正負號的資料類型 `Byte` ） (、 `UShort` 、 `UInteger` 、 `ULong`) </span><span class="sxs-lookup"><span data-stu-id="b633b-147">0 for an arithmetic right shift of an unsigned data type (`Byte`, `UShort`, `UInteger`, `ULong`)</span></span>  
  
- <span data-ttu-id="b633b-148">1代表數位 (`SByte` 、、 `Short` `Integer` 或 `Long`) 的算術右移位</span><span class="sxs-lookup"><span data-stu-id="b633b-148">1 for an arithmetic right shift of a negative number (`SByte`, `Short`, `Integer`, or `Long`)</span></span>  
  
 <span data-ttu-id="b633b-149">下列範例會將 `Integer` 值向左和向右移。</span><span class="sxs-lookup"><span data-stu-id="b633b-149">The following example shifts an `Integer` value both left and right.</span></span>  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 <span data-ttu-id="b633b-150">算術移位絕不會產生溢位例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b633b-150">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="b633b-151">位運算</span><span class="sxs-lookup"><span data-stu-id="b633b-151">Bitwise Operations</span></span>  

 <span data-ttu-id="b633b-152">除了為邏輯運算子之外，、 `Not` 、 `Or` `And` 和也會在 `Xor` 使用於數值時執行位運算。</span><span class="sxs-lookup"><span data-stu-id="b633b-152">In addition to being logical operators, `Not`, `Or`, `And`, and `Xor` also perform bitwise arithmetic when used on numeric values.</span></span> <span data-ttu-id="b633b-153">如需詳細資訊，請參閱 [Visual Basic 中邏輯和位運算子](logical-and-bitwise-operators.md)中的「位運算」。</span><span class="sxs-lookup"><span data-stu-id="b633b-153">For more information, see "Bitwise Operations" in [Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md).</span></span>  
  
## <a name="type-safety"></a><span data-ttu-id="b633b-154">型別安全</span><span class="sxs-lookup"><span data-stu-id="b633b-154">Type Safety</span></span>  

 <span data-ttu-id="b633b-155">運算元通常應該是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="b633b-155">Operands should normally be of the same type.</span></span> <span data-ttu-id="b633b-156">例如，如果您要加入 `Integer` 變數，您應該將它新增至另一個 `Integer` 變數，也應該將結果指派給類型的變數 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="b633b-156">For example, if you are doing addition with an `Integer` variable, you should add it to another `Integer` variable, and you should assign the result to a variable of type `Integer` as well.</span></span>  
  
 <span data-ttu-id="b633b-157">有一種方法可確保良好的型別安全程式碼撰寫作法是使用 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="b633b-157">One way to ensure good type-safe coding practice is to use the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="b633b-158">如果設定 `Option Strict On` ，Visual Basic 會自動執行 *型別安全* 轉換。</span><span class="sxs-lookup"><span data-stu-id="b633b-158">If you set `Option Strict On`, Visual Basic automatically performs *type-safe* conversions.</span></span> <span data-ttu-id="b633b-159">例如，如果您嘗試將 `Integer` 變數新增至 `Double` 變數，並將值指派給 `Double` 變數，則作業會正常執行，因為 `Integer` 值可以轉換成 `Double` 不會遺失資料。</span><span class="sxs-lookup"><span data-stu-id="b633b-159">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to a `Double` variable, the operation proceeds normally, because an `Integer` value can be converted to `Double` without loss of data.</span></span> <span data-ttu-id="b633b-160">另一方面，型別 unsafe 轉換會造成編譯器錯誤 `Option Strict On` 。</span><span class="sxs-lookup"><span data-stu-id="b633b-160">Type-unsafe conversions, on the other hand, cause a compiler error with `Option Strict On`.</span></span> <span data-ttu-id="b633b-161">例如，如果您嘗試將變數加入變數 `Integer` `Double` ，並將值指派給 `Integer` 變數，就會產生編譯器錯誤，因為 `Double` 變數無法隱含轉換成類型 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="b633b-161">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to an `Integer` variable, a compiler error results, because a `Double` variable cannot be implicitly converted to type `Integer`.</span></span>  
  
 <span data-ttu-id="b633b-162">但是，如果您設定 `Option Strict Off` Visual Basic 允許隱含的縮小轉換，雖然它們可能會導致非預期的資料或精確度遺失。</span><span class="sxs-lookup"><span data-stu-id="b633b-162">If you set `Option Strict Off`, however, Visual Basic allows implicit narrowing conversions to take place, although they can result in the unexpected loss of data or precision.</span></span> <span data-ttu-id="b633b-163">基於這個理由，我們建議您在 `Option Strict On` 撰寫生產程式碼時使用。</span><span class="sxs-lookup"><span data-stu-id="b633b-163">For this reason, we recommend that you use `Option Strict On` when writing production code.</span></span> <span data-ttu-id="b633b-164">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="b633b-164">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b633b-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b633b-165">See also</span></span>

- [<span data-ttu-id="b633b-166">算術運算子</span><span class="sxs-lookup"><span data-stu-id="b633b-166">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b633b-167">位元移位運算子</span><span class="sxs-lookup"><span data-stu-id="b633b-167">Bit Shift Operators</span></span>](../../../language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="b633b-168">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b633b-168">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="b633b-169">Visual Basic 中的串連運算子</span><span class="sxs-lookup"><span data-stu-id="b633b-169">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="b633b-170">Visual Basic 中的邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="b633b-170">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="b633b-171">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="b633b-171">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
