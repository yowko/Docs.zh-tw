---
title: '- 運算子'
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
ms.openlocfilehash: b5129c2dbb361940fa6da2cb424ee23736ba72c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875336"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="6eb98-102">- 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6eb98-102">- Operator (Visual Basic)</span></span>

<span data-ttu-id="6eb98-103">傳回兩個數值運算式或數值運算式的負數值之間的差異。</span><span class="sxs-lookup"><span data-stu-id="6eb98-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb98-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6eb98-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="6eb98-105">或</span><span class="sxs-lookup"><span data-stu-id="6eb98-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="6eb98-106">組件</span><span class="sxs-lookup"><span data-stu-id="6eb98-106">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="6eb98-107">必要。</span><span class="sxs-lookup"><span data-stu-id="6eb98-107">Required.</span></span> <span data-ttu-id="6eb98-108">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6eb98-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="6eb98-109">除非 `–` 運算子計算負數值，否則為必要項。</span><span class="sxs-lookup"><span data-stu-id="6eb98-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="6eb98-110">任何數值運算式。</span><span class="sxs-lookup"><span data-stu-id="6eb98-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="6eb98-111">結果</span><span class="sxs-lookup"><span data-stu-id="6eb98-111">Result</span></span>  

 <span data-ttu-id="6eb98-112">結果是和之間的差異 `expression1` `expression2` ，或的負數值 `expression1` 。</span><span class="sxs-lookup"><span data-stu-id="6eb98-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="6eb98-113">結果資料類型是適用于和之資料類型的數數值型別 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="6eb98-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="6eb98-114">請參閱 [運算子結果資料類型](data-types-of-operator-results.md)中的「整數算術」資料表。</span><span class="sxs-lookup"><span data-stu-id="6eb98-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="6eb98-115">支援的型別</span><span class="sxs-lookup"><span data-stu-id="6eb98-115">Supported Types</span></span>  

 <span data-ttu-id="6eb98-116">所有數值類型。</span><span class="sxs-lookup"><span data-stu-id="6eb98-116">All numeric types.</span></span> <span data-ttu-id="6eb98-117">這包括不帶正負號的和浮點數類型和 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="6eb98-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb98-118">備註</span><span class="sxs-lookup"><span data-stu-id="6eb98-118">Remarks</span></span>  

 <span data-ttu-id="6eb98-119">在先前所顯示的語法中， `–` 運算子是兩個數值運算式之間差異的 *二進位* 算術減法運算子。</span><span class="sxs-lookup"><span data-stu-id="6eb98-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="6eb98-120">在先前所顯示的語法中， `–` 運算子是運算式負數值的 *一元* 負運算子。</span><span class="sxs-lookup"><span data-stu-id="6eb98-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="6eb98-121">在這種情況下，負號包含反轉的正負號， `expression1` 因此如果是負數，則結果為正數 `expression1` 。</span><span class="sxs-lookup"><span data-stu-id="6eb98-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="6eb98-122">如果任一個運算式評估為 [Nothing](../nothing.md)， `–` 運算子就會將它視為零。</span><span class="sxs-lookup"><span data-stu-id="6eb98-122">If either expression evaluates to [Nothing](../nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6eb98-123">可以多載 `–` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="6eb98-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="6eb98-124">如果您的程式碼在這類類別或結構上使用這個運算子，請確定您瞭解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="6eb98-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="6eb98-125">如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb98-125">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eb98-126">範例</span><span class="sxs-lookup"><span data-stu-id="6eb98-126">Example</span></span>  

 <span data-ttu-id="6eb98-127">下列範例會使用 `–` 運算子來計算並傳回兩個數字之間的差異，然後再對數位進行否定。</span><span class="sxs-lookup"><span data-stu-id="6eb98-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="6eb98-128">執行這些語句之後，會 `binaryResult` 包含124.45 且 `unaryResult` contains –334.90。</span><span class="sxs-lookup"><span data-stu-id="6eb98-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb98-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eb98-129">See also</span></span>

- [<span data-ttu-id="6eb98-130">-= 運算子 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="6eb98-130">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="6eb98-131">算術運算子</span><span class="sxs-lookup"><span data-stu-id="6eb98-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="6eb98-132">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="6eb98-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="6eb98-133">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="6eb98-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="6eb98-134">Visual Basic 的算術運算子</span><span class="sxs-lookup"><span data-stu-id="6eb98-134">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
