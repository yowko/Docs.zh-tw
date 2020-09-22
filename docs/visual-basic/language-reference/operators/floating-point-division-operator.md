---
title: / 運算子
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: 765a80d45908e0ecf17e4c21b748dbf6b2a4c0f5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867039"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b0236-102">/ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0236-102">/ Operator (Visual Basic)</span></span>

<span data-ttu-id="b0236-103">兩數相除並傳回浮點結果。</span><span class="sxs-lookup"><span data-stu-id="b0236-103">Divides two numbers and returns a floating-point result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0236-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0236-104">Syntax</span></span>  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b0236-105">組件</span><span class="sxs-lookup"><span data-stu-id="b0236-105">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="b0236-106">必要。</span><span class="sxs-lookup"><span data-stu-id="b0236-106">Required.</span></span> <span data-ttu-id="b0236-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="b0236-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b0236-108">必要。</span><span class="sxs-lookup"><span data-stu-id="b0236-108">Required.</span></span> <span data-ttu-id="b0236-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="b0236-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="b0236-110">支援的型別</span><span class="sxs-lookup"><span data-stu-id="b0236-110">Supported Types</span></span>  

 <span data-ttu-id="b0236-111">所有數數值型別，包括不帶正負號的和浮點數類型，以及 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="b0236-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="b0236-112">結果</span><span class="sxs-lookup"><span data-stu-id="b0236-112">Result</span></span>  

 <span data-ttu-id="b0236-113">結果是除以的完整商 `expression1` `expression2` ，包含任何餘數。</span><span class="sxs-lookup"><span data-stu-id="b0236-113">The result is the full quotient of `expression1` divided by `expression2`, including any remainder.</span></span>  
  
 <span data-ttu-id="b0236-114">[\ 運算子 (Visual Basic) ](integer-division-operator.md)會傳回整數商，這會捨棄餘數。</span><span class="sxs-lookup"><span data-stu-id="b0236-114">The [\ Operator (Visual Basic)](integer-division-operator.md) returns the integer quotient, which drops the remainder.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0236-115">備註</span><span class="sxs-lookup"><span data-stu-id="b0236-115">Remarks</span></span>  

 <span data-ttu-id="b0236-116">結果的資料類型取決於運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="b0236-116">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="b0236-117">下表顯示如何決定結果的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b0236-117">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="b0236-118">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="b0236-118">Operand data types</span></span>|<span data-ttu-id="b0236-119">結果資料類型</span><span class="sxs-lookup"><span data-stu-id="b0236-119">Result data type</span></span>|  
