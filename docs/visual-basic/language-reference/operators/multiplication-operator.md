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
ms.openlocfilehash: 7038fef4258d190b726a851b26f2a2840ff3c0ea
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873369"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="04abb-102">\* 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04abb-102">\* Operator (Visual Basic)</span></span>

<span data-ttu-id="04abb-103">兩個數目相乘。</span><span class="sxs-lookup"><span data-stu-id="04abb-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04abb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="04abb-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="04abb-105">組件</span><span class="sxs-lookup"><span data-stu-id="04abb-105">Parts</span></span>  
  
|<span data-ttu-id="04abb-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="04abb-106">Term</span></span>|<span data-ttu-id="04abb-107">定義</span><span class="sxs-lookup"><span data-stu-id="04abb-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="04abb-108">必要。</span><span class="sxs-lookup"><span data-stu-id="04abb-108">Required.</span></span> <span data-ttu-id="04abb-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="04abb-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="04abb-110">必要。</span><span class="sxs-lookup"><span data-stu-id="04abb-110">Required.</span></span> <span data-ttu-id="04abb-111">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="04abb-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="04abb-112">結果</span><span class="sxs-lookup"><span data-stu-id="04abb-112">Result</span></span>  

 <span data-ttu-id="04abb-113">結果會是和的乘積 `number1` `number2` 。</span><span class="sxs-lookup"><span data-stu-id="04abb-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="04abb-114">支援的型別</span><span class="sxs-lookup"><span data-stu-id="04abb-114">Supported Types</span></span>  

 <span data-ttu-id="04abb-115">所有數數值型別，包括不帶正負號的和浮點數類型，以及 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="04abb-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04abb-116">備註</span><span class="sxs-lookup"><span data-stu-id="04abb-116">Remarks</span></span>  

 <span data-ttu-id="04abb-117">結果的資料類型取決於運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="04abb-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="04abb-118">下表顯示如何決定結果的資料類型。</span><span class="sxs-lookup"><span data-stu-id="04abb-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="04abb-119">運算元資料類型</span><span class="sxs-lookup"><span data-stu-id="04abb-119">Operand data types</span></span>|<span data-ttu-id="04abb-120">結果資料類型</span><span class="sxs-lookup"><span data-stu-id="04abb-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="04abb-121">這兩個運算式都是整數資料類型 ([SByte](../data-types/sbyte-data-type.md)、 [Byte](../data-types/byte-data-type.md)、 [Short](../data-types/short-data-type.md)、 [UShort](../data-types/ushort-data-type.md)、 [Integer](../data-types/integer-data-type.md)、 [UInteger](../data-types/uinteger-data-type.md)、 [Long](../data-types/long-data-type.md)、 [ULong](../data-types/ulong-data-type.md)) </span><span class="sxs-lookup"><span data-stu-id="04abb-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="04abb-122">適用于和之資料類型的數值資料類型 `number1` `number2` 。</span><span class="sxs-lookup"><span data-stu-id="04abb-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="04abb-123">請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「整數算術」資料表。</span><span class="sxs-lookup"><span data-stu-id="04abb-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="04abb-124">這兩個運算式都是 [Decimal](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="04abb-124">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="04abb-125">這兩個運算式都是 [Single](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="04abb-125">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="04abb-126">任一個運算式是浮點數資料類型 (`Single` 或 [Double](../data-types/double-data-type.md)) 但不是兩個 `Single` (附注都不是 `Decimal` 浮點數資料類型) </span><span class="sxs-lookup"><span data-stu-id="04abb-126">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="04abb-127">如果運算式評估為 [Nothing](../nothing.md)，則會將其視為零。</span><span class="sxs-lookup"><span data-stu-id="04abb-127">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="04abb-128">多載化</span><span class="sxs-lookup"><span data-stu-id="04abb-128">Overloading</span></span>  

 <span data-ttu-id="04abb-129">可以多載 `*` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="04abb-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="04abb-130">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="04abb-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="04abb-131">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="04abb-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04abb-132">範例</span><span class="sxs-lookup"><span data-stu-id="04abb-132">Example</span></span>  

 <span data-ttu-id="04abb-133">這個範例會使用 `*` 運算子來將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="04abb-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="04abb-134">結果會是兩個運算元的乘積。</span><span class="sxs-lookup"><span data-stu-id="04abb-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="04abb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04abb-135">See also</span></span>

- [<span data-ttu-id="04abb-136">\* = 運算子</span><span class="sxs-lookup"><span data-stu-id="04abb-136">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="04abb-137">算術運算子</span><span class="sxs-lookup"><span data-stu-id="04abb-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="04abb-138">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="04abb-138">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="04abb-139">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="04abb-139">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="04abb-140">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="04abb-140">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
