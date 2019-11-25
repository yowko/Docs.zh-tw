---
title: '* 運算子'
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
ms.openlocfilehash: 4f6a8ea2c5f4e23791afdfe98d2a08bf67219048
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348369"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="43da1-102">\* 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43da1-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="43da1-103">將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="43da1-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43da1-104">語法</span><span class="sxs-lookup"><span data-stu-id="43da1-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="43da1-105">組件</span><span class="sxs-lookup"><span data-stu-id="43da1-105">Parts</span></span>  
  
|<span data-ttu-id="43da1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="43da1-106">Term</span></span>|<span data-ttu-id="43da1-107">定義</span><span class="sxs-lookup"><span data-stu-id="43da1-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="43da1-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="43da1-108">Required.</span></span> <span data-ttu-id="43da1-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="43da1-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="43da1-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="43da1-110">Required.</span></span> <span data-ttu-id="43da1-111">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="43da1-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="43da1-112">結果</span><span class="sxs-lookup"><span data-stu-id="43da1-112">Result</span></span>  
 <span data-ttu-id="43da1-113">The result is the product of `number1` and `number2`.</span><span class="sxs-lookup"><span data-stu-id="43da1-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="43da1-114">支援的型別</span><span class="sxs-lookup"><span data-stu-id="43da1-114">Supported Types</span></span>  
 <span data-ttu-id="43da1-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="43da1-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43da1-116">備註</span><span class="sxs-lookup"><span data-stu-id="43da1-116">Remarks</span></span>  
 <span data-ttu-id="43da1-117">The data type of the result depends on the types of the operands.</span><span class="sxs-lookup"><span data-stu-id="43da1-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="43da1-118">The following table shows how the data type of the result is determined.</span><span class="sxs-lookup"><span data-stu-id="43da1-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="43da1-119">Operand data types</span><span class="sxs-lookup"><span data-stu-id="43da1-119">Operand data types</span></span>|<span data-ttu-id="43da1-120">Result data type</span><span class="sxs-lookup"><span data-stu-id="43da1-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="43da1-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="43da1-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="43da1-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span><span class="sxs-lookup"><span data-stu-id="43da1-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="43da1-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="43da1-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="43da1-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="43da1-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="43da1-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="43da1-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="43da1-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span><span class="sxs-lookup"><span data-stu-id="43da1-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="43da1-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span><span class="sxs-lookup"><span data-stu-id="43da1-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="43da1-128">多載化</span><span class="sxs-lookup"><span data-stu-id="43da1-128">Overloading</span></span>  
 <span data-ttu-id="43da1-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span><span class="sxs-lookup"><span data-stu-id="43da1-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="43da1-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span><span class="sxs-lookup"><span data-stu-id="43da1-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="43da1-131">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="43da1-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43da1-132">範例</span><span class="sxs-lookup"><span data-stu-id="43da1-132">Example</span></span>  
 <span data-ttu-id="43da1-133">This example uses the `*` operator to multiply two numbers.</span><span class="sxs-lookup"><span data-stu-id="43da1-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="43da1-134">The result is the product of the two operands.</span><span class="sxs-lookup"><span data-stu-id="43da1-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="43da1-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="43da1-135">See also</span></span>

- [<span data-ttu-id="43da1-136">\*= 運算子</span><span class="sxs-lookup"><span data-stu-id="43da1-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="43da1-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="43da1-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="43da1-138">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="43da1-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="43da1-139">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="43da1-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="43da1-140">Arithmetic Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43da1-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