|------------------------|----------------------|  
|<span data-ttu-id="b0236-120">這兩個運算式都是整數資料類型 ([SByte](../data-types/sbyte-data-type.md)、 [Byte](../data-types/byte-data-type.md)、 [Short](../data-types/short-data-type.md)、 [UShort](../data-types/ushort-data-type.md)、 [Integer](../data-types/integer-data-type.md)、 [UInteger](../data-types/uinteger-data-type.md)、 [Long](../data-types/long-data-type.md)、 [ULong](../data-types/ulong-data-type.md)) </span><span class="sxs-lookup"><span data-stu-id="b0236-120">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|`Double`|  
|<span data-ttu-id="b0236-121">一個運算式是 [單一](../data-types/single-data-type.md) 資料類型，另一個則不是 [雙精度浮點數](../data-types/double-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="b0236-121">One expression is a [Single](../data-types/single-data-type.md) data type and the other is not a [Double](../data-types/double-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="b0236-122">其中一個運算式是[Decimal](../data-types/decimal-data-type.md)資料類型，另一個則不是[單一](../data-types/single-data-type.md)或[雙精度浮點數](../data-types/double-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="b0236-122">One expression is a [Decimal](../data-types/decimal-data-type.md) data type and the other is not a [Single](../data-types/single-data-type.md) or a [Double](../data-types/double-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="b0236-123">任一個運算式是 [Double](../data-types/double-data-type.md) 資料類型</span><span class="sxs-lookup"><span data-stu-id="b0236-123">Either expression is a [Double](../data-types/double-data-type.md) data type</span></span>|`Double`|  
  
 <span data-ttu-id="b0236-124">在執行除法之前，任何整數數值運算式都會擴展至 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="b0236-124">Before division is performed, any integral numeric expressions are widened to `Double`.</span></span> <span data-ttu-id="b0236-125">如果您將結果指派給整數資料類型，Visual Basic 會嘗試將結果轉換 `Double` 為該類型。</span><span class="sxs-lookup"><span data-stu-id="b0236-125">If you assign the result to an integral data type, Visual Basic attempts to convert the result from `Double` to that type.</span></span> <span data-ttu-id="b0236-126">如果結果不符合該類型，這可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b0236-126">This can throw an exception if the result does not fit in that type.</span></span> <span data-ttu-id="b0236-127">特別是，請參閱此說明頁面上的「嘗試零除」。</span><span class="sxs-lookup"><span data-stu-id="b0236-127">In particular, see "Attempted Division by Zero" on this Help page.</span></span>  
  
 <span data-ttu-id="b0236-128">如果 `expression1` 或 `expression2` 評估為 [Nothing](../nothing.md)，則會將其視為零。</span><span class="sxs-lookup"><span data-stu-id="b0236-128">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="b0236-129">嘗試除以零</span><span class="sxs-lookup"><span data-stu-id="b0236-129">Attempted Division by Zero</span></span>  

 <span data-ttu-id="b0236-130">如果 `expression2` 評估為零， `/` 運算子的行為會因不同的運算元資料類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="b0236-130">If `expression2` evaluates to zero, the `/` operator behaves differently for different operand data types.</span></span> <span data-ttu-id="b0236-131">下表顯示可能的行為。</span><span class="sxs-lookup"><span data-stu-id="b0236-131">The following table shows the possible behaviors.</span></span>  
  
|<span data-ttu-id="b0236-132">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="b0236-132">Operand data types</span></span>|<span data-ttu-id="b0236-133">如果 `expression2` 為零，則為行為</span><span class="sxs-lookup"><span data-stu-id="b0236-133">Behavior if `expression2` is zero</span></span>|  
|------------------------|---------------------------------------|  
|<span data-ttu-id="b0236-134">浮點數 (`Single` 或 `Double`) </span><span class="sxs-lookup"><span data-stu-id="b0236-134">Floating-point (`Single` or `Double`)</span></span>|<span data-ttu-id="b0236-135"><xref:System.Double.PositiveInfinity>如果也是零，則傳回無限大 (或 <xref:System.Double.NegativeInfinity>) ，或 <xref:System.Double.NaN> (非數位) `expression1`</span><span class="sxs-lookup"><span data-stu-id="b0236-135">Returns infinity (<xref:System.Double.PositiveInfinity> or <xref:System.Double.NegativeInfinity>), or <xref:System.Double.NaN> (not a number) if `expression1` is also zero</span></span>|  
|`Decimal`|<span data-ttu-id="b0236-136">拋出 <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="b0236-136">Throws <xref:System.DivideByZeroException></span></span>|  
|<span data-ttu-id="b0236-137">整數 (帶正負號或不帶正負號的) </span><span class="sxs-lookup"><span data-stu-id="b0236-137">Integral (signed or unsigned)</span></span>|<span data-ttu-id="b0236-138"><xref:System.OverflowException>因為整數類資料類型無法接受 <xref:System.Double.PositiveInfinity> 、或，所以嘗試轉換回整數類資料類型 <xref:System.Double.NegativeInfinity><xref:System.Double.NaN></span><span class="sxs-lookup"><span data-stu-id="b0236-138">Attempted conversion back to integral type throws <xref:System.OverflowException> because integral types cannot accept <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, or <xref:System.Double.NaN></span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b0236-139">可以多載 `/` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="b0236-139">The `/` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b0236-140">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="b0236-140">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b0236-141">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="b0236-141">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0236-142">範例</span><span class="sxs-lookup"><span data-stu-id="b0236-142">Example</span></span>  

 <span data-ttu-id="b0236-143">這個範例會使用 `/` 運算子來執行浮點除法。</span><span class="sxs-lookup"><span data-stu-id="b0236-143">This example uses the `/` operator to perform floating-point division.</span></span> <span data-ttu-id="b0236-144">結果會是兩個運算元的商。</span><span class="sxs-lookup"><span data-stu-id="b0236-144">The result is the quotient of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 <span data-ttu-id="b0236-145">上述範例中的運算式傳回的值為2.5 和3.333333。</span><span class="sxs-lookup"><span data-stu-id="b0236-145">The expressions in the preceding example return values of 2.5 and 3.333333.</span></span> <span data-ttu-id="b0236-146">請注意， `Double` 即使這兩個運算元都是整數常數，但結果一律為浮點數 () 。</span><span class="sxs-lookup"><span data-stu-id="b0236-146">Note that the result is always floating-point (`Double`), even though both operands are integer constants.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0236-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0236-147">See also</span></span>

- [<span data-ttu-id="b0236-148">/= 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="b0236-148">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="b0236-149">\ 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="b0236-149">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="b0236-150">運算子結果的資料類型</span><span class="sxs-lookup"><span data-stu-id="b0236-150">Data Types of Operator Results</span></span>](data-types-of-operator-results.md)
- [<span data-ttu-id="b0236-151">算術運算子</span><span class="sxs-lookup"><span data-stu-id="b0236-151">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="b0236-152">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="b0236-152">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b0236-153">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="b0236-153">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b0236-154">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="b0236-154">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
