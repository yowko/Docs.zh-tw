---
title: '* 運算子（Visual Basic）'
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
ms.openlocfilehash: b5b601c7604cb7ce1afaebc98b2157634a77fda4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701098"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="934df-102">\* 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="934df-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="934df-103">將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="934df-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="934df-104">語法</span><span class="sxs-lookup"><span data-stu-id="934df-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="934df-105">組件</span><span class="sxs-lookup"><span data-stu-id="934df-105">Parts</span></span>  
  
|<span data-ttu-id="934df-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="934df-106">Term</span></span>|<span data-ttu-id="934df-107">定義</span><span class="sxs-lookup"><span data-stu-id="934df-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="934df-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="934df-108">Required.</span></span> <span data-ttu-id="934df-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="934df-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="934df-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="934df-110">Required.</span></span> <span data-ttu-id="934df-111">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="934df-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="934df-112">結果</span><span class="sxs-lookup"><span data-stu-id="934df-112">Result</span></span>  
 <span data-ttu-id="934df-113">結果為 `number1` 和 `number2` 的乘積。</span><span class="sxs-lookup"><span data-stu-id="934df-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="934df-114">支援的型別</span><span class="sxs-lookup"><span data-stu-id="934df-114">Supported Types</span></span>  
 <span data-ttu-id="934df-115">所有數數值型別，包括不帶正負號的和浮點類型，以及 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="934df-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="934df-116">備註</span><span class="sxs-lookup"><span data-stu-id="934df-116">Remarks</span></span>  
 <span data-ttu-id="934df-117">結果的資料類型取決於運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="934df-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="934df-118">下表顯示如何判斷結果的資料類型。</span><span class="sxs-lookup"><span data-stu-id="934df-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="934df-119">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="934df-119">Operand data types</span></span>|<span data-ttu-id="934df-120">結果資料類型</span><span class="sxs-lookup"><span data-stu-id="934df-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="934df-121">這兩個運算式都是整數資料類型（[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、 [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、 [Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、 [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、 [Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)）</span><span class="sxs-lookup"><span data-stu-id="934df-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="934df-122">適用于 `number1` 和 `number2` 之資料類型的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="934df-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="934df-123">請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」資料表。</span><span class="sxs-lookup"><span data-stu-id="934df-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="934df-124">這兩個運算式都是[十進位](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="934df-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="934df-125">這兩個運算式都是[Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="934df-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="934df-126">任一運算式是浮點資料類型（`Single` 或[雙精度](../../../visual-basic/language-reference/data-types/double-data-type.md)浮點數），但不能同時 `Single` （注意 `Decimal` 不是浮點資料類型）</span><span class="sxs-lookup"><span data-stu-id="934df-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="934df-127">如果運算式評估為不是[任何](../../../visual-basic/language-reference/nothing.md)值，則會將它視為零。</span><span class="sxs-lookup"><span data-stu-id="934df-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="934df-128">多載化</span><span class="sxs-lookup"><span data-stu-id="934df-128">Overloading</span></span>  
 <span data-ttu-id="934df-129">@No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="934df-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="934df-130">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="934df-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="934df-131">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="934df-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="934df-132">範例</span><span class="sxs-lookup"><span data-stu-id="934df-132">Example</span></span>  
 <span data-ttu-id="934df-133">這個範例會使用 `*` 運算子來將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="934df-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="934df-134">結果為兩個運算元的乘積。</span><span class="sxs-lookup"><span data-stu-id="934df-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="934df-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="934df-135">See also</span></span>

- [<span data-ttu-id="934df-136">\*= 運算子</span><span class="sxs-lookup"><span data-stu-id="934df-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="934df-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="934df-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="934df-138">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="934df-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="934df-139">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="934df-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="934df-140">Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="934df-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
