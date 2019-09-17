---
title: '- 運算子（Visual Basic）'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: eb34b34986613f36b624c43c04f98390ffba4fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965857"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="63b73-102">- 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63b73-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="63b73-103">傳回兩個數值運算式之間的差異，或數值運算式的負數值。</span><span class="sxs-lookup"><span data-stu-id="63b73-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b73-104">語法</span><span class="sxs-lookup"><span data-stu-id="63b73-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="63b73-105">組件</span><span class="sxs-lookup"><span data-stu-id="63b73-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="63b73-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="63b73-106">Required.</span></span> <span data-ttu-id="63b73-107">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="63b73-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="63b73-108">除非`–`運算子正在計算負數值，否則為必要。</span><span class="sxs-lookup"><span data-stu-id="63b73-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="63b73-109">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="63b73-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="63b73-110">結果</span><span class="sxs-lookup"><span data-stu-id="63b73-110">Result</span></span>  
 <span data-ttu-id="63b73-111">結果是和`expression1` `expression2`之間的差異， `expression1`或的負值。</span><span class="sxs-lookup"><span data-stu-id="63b73-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="63b73-112">結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="63b73-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="63b73-113">請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」資料表。</span><span class="sxs-lookup"><span data-stu-id="63b73-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="63b73-114">支援的型別</span><span class="sxs-lookup"><span data-stu-id="63b73-114">Supported Types</span></span>  
 <span data-ttu-id="63b73-115">所有數值類型。</span><span class="sxs-lookup"><span data-stu-id="63b73-115">All numeric types.</span></span> <span data-ttu-id="63b73-116">這包括不帶正負號的和浮點類型`Decimal`，以及。</span><span class="sxs-lookup"><span data-stu-id="63b73-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63b73-117">備註</span><span class="sxs-lookup"><span data-stu-id="63b73-117">Remarks</span></span>  
 <span data-ttu-id="63b73-118">在先前所示的語法中，第一次使用`–`時，運算子是*二元*算術減法運算子，用於兩個數值運算式之間的差異。</span><span class="sxs-lookup"><span data-stu-id="63b73-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="63b73-119">在先前顯示的語法中，第二個使用方式`–`中，運算子是運算式之負值的*一元*負運算子。</span><span class="sxs-lookup"><span data-stu-id="63b73-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="63b73-120">就這一點而言，否定是由反轉的正負號`expression1`所組成，因此如果`expression1`為負數，則結果為正數。</span><span class="sxs-lookup"><span data-stu-id="63b73-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="63b73-121">如果任一運算式評估為[不是任何值](../../../visual-basic/language-reference/nothing.md)，則 `–`運算子會將它視為零。</span><span class="sxs-lookup"><span data-stu-id="63b73-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63b73-122">運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。 `–`</span><span class="sxs-lookup"><span data-stu-id="63b73-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="63b73-123">如果您的程式碼在這類類別或結構上使用這個運算子，請確定您瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="63b73-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="63b73-124">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="63b73-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b73-125">範例</span><span class="sxs-lookup"><span data-stu-id="63b73-125">Example</span></span>  
 <span data-ttu-id="63b73-126">下列範例會使用`–`運算子來計算並傳回兩個數字之間的差異，然後再將數位否定。</span><span class="sxs-lookup"><span data-stu-id="63b73-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="63b73-127">執行這些語句之後， `binaryResult`會包含124.45 和`unaryResult` contains –334.90。</span><span class="sxs-lookup"><span data-stu-id="63b73-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b73-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63b73-128">See also</span></span>

- [<span data-ttu-id="63b73-129">-= 運算子（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="63b73-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="63b73-130">算術運算子</span><span class="sxs-lookup"><span data-stu-id="63b73-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="63b73-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="63b73-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="63b73-132">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="63b73-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="63b73-133">Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="63b73-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
