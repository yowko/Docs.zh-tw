---
title: Visual Basic 中的運算子優先順序
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d8de9deea84c7f0c11c91b55951cdfc200b017f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="b9b68-102">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="b9b68-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="b9b68-103">每個組件時數個作業發生時在運算式中，評估，而且在呼叫預先定義的順序解決*運算子優先順序*。</span><span class="sxs-lookup"><span data-stu-id="b9b68-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="b9b68-104">優先順序規則</span><span class="sxs-lookup"><span data-stu-id="b9b68-104">Precedence Rules</span></span>  
 <span data-ttu-id="b9b68-105">當運算式包含來自多個類別目錄的運算子時，它們會根據下列規則進行評估：</span><span class="sxs-lookup"><span data-stu-id="b9b68-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="b9b68-106">算術和串連運算子具有的優先順序在下一節中所述，而且全都有更高的優先順序高於比較、 邏輯和位元運算子。</span><span class="sxs-lookup"><span data-stu-id="b9b68-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="b9b68-107">所有比較運算子都有相同的優先順序，以及所有都具有較高的優先順序高於邏輯和位元運算子，但較低的優先順序高於算術和串連運算子。</span><span class="sxs-lookup"><span data-stu-id="b9b68-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="b9b68-108">邏輯和位元運算子具有的優先順序在下一節中所述，而且全都有較低的優先順序高於算術、 串連運算子和比較運算子。</span><span class="sxs-lookup"><span data-stu-id="b9b68-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="b9b68-109">具有相同優先順序的運算子會由左至右評估的運算式中出現的順序。</span><span class="sxs-lookup"><span data-stu-id="b9b68-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="b9b68-110">優先順序</span><span class="sxs-lookup"><span data-stu-id="b9b68-110">Precedence Order</span></span>  
 <span data-ttu-id="b9b68-111">運算子會評估順序的優先順序如下：</span><span class="sxs-lookup"><span data-stu-id="b9b68-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="b9b68-112">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-112">Await Operator</span></span>  
 <span data-ttu-id="b9b68-113">await</span><span class="sxs-lookup"><span data-stu-id="b9b68-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="b9b68-114">算術運算子和串連運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="b9b68-115">乘冪 (`^`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="b9b68-116">一元身分識別和否定 (`+`， `–`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="b9b68-117">乘法和除法浮點 (`*`， `/`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="b9b68-118">整數除法 (`\`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="b9b68-119">模數算術 (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="b9b68-120">加法和減法 (`+`， `–`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="b9b68-121">字串串連 (`&`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="b9b68-122">算術的位元移位 (`<<`， `>>`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="b9b68-123">比較運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-123">Comparison Operators</span></span>  
 <span data-ttu-id="b9b68-124">所有比較運算子 (`=`， `<>`， `<`， `<=`， `>`， `>=`， `Is`， `IsNot`， `Like`， `TypeOf`...`Is`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="b9b68-125">邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="b9b68-126">否定 (`Not`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="b9b68-127">搭配使用 (`And`， `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="b9b68-128">內含分離 (`Or`， `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="b9b68-129">排除分離 (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="b9b68-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="b9b68-130">註解</span><span class="sxs-lookup"><span data-stu-id="b9b68-130">Comments</span></span>  
 <span data-ttu-id="b9b68-131">`=`運算子只是等號比較運算子，不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="b9b68-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="b9b68-132">字串串連運算子 (`&`) 不是算術運算子，但它分組搭配算術運算子的優先順序。</span><span class="sxs-lookup"><span data-stu-id="b9b68-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="b9b68-133">`Is`和`IsNot`運算子都是物件參考的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="b9b68-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="b9b68-134">不會比較兩個物件的值他們檢查只是用來判斷兩個物件變數是否參考相同的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="b9b68-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="b9b68-135">順序關聯性</span><span class="sxs-lookup"><span data-stu-id="b9b68-135">Associativity</span></span>  
 <span data-ttu-id="b9b68-136">相同優先順序的運算子一起出現在運算式中，例如乘法與除法，編譯器會評估為遇到它從左到右每一項作業。</span><span class="sxs-lookup"><span data-stu-id="b9b68-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="b9b68-137">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="b9b68-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="b9b68-138">第一個運算式會評估除法 96 / 8 （這會產生 12），然後除法 12 / 4，這會產生三個。</span><span class="sxs-lookup"><span data-stu-id="b9b68-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="b9b68-139">因為編譯器會評估為作業`n1`從左到右，評估時，相同的明確指定該順序`n2`。</span><span class="sxs-lookup"><span data-stu-id="b9b68-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="b9b68-140">同時`n1`和`n2`有三個結果。</span><span class="sxs-lookup"><span data-stu-id="b9b68-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="b9b68-141">相反地，`n3`的結果是 48，因為括號會強制編譯器將評估 8 / 4 第一次。</span><span class="sxs-lookup"><span data-stu-id="b9b68-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="b9b68-142">基於此行為，運算子可視為是*左向關聯*在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="b9b68-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="b9b68-143">覆寫優先順序和關聯性</span><span class="sxs-lookup"><span data-stu-id="b9b68-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="b9b68-144">您可以使用括號強制其他項目之前，在評估運算式的某些部分。</span><span class="sxs-lookup"><span data-stu-id="b9b68-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="b9b68-145">優先順序和左順序關聯性，也可以覆寫。</span><span class="sxs-lookup"><span data-stu-id="b9b68-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="b9b68-146">Visual Basic 一定會執行之前以外的括號括住的作業。</span><span class="sxs-lookup"><span data-stu-id="b9b68-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="b9b68-147">不過，在括號，它仍保留一般優先順序和關聯性，除非您使用括號括號內。</span><span class="sxs-lookup"><span data-stu-id="b9b68-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="b9b68-148">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="b9b68-148">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b9b68-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b68-149">See Also</span></span>  
 [<span data-ttu-id="b9b68-150">= 運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [<span data-ttu-id="b9b68-151">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="b9b68-152">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="b9b68-153">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="b9b68-154">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="b9b68-155">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="b9b68-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="b9b68-156">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="b9b68-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="b9b68-157">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="b9b68-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
