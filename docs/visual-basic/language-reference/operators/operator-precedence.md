---
title: 運算子優先順序
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
ms.openlocfilehash: eef6314f5fc1f5a7fffa7997559f697130f6f755
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401442"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="c59fb-102">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="c59fb-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="c59fb-103">當運算式中發生數個作業時，每個元件都會以預先決定的順序（稱為*運算子優先順序*）進行評估和解析。</span><span class="sxs-lookup"><span data-stu-id="c59fb-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="c59fb-104">優先順序規則</span><span class="sxs-lookup"><span data-stu-id="c59fb-104">Precedence Rules</span></span>
 <span data-ttu-id="c59fb-105">當運算式包含來自多個類別的運算子時，會根據下列規則進行評估：</span><span class="sxs-lookup"><span data-stu-id="c59fb-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="c59fb-106">算術和串連運算子具有下一節所描述的優先順序順序，而且所有的優先順序高於比較、邏輯和位運算子。</span><span class="sxs-lookup"><span data-stu-id="c59fb-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="c59fb-107">所有比較運算子都具有相同的優先順序，而且所有的優先順序高於邏輯和位運算子，但較低的優先順序高於算術和串連運算子。</span><span class="sxs-lookup"><span data-stu-id="c59fb-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="c59fb-108">邏輯和位運算子具有下一節所描述的優先順序順序，而且所有的優先順序都低於算術、串連和比較運算子。</span><span class="sxs-lookup"><span data-stu-id="c59fb-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="c59fb-109">具有相等優先順序的運算子會依其在運算式中出現的順序向右評估。</span><span class="sxs-lookup"><span data-stu-id="c59fb-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="c59fb-110">優先順序</span><span class="sxs-lookup"><span data-stu-id="c59fb-110">Precedence Order</span></span>
 <span data-ttu-id="c59fb-111">運算子會依照下列優先順序來進行評估：</span><span class="sxs-lookup"><span data-stu-id="c59fb-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="c59fb-112">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-112">Await Operator</span></span>
 <span data-ttu-id="c59fb-113">遇到</span><span class="sxs-lookup"><span data-stu-id="c59fb-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="c59fb-114">算術和串連運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-114">Arithmetic and Concatenation Operators</span></span>
 <span data-ttu-id="c59fb-115">乘冪（ `^` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="c59fb-116">一元識別和否定（ `+` ， `–` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="c59fb-117">乘法和浮點除法（ `*` ， `/` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="c59fb-118">整數除法（ `\` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-118">Integer division (`\`)</span></span>

 <span data-ttu-id="c59fb-119">模組化算術（ `Mod` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="c59fb-120">加法和減法（ `+` ， `–` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="c59fb-121">字串串連（ `&` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="c59fb-122">算術位移位（ `<<` ， `>>` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="c59fb-123">比較運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-123">Comparison Operators</span></span>
 <span data-ttu-id="c59fb-124">所有比較運算子（ `=` 、 `<>` 、 `<` 、 `<=` 、、、、、 `>` `>=` `Is` `IsNot` `Like` 、 `TypeOf` ... `Is` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="c59fb-125">邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-125">Logical and Bitwise Operators</span></span>
 <span data-ttu-id="c59fb-126">否定（ `Not` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-126">Negation (`Not`)</span></span>

 <span data-ttu-id="c59fb-127">結合（ `And` 、 `AndAlso` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="c59fb-128">內含析取（ `Or` ， `OrElse` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="c59fb-129">獨佔分離（ `Xor` ）</span><span class="sxs-lookup"><span data-stu-id="c59fb-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="c59fb-130">註解</span><span class="sxs-lookup"><span data-stu-id="c59fb-130">Comments</span></span>
 <span data-ttu-id="c59fb-131">`=`運算子只是相等比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="c59fb-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="c59fb-132">字串串連運算子（ `&` ）不是算術運算子，但優先順序會與算術運算子群組在一起。</span><span class="sxs-lookup"><span data-stu-id="c59fb-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="c59fb-133">`Is`和 `IsNot` 運算子是物件參考比較運算子。</span><span class="sxs-lookup"><span data-stu-id="c59fb-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="c59fb-134">它們不會比較兩個物件的值。它們只會檢查以判斷兩個物件變數是否參考相同的物件實例。</span><span class="sxs-lookup"><span data-stu-id="c59fb-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="c59fb-135">關聯性</span><span class="sxs-lookup"><span data-stu-id="c59fb-135">Associativity</span></span>
 <span data-ttu-id="c59fb-136">當相等優先順序的運算子同時出現在運算式中時（例如乘法和除法），編譯器會在每個作業從左至右遇到時進行評估。</span><span class="sxs-lookup"><span data-stu-id="c59fb-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="c59fb-137">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="c59fb-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="c59fb-138">第一個運算式會評估除法 96/8 （這會產生12），然後是除法 12/4，這會產生三個。</span><span class="sxs-lookup"><span data-stu-id="c59fb-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="c59fb-139">因為編譯器 `n1` 會從左至右評估的作業，所以當明確指出該順序時，評估會是相同的 `n2` 。</span><span class="sxs-lookup"><span data-stu-id="c59fb-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="c59fb-140">`n1`和都 `n2` 有三個結果。</span><span class="sxs-lookup"><span data-stu-id="c59fb-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="c59fb-141">相反地，的 `n3` 結果為48，因為括弧會強制編譯器先評估 8/4。</span><span class="sxs-lookup"><span data-stu-id="c59fb-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="c59fb-142">基於此行為，運算子稱為 Visual Basic 中的*左關聯*。</span><span class="sxs-lookup"><span data-stu-id="c59fb-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="c59fb-143">覆寫優先順序和關聯性</span><span class="sxs-lookup"><span data-stu-id="c59fb-143">Overriding Precedence and Associativity</span></span>
 <span data-ttu-id="c59fb-144">您可以使用括弧來強制評估運算式的某些部分。</span><span class="sxs-lookup"><span data-stu-id="c59fb-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="c59fb-145">這可能會覆寫優先順序和左側關聯性的順序。</span><span class="sxs-lookup"><span data-stu-id="c59fb-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="c59fb-146">Visual Basic 一律會執行以括弧括住的作業，而不是在外部。</span><span class="sxs-lookup"><span data-stu-id="c59fb-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="c59fb-147">不過，在括弧內，除非您在括弧內使用括弧，否則會維持一般優先順序和關聯性。</span><span class="sxs-lookup"><span data-stu-id="c59fb-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="c59fb-148">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="c59fb-148">The following example illustrates this.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="c59fb-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c59fb-149">See also</span></span>

- [<span data-ttu-id="c59fb-150">= 運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-150">= Operator</span></span>](assignment-operator.md)
- [<span data-ttu-id="c59fb-151">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-151">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="c59fb-152">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-152">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="c59fb-153">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-153">Like Operator</span></span>](like-operator.md)
- [<span data-ttu-id="c59fb-154">TypeOf 運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-154">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="c59fb-155">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-155">Await Operator</span></span>](await-operator.md)
- [<span data-ttu-id="c59fb-156">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="c59fb-156">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="c59fb-157">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="c59fb-157">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
