---
title: "- 運算子 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
dev_langs:
- VB
helpviewer_keywords:
- '- operator [Visual Basic]'
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator
- operators [Visual Basic], arithmetic
- subtraction operator, syntax
- arithmetic operators, subtraction
- difference operator
- math operators
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: eb9b8e94877cce9aacde69c5f555f4a7f4a9ad7c
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="--operator-visual-basic"></a><span data-ttu-id="16639-102">- 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16639-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="16639-103">傳回兩個數值運算式或數值運算式的負值之間的差異。</span><span class="sxs-lookup"><span data-stu-id="16639-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16639-104">語法</span><span class="sxs-lookup"><span data-stu-id="16639-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="16639-105">組件</span><span class="sxs-lookup"><span data-stu-id="16639-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="16639-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="16639-106">Required.</span></span> <span data-ttu-id="16639-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="16639-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="16639-108">除非`–`運算子計算的負值。</span><span class="sxs-lookup"><span data-stu-id="16639-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="16639-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="16639-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="16639-110">結果</span><span class="sxs-lookup"><span data-stu-id="16639-110">Result</span></span>  
 <span data-ttu-id="16639-111">結果是之間的差異`expression1`和`expression2`，相反的值或`expression1`。</span><span class="sxs-lookup"><span data-stu-id="16639-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="16639-112">結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="16639-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="16639-113">請參閱中的 「 整數算術 」 資料表[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="16639-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="16639-114">支援的型別</span><span class="sxs-lookup"><span data-stu-id="16639-114">Supported Types</span></span>  
 <span data-ttu-id="16639-115">所有數字型別。</span><span class="sxs-lookup"><span data-stu-id="16639-115">All numeric types.</span></span> <span data-ttu-id="16639-116">這包括不帶正負號和浮點類型和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="16639-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16639-117">備註</span><span class="sxs-lookup"><span data-stu-id="16639-117">Remarks</span></span>  
 <span data-ttu-id="16639-118">在先前所示的語法中顯示的第一個使用`–`運算子是*二進位*算術減法運算子的兩個數值運算式之間的差異。</span><span class="sxs-lookup"><span data-stu-id="16639-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="16639-119">在先前所示的語法中顯示的第二個使用方式`–`運算子是*一元*負運算子的運算式的負值。</span><span class="sxs-lookup"><span data-stu-id="16639-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="16639-120">在這種情況下，否定包含反轉的正負號`expression1`使結果為正數如果`expression1`是負數。</span><span class="sxs-lookup"><span data-stu-id="16639-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="16639-121">如果任一個運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`運算子會將其視為零。</span><span class="sxs-lookup"><span data-stu-id="16639-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16639-122">`–`運算子可以*多載*，也就是說，類別或結構可以重新定義它的行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="16639-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="16639-123">如果您的程式碼會使用此運算子在這種類別或結構，請確定您已了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="16639-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="16639-124">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="16639-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16639-125">範例</span><span class="sxs-lookup"><span data-stu-id="16639-125">Example</span></span>  
 <span data-ttu-id="16639-126">下列範例會使用`–`運算子來計算並傳回兩個數字，之間的差異，然後要變換正負號的數字。</span><span class="sxs-lookup"><span data-stu-id="16639-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 <span data-ttu-id="16639-127">[!code-vb[VbVbalrOperators #&10;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="16639-127">[!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="16639-128">在執行這些陳述式，`binaryResult`包含 124.45 和`unaryResult`包含 –334.90。</span><span class="sxs-lookup"><span data-stu-id="16639-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16639-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16639-129">See Also</span></span>  
 <span data-ttu-id="16639-130">[-= 運算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [算術運算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="16639-130">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="16639-131"> [在 Visual Basic 中的運算子優先順序](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="16639-131"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="16639-132"> [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="16639-132"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="16639-133"> [在 Visual Basic 中的算術運算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="16639-133"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

