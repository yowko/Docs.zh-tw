---
title: '* 運算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 450d728e44ef5639d75369e05b47cb3009b4d769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="69fb5-102">\* 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69fb5-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="69fb5-103">將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="69fb5-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69fb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="69fb5-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="69fb5-105">組件</span><span class="sxs-lookup"><span data-stu-id="69fb5-105">Parts</span></span>  
  
|<span data-ttu-id="69fb5-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="69fb5-106">Term</span></span>|<span data-ttu-id="69fb5-107">定義</span><span class="sxs-lookup"><span data-stu-id="69fb5-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="69fb5-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="69fb5-108">Required.</span></span> <span data-ttu-id="69fb5-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="69fb5-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="69fb5-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="69fb5-110">Required.</span></span> <span data-ttu-id="69fb5-111">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="69fb5-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="69fb5-112">結果</span><span class="sxs-lookup"><span data-stu-id="69fb5-112">Result</span></span>  
 <span data-ttu-id="69fb5-113">結果是產品的`number1`和`number2`。</span><span class="sxs-lookup"><span data-stu-id="69fb5-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="69fb5-114">支援的型別</span><span class="sxs-lookup"><span data-stu-id="69fb5-114">Supported Types</span></span>  
 <span data-ttu-id="69fb5-115">所有數字類型，包括不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="69fb5-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69fb5-116">備註</span><span class="sxs-lookup"><span data-stu-id="69fb5-116">Remarks</span></span>  
 <span data-ttu-id="69fb5-117">結果的資料類型而定，運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="69fb5-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="69fb5-118">下表顯示如何決定結果的資料類型。</span><span class="sxs-lookup"><span data-stu-id="69fb5-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="69fb5-119">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="69fb5-119">Operand data types</span></span>|<span data-ttu-id="69fb5-120">結果資料類型</span><span class="sxs-lookup"><span data-stu-id="69fb5-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="69fb5-121">這兩個運算式都是整數類資料類型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[位元組](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[簡短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整數](../../../visual-basic/language-reference/data-types/integer-data-type.md)，[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[長](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="69fb5-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="69fb5-122">數值資料類型適合的資料型別`number1`和`number2`。</span><span class="sxs-lookup"><span data-stu-id="69fb5-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="69fb5-123">請參閱中的 「 整數算術 」 資料表[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="69fb5-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="69fb5-124">這兩個運算式都是[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="69fb5-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="69fb5-125">這兩個運算式都是[單一](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="69fb5-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="69fb5-126">任一個運算式是否為浮點資料類型 (`Single`或[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) 但不是能同時`Single`(請注意`Decimal`不是浮點數資料類型)</span><span class="sxs-lookup"><span data-stu-id="69fb5-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="69fb5-127">如果運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，它會被視為零。</span><span class="sxs-lookup"><span data-stu-id="69fb5-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="69fb5-128">多載化</span><span class="sxs-lookup"><span data-stu-id="69fb5-128">Overloading</span></span>  
 <span data-ttu-id="69fb5-129">`*`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="69fb5-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="69fb5-130">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="69fb5-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="69fb5-131">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="69fb5-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69fb5-132">範例</span><span class="sxs-lookup"><span data-stu-id="69fb5-132">Example</span></span>  
 <span data-ttu-id="69fb5-133">這個範例會使用`*`運算子讓兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="69fb5-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="69fb5-134">結果是兩個運算元的產品。</span><span class="sxs-lookup"><span data-stu-id="69fb5-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="69fb5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69fb5-135">See Also</span></span>  
 [<span data-ttu-id="69fb5-136">\*= 運算子</span><span class="sxs-lookup"><span data-stu-id="69fb5-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="69fb5-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="69fb5-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="69fb5-138">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="69fb5-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="69fb5-139">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="69fb5-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="69fb5-140">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="69fb5-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
