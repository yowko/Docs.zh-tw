---
title: "在 Visual Basic 中的運算子優先順序 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- arithmetic operators, precedence
- operator precedence
- logical operators, precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators
- operators [Visual Basic], precedence
- precedence, of operators
- comparison operators, precedence
- math operators
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
caps.latest.revision: 18
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f653dd83c9778dddfe0e52db27065f7d73866e37
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="7b6a3-102">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="7b6a3-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="7b6a3-103">每個部分數個作業發生時在運算式中，評估並解決在預先定義的順序呼叫*運算子優先順序*。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>  
  
## <a name="precedence-rules"></a><span data-ttu-id="7b6a3-104">優先順序規則</span><span class="sxs-lookup"><span data-stu-id="7b6a3-104">Precedence Rules</span></span>  
 <span data-ttu-id="7b6a3-105">當運算式包含運算子，從多個類別時，會評估根據下列規則︰</span><span class="sxs-lookup"><span data-stu-id="7b6a3-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>  
  
-   <span data-ttu-id="7b6a3-106">算術和串連運算子有下列的一節所述的優先順序，而且全都有更高的優先順序高於比較、 邏輯和位元運算子。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>  
  
-   <span data-ttu-id="7b6a3-107">所有比較運算子優先順序都都相同，且只需要較高的優先順序高於邏輯和位元運算子，但低於算術和串連運算子。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>  
  
-   <span data-ttu-id="7b6a3-108">邏輯和位元運算子有下列的一節所述的優先順序，而且全都有較低的優先順序高於算術、 串連運算子和比較運算子。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>  
  
-   <span data-ttu-id="7b6a3-109">具有相同優先順序的運算子會向左到右評估運算式中出現的順序。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>  
  
## <a name="precedence-order"></a><span data-ttu-id="7b6a3-110">優先順序</span><span class="sxs-lookup"><span data-stu-id="7b6a3-110">Precedence Order</span></span>  
 <span data-ttu-id="7b6a3-111">運算子會依下列優先順序進行評估︰</span><span class="sxs-lookup"><span data-stu-id="7b6a3-111">Operators are evaluated in the following order of precedence:</span></span>  
  
### <a name="await-operator"></a><span data-ttu-id="7b6a3-112">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="7b6a3-112">Await Operator</span></span>  
 <span data-ttu-id="7b6a3-113">Await</span><span class="sxs-lookup"><span data-stu-id="7b6a3-113">Await</span></span>  
  
### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="7b6a3-114">算術和串連運算子</span><span class="sxs-lookup"><span data-stu-id="7b6a3-114">Arithmetic and Concatenation Operators</span></span>  
 <span data-ttu-id="7b6a3-115">乘冪 (`^`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-115">Exponentiation (`^`)</span></span>  
  
 <span data-ttu-id="7b6a3-116">一元識別和否定 (`+`， `–`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-116">Unary identity and negation (`+`, `–`)</span></span>  
  
 <span data-ttu-id="7b6a3-117">乘法和除法浮點數 (`*`， `/`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-117">Multiplication and floating-point division (`*`, `/`)</span></span>  
  
 <span data-ttu-id="7b6a3-118">整數除法 (`\`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-118">Integer division (`\`)</span></span>  
  
 <span data-ttu-id="7b6a3-119">模數算術 (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-119">Modulus arithmetic (`Mod`)</span></span>  
  
 <span data-ttu-id="7b6a3-120">加法和減法 (`+`， `–`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-120">Addition and subtraction (`+`, `–`)</span></span>  
  
 <span data-ttu-id="7b6a3-121">字串串連 (`&`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-121">String concatenation (`&`)</span></span>  
  
 <span data-ttu-id="7b6a3-122">算術的位元移位 (`<<`， `>>`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-122">Arithmetic bit shift (`<<`, `>>`)</span></span>  
  
### <a name="comparison-operators"></a><span data-ttu-id="7b6a3-123">比較運算子</span><span class="sxs-lookup"><span data-stu-id="7b6a3-123">Comparison Operators</span></span>  
 <span data-ttu-id="7b6a3-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>  
  
### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="7b6a3-125">邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="7b6a3-125">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="7b6a3-126">否定 (`Not`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-126">Negation (`Not`)</span></span>  
  
 <span data-ttu-id="7b6a3-127">搭配使用 (`And`， `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-127">Conjunction (`And`, `AndAlso`)</span></span>  
  
 <span data-ttu-id="7b6a3-128">內含分離 (`Or`， `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>  
  
 <span data-ttu-id="7b6a3-129">排除分離 (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-129">Exclusive disjunction (`Xor`)</span></span>  
  
### <a name="comments"></a><span data-ttu-id="7b6a3-130">註解</span><span class="sxs-lookup"><span data-stu-id="7b6a3-130">Comments</span></span>  
 <span data-ttu-id="7b6a3-131">`=`運算子只是等號比較運算子，指派運算子。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="7b6a3-132">字串串連運算子 (`&`) 不是算術運算子，但它分組搭配算術運算子的優先順序。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>  
  
 <span data-ttu-id="7b6a3-133">`Is`和`IsNot`運算子是物件參考的比較運算子。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="7b6a3-134">它們不會比較兩個物件的值這些檢查只是為了確定是否兩個物件變數參考相同物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>  
  
## <a name="associativity"></a><span data-ttu-id="7b6a3-135">順序關聯性</span><span class="sxs-lookup"><span data-stu-id="7b6a3-135">Associativity</span></span>  
 <span data-ttu-id="7b6a3-136">相同優先順序的運算子一起出現在運算式中，例如乘法與除法，編譯器會評估為遇到它從左到右每項作業。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="7b6a3-137">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-137">The following example illustrates this.</span></span>  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 <span data-ttu-id="7b6a3-138">第一個運算式會評估除法 96 / 8 （這會產生 12），然後除法 12 / 4，這會產生三個。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="7b6a3-139">因為編譯器會判斷值為作業`n1`從左到右，評估時，相同的明確指定該順序`n2`。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="7b6a3-140">同時`n1`和`n2`有三個結果。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="7b6a3-141">相較之下，`n3`的結果是 48，因為括號會強制編譯器將評估 8 / 4 第一次。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>  
  
 <span data-ttu-id="7b6a3-142">基於此行為，運算子可以說是*左向*中[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-142">Because of this behavior, operators are said to be *left associative* in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="7b6a3-143">覆寫優先順序和順序關聯性</span><span class="sxs-lookup"><span data-stu-id="7b6a3-143">Overriding Precedence and Associativity</span></span>  
 <span data-ttu-id="7b6a3-144">您可以使用括號強制優先評估運算式的某些部分。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="7b6a3-145">優先順序和左順序關聯性，也可以覆寫。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-145">This can override both the order of precedence and the left associativity.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="7b6a3-146">永遠執行之前以外的括號括住的作業。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-146"> always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="7b6a3-147">不過，在括號括住，它會維護一般優先順序和關聯性，除非您使用括號括號內。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="7b6a3-148">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="7b6a3-148">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7b6a3-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b6a3-149">See Also</span></span>  
 <span data-ttu-id="7b6a3-150">[= 運算子](../../../visual-basic/language-reference/operators/assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7b6a3-150">[= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) </span></span>  
<span data-ttu-id="7b6a3-151"> [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7b6a3-151"> [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="7b6a3-152"> [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7b6a3-152"> [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md) </span></span>  
<span data-ttu-id="7b6a3-153"> [Like 運算子](../../../visual-basic/language-reference/operators/like-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7b6a3-153"> [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md) </span></span>  
<span data-ttu-id="7b6a3-154"> [TypeOf 運算子](../../../visual-basic/language-reference/operators/typeof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7b6a3-154"> [TypeOf Operator](../../../visual-basic/language-reference/operators/typeof-operator.md) </span></span>  
<span data-ttu-id="7b6a3-155"> [Await 運算子](../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7b6a3-155"> [Await Operator](../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="7b6a3-156"> [依功能排列的運算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="7b6a3-156"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="7b6a3-157"> [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span><span class="sxs-lookup"><span data-stu-id="7b6a3-157"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)</span></span>
