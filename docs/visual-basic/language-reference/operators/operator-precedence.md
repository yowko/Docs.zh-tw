---
title: Visual Basic 中的運算子優先順序
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 568927eb4759c214311ad34a5b45e28094dd80be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013526"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="0a52d-102">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="0a52d-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="0a52d-103">每個部分時數個作業發生時在運算式中，評估，以及在預先決定的順序呼叫中解決*運算子優先順序*。</span><span class="sxs-lookup"><span data-stu-id="0a52d-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="0a52d-104">優先順序規則</span><span class="sxs-lookup"><span data-stu-id="0a52d-104">Precedence Rules</span></span>  
 <span data-ttu-id="0a52d-105">當運算式包含來自多個類別目錄的運算子時，會評估根據下列規則：</span><span class="sxs-lookup"><span data-stu-id="0a52d-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
- <span data-ttu-id="0a52d-106">算術和串連運算子有下列的一節所述的優先順序，都有更高的優先順序高於比較、 邏輯和位元運算子。</span><span class="sxs-lookup"><span data-stu-id="0a52d-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
- <span data-ttu-id="0a52d-107">所有的比較運算子具有相等的優先順序，及其所有具有較高的優先順序高於邏輯和位元運算子，但較低的優先順序高於算術和串連運算子。</span><span class="sxs-lookup"><span data-stu-id="0a52d-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
- <span data-ttu-id="0a52d-108">邏輯和位元運算子有下列的一節所述的優先順序，所有具有較低的優先順序高於算術運算子、 串連和比較運算子。</span><span class="sxs-lookup"><span data-stu-id="0a52d-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
- <span data-ttu-id="0a52d-109">具有相同優先順序的運算子會由左至右評估以其出現在運算式中的順序。</span><span class="sxs-lookup"><span data-stu-id="0a52d-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="0a52d-110">優先順序</span><span class="sxs-lookup"><span data-stu-id="0a52d-110">Precedence Order</span></span>  
 <span data-ttu-id="0a52d-111">運算子會評估順序的優先順序如下：</span><span class="sxs-lookup"><span data-stu-id="0a52d-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="0a52d-112">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-112">Await Operator</span></span>  
 <span data-ttu-id="0a52d-113">Await</span><span class="sxs-lookup"><span data-stu-id="0a52d-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="0a52d-114">算術運算子和串連運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="0a52d-115">乘冪 (`^`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="0a52d-116">一元 （unary) 身分識別和否定 (`+`， `–`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="0a52d-117">乘法和浮點除法 (`*`， `/`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="0a52d-118">整數除法 (`\`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="0a52d-119">模數算術 (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="0a52d-120">加法和減法 (`+`， `–`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="0a52d-121">字串串連 (`&`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="0a52d-122">算術的位元移位 (`<<`， `>>`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="0a52d-123">比較運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-123">Comparison Operators</span></span>  
 <span data-ttu-id="0a52d-124">所有的比較運算子 (`=`， `<>`， `<`， `<=`， `>`， `>=`， `Is`， `IsNot`， `Like`， `TypeOf`...`Is`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="0a52d-125">邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="0a52d-126">否定 (`Not`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="0a52d-127">搭配使用 (`And`， `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="0a52d-128">內含分離 (`Or`， `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="0a52d-129">獨佔分離 (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="0a52d-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="0a52d-130">註解</span><span class="sxs-lookup"><span data-stu-id="0a52d-130">Comments</span></span>  
 <span data-ttu-id="0a52d-131">`=`運算子只是等號比較運算子，不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="0a52d-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="0a52d-132">字串串連運算子 (`&`) 不是算術運算子，但它分組搭配算術運算子的優先順序。</span><span class="sxs-lookup"><span data-stu-id="0a52d-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="0a52d-133">`Is`和`IsNot`運算子是物件參考的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="0a52d-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="0a52d-134">它們不會比較兩個物件; 的值他們檢查才能判斷兩個物件變數是否指向相同物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="0a52d-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="0a52d-135">順序關聯性</span><span class="sxs-lookup"><span data-stu-id="0a52d-135">Associativity</span></span>  
 <span data-ttu-id="0a52d-136">當相同優先順序的運算子一起出現在運算式中，例如乘法與除法，編譯器會評估每個作業發生它從左到右。</span><span class="sxs-lookup"><span data-stu-id="0a52d-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="0a52d-137">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="0a52d-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="0a52d-138">第一個運算式會評估部門 96 / 8 （這會產生 12），然後除法 12 / 4，這會產生三個。</span><span class="sxs-lookup"><span data-stu-id="0a52d-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="0a52d-139">因為編譯器會評估的作業`n1`從左到右，評估時，相同的明確指定該順序`n2`。</span><span class="sxs-lookup"><span data-stu-id="0a52d-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="0a52d-140">兩者`n1`和`n2`有三個結果。</span><span class="sxs-lookup"><span data-stu-id="0a52d-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="0a52d-141">相較之下，`n3`的結果是 48，因為括號會強制編譯器將評估 8 / 4 第一次。</span><span class="sxs-lookup"><span data-stu-id="0a52d-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="0a52d-142">由於這個行為，運算子可以說是*左向*Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="0a52d-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="0a52d-143">覆寫優先順序和關聯性</span><span class="sxs-lookup"><span data-stu-id="0a52d-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="0a52d-144">若要強制其他項目之前評估運算式的某些部分，您可以使用括號。</span><span class="sxs-lookup"><span data-stu-id="0a52d-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="0a52d-145">優先順序和左順序關聯性，也可以覆寫。</span><span class="sxs-lookup"><span data-stu-id="0a52d-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="0a52d-146">Visual Basic 一律會執行之前以外的括號括住的作業。</span><span class="sxs-lookup"><span data-stu-id="0a52d-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="0a52d-147">不過，在括號，它會維護一般優先順序和關聯性，除非您使用以括弧括住的括號。</span><span class="sxs-lookup"><span data-stu-id="0a52d-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="0a52d-148">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="0a52d-148">The following example illustrates this.</span></span>  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a52d-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a52d-149">See also</span></span>

- [<span data-ttu-id="0a52d-150">= 運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="0a52d-151">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="0a52d-152">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="0a52d-153">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="0a52d-154">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="0a52d-155">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="0a52d-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="0a52d-156">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="0a52d-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0a52d-157">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="0a52d-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
