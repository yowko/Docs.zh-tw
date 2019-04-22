---
title: '* 運算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 09b95585325b05c0b7925c4c1c9e123f45791e10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828949"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8cbba-102">\* 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cbba-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="8cbba-103">將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="8cbba-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbba-104">語法</span><span class="sxs-lookup"><span data-stu-id="8cbba-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="8cbba-105">組件</span><span class="sxs-lookup"><span data-stu-id="8cbba-105">Parts</span></span>  
  
|<span data-ttu-id="8cbba-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="8cbba-106">Term</span></span>|<span data-ttu-id="8cbba-107">定義</span><span class="sxs-lookup"><span data-stu-id="8cbba-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="8cbba-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="8cbba-108">Required.</span></span> <span data-ttu-id="8cbba-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="8cbba-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="8cbba-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="8cbba-110">Required.</span></span> <span data-ttu-id="8cbba-111">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="8cbba-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="8cbba-112">結果</span><span class="sxs-lookup"><span data-stu-id="8cbba-112">Result</span></span>  
 <span data-ttu-id="8cbba-113">結果是乘積`number1`和`number2`。</span><span class="sxs-lookup"><span data-stu-id="8cbba-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="8cbba-114">支援的型別</span><span class="sxs-lookup"><span data-stu-id="8cbba-114">Supported Types</span></span>  
 <span data-ttu-id="8cbba-115">所有的數字類型，包括不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="8cbba-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cbba-116">備註</span><span class="sxs-lookup"><span data-stu-id="8cbba-116">Remarks</span></span>  
 <span data-ttu-id="8cbba-117">結果的資料類型取決於運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="8cbba-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="8cbba-118">下表顯示如何決定結果的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8cbba-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="8cbba-119">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="8cbba-119">Operand data types</span></span>|<span data-ttu-id="8cbba-120">結果資料類型</span><span class="sxs-lookup"><span data-stu-id="8cbba-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="8cbba-121">這兩個運算式都是整數資料類型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)，[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="8cbba-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="8cbba-122">適用於資料類型的數值資料類型`number1`和`number2`。</span><span class="sxs-lookup"><span data-stu-id="8cbba-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="8cbba-123">請參閱中的 「 整數算術 」 表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="8cbba-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="8cbba-124">這兩個運算式都是[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="8cbba-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="8cbba-125">這兩個運算式都是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="8cbba-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="8cbba-126">任一個運算式是否為浮點資料類型 (`Single`或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md))，但不是能兩者都`Single`(請注意`Decimal`不是浮點資料類型)</span><span class="sxs-lookup"><span data-stu-id="8cbba-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="8cbba-127">如果運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。</span><span class="sxs-lookup"><span data-stu-id="8cbba-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8cbba-128">多載化</span><span class="sxs-lookup"><span data-stu-id="8cbba-128">Overloading</span></span>  
 <span data-ttu-id="8cbba-129">`*`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="8cbba-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8cbba-130">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="8cbba-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8cbba-131">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="8cbba-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cbba-132">範例</span><span class="sxs-lookup"><span data-stu-id="8cbba-132">Example</span></span>  
 <span data-ttu-id="8cbba-133">這個範例會使用`*`運算子來將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="8cbba-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="8cbba-134">結果是兩個運算元的乘積。</span><span class="sxs-lookup"><span data-stu-id="8cbba-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8cbba-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cbba-135">See also</span></span>

- [<span data-ttu-id="8cbba-136">\*= 運算子</span><span class="sxs-lookup"><span data-stu-id="8cbba-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="8cbba-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="8cbba-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="8cbba-138">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="8cbba-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8cbba-139">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="8cbba-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8cbba-140">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="8cbba-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
