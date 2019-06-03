---
title: 運算子 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 60e7f7c25b525c6db856731bd16c1c0e60efe6d6
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422934"
---
# <a name="operators-c-programming-guide"></a><span data-ttu-id="e9dc8-102">運算子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e9dc8-102">Operators (C# Programming Guide)</span></span>

<span data-ttu-id="e9dc8-103">在 C# 中，「 *運算子* 」(Operator) 是程式的元素，這類元素會套用至運算式或陳述式中的一個或多個「 *運算元* 」(Operand)。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-103">In C#, an *operator* is a program element that is applied to one or more *operands* in an expression or statement.</span></span> <span data-ttu-id="e9dc8-104">只使用一個運算元的運算子稱為`++`「一元」 `new`(Unary) 運算子，例如遞增運算子 ( *) 或* 。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-104">Operators that take one operand, such as the increment operator (`++`) or `new`, are referred to as *unary* operators.</span></span> <span data-ttu-id="e9dc8-105">使用兩個運算元的運算子稱為`+`「二元」`-`(Binary) 運算子，例如算術運算子 (`*`、`/`、 *及* )。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-105">Operators that take two operands, such as arithmetic operators (`+`,`-`,`*`,`/`), are referred to as *binary* operators.</span></span> <span data-ttu-id="e9dc8-106">還有一種運算子稱為條件運算子 (`?:`)，它會使用三個運算元而且是 C# 中唯一的三元運算子。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-106">One operator, the conditional operator (`?:`), takes three operands and is the sole ternary operator in C#.</span></span>  
  
 <span data-ttu-id="e9dc8-107">下列 C# 陳述式包含一個一元運算子和一個運算元。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-107">The following C# statement contains a single unary operator and a single operand.</span></span> <span data-ttu-id="e9dc8-108">遞增運算子 `++`會修改運算元 `y`的值。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-108">The increment operator, `++`, modifies the value of the operand `y`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 <span data-ttu-id="e9dc8-109">下列 C# 陳述式包含兩個二元運算子，這兩個運算子各有兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-109">The following C# statement contains two binary operators, each with two operands.</span></span> <span data-ttu-id="e9dc8-110">指派運算子 `=`的運算元為整數變數 `y` 和運算式 `2 + 3` 。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-110">The assignment operator, `=`, has the integer variable `y` and the expression `2 + 3` as operands.</span></span> <span data-ttu-id="e9dc8-111">運算式 `2 + 3` 本身包含加法運算子和兩個運算元 `2` 和 `3`。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-111">The expression `2 + 3` itself consists of the addition operator and two operands, `2` and `3`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
<span data-ttu-id="e9dc8-112">運算元可以是由任何長度的程式碼撰寫而成的有效運算式，而且可以包含任何數量的子運算式。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-112">An operand can be a valid expression that is composed of any length of code, and it can comprise any number of sub expressions.</span></span> <span data-ttu-id="e9dc8-113">在包含多個運算子的運算式中，套用運算子的順序取決於「 *運算子優先順序*」(Operator Precedence)、「 *順序關聯性*」(Associativity) 以及括號。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-113">In an expression that contains multiple operators, the order in which the operators are applied is determined by *operator precedence*, *associativity*, and parentheses.</span></span>  

## <a name="operator-precedence"></a><span data-ttu-id="e9dc8-114">運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="e9dc8-114">Operator precedence</span></span>
  
<span data-ttu-id="e9dc8-115">每個運算子都有定義的優先順序。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-115">Each operator has a defined precedence.</span></span> <span data-ttu-id="e9dc8-116">在包含多個運算子且運算子具有不同優先順序層級的運算式中，運算子的優先順序決定評估運算子的順序。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-116">In an expression that contains multiple operators that have different precedence levels, the precedence of the operators determines the order in which the operators are evaluated.</span></span> <span data-ttu-id="e9dc8-117">例如，下列陳述式會將 3 指派給 `n1`：</span><span class="sxs-lookup"><span data-stu-id="e9dc8-117">For example, the following statement assigns 3 to `n1`:</span></span>

```csharp
n1 = 11 - 2 * 4;
```

<span data-ttu-id="e9dc8-118">因為乘法的優先順序高於減法，所以會先執行乘法。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-118">The multiplication is executed first because multiplication takes precedence over subtraction.</span></span>

<span data-ttu-id="e9dc8-119">如需按優先順序層級排序的 C# 運算子完整清單，請參閱 [C# 運算子](../../language-reference/operators/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-119">For the complete list of C# operators ordered by precedence level, see [C# operators](../../language-reference/operators/index.md).</span></span>
  
## <a name="associativity"></a><span data-ttu-id="e9dc8-120">順序關聯性</span><span class="sxs-lookup"><span data-stu-id="e9dc8-120">Associativity</span></span>

 <span data-ttu-id="e9dc8-121">當運算式中有兩個以上具有相同優先順序的運算子時，會根據順序關聯性評估這些運算子。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-121">When two or more operators that have the same precedence are present in an expression, they are evaluated based on associativity.</span></span> <span data-ttu-id="e9dc8-122">左向關聯運算子會依由左至右的順序進行評估。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-122">Left-associative operators are evaluated in order from left to right.</span></span> <span data-ttu-id="e9dc8-123">例如， `x * y / z` 會判斷值為 `(x * y) / z`。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-123">For example, `x * y / z` is evaluated as `(x * y) / z`.</span></span> <span data-ttu-id="e9dc8-124">右向關聯運算子會依由右至左的順序進行評估。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-124">Right-associative operators are evaluated in order from right to left.</span></span> <span data-ttu-id="e9dc8-125">例如，指派運算子就是右向關聯。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-125">For example, the assignment operator is right associative.</span></span> <span data-ttu-id="e9dc8-126">如果不是的話，下列程式碼將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-126">If it were not, the following code would result in an error.</span></span>  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 <span data-ttu-id="e9dc8-127">另一個範例是右向關聯的三元運算子 ([?:](../../../csharp/language-reference/operators/conditional-operator.md))。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-127">As another example the ternary operator ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) is right associative.</span></span> <span data-ttu-id="e9dc8-128">大部分的二元運算子都是左向關聯。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-128">Most binary operators are left associative.</span></span>  
  
 <span data-ttu-id="e9dc8-129">不論運算式中的運算子是左向關聯還是右向關聯，都會由左至右先行評估每個運算式的運算元。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-129">Whether the operators in an expression are left associative or right associative, the operands of each expression are evaluated first, from left to right.</span></span> <span data-ttu-id="e9dc8-130">下列範例將說明運算子和運算元的評估順序。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-130">The following examples illustrate the order of evaluation of operators and operands.</span></span>  
  
|<span data-ttu-id="e9dc8-131">陳述式</span><span class="sxs-lookup"><span data-stu-id="e9dc8-131">Statement</span></span>|<span data-ttu-id="e9dc8-132">評估的順序</span><span class="sxs-lookup"><span data-stu-id="e9dc8-132">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = b`|<span data-ttu-id="e9dc8-133">a, b, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-133">a, b, =</span></span>|  
|`a = b + c`|<span data-ttu-id="e9dc8-134">a, b, c, +, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-134">a, b, c, +, =</span></span>|  
|`a = b + c * d`|<span data-ttu-id="e9dc8-135">a, b, c, d, \*, +, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-135">a, b, c, d, \*, +, =</span></span>|  
|`a = b * c + d`|<span data-ttu-id="e9dc8-136">a, b, c, \*, d, +, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-136">a, b, c, \*, d, +, =</span></span>|  
|`a = b - c + d`|<span data-ttu-id="e9dc8-137">a, b, c, -, d, +, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-137">a, b, c, -, d, +, =</span></span>|  
|`a += b -= c`|<span data-ttu-id="e9dc8-138">a, b, c, -=, +=</span><span class="sxs-lookup"><span data-stu-id="e9dc8-138">a, b, c, -=, +=</span></span>|  
  
## <a name="adding-parentheses"></a><span data-ttu-id="e9dc8-139">加入括號</span><span class="sxs-lookup"><span data-stu-id="e9dc8-139">Adding parentheses</span></span>

 <span data-ttu-id="e9dc8-140">您可以使用括號變更運算子優先順序和順序關聯性強制執行的順序。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-140">You can change the order imposed by operator precedence and associativity by using parentheses.</span></span> <span data-ttu-id="e9dc8-141">例如， `2 + 3 * 2` 正常情況下會判斷值為 8，這是因為乘法類運算子的優先順序高於加法類運算子。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-141">For example, `2 + 3 * 2` ordinarily evaluates to 8, because multiplicative operators take precedence over additive operators.</span></span> <span data-ttu-id="e9dc8-142">但是，如果您將運算式撰寫為 `(2 + 3) * 2`，則會先評估加法再評估乘法，而得到的結果會是 10。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-142">However, if you write the expression as `(2 + 3) * 2`, the addition is evaluated before the multiplication, and the result is 10.</span></span> <span data-ttu-id="e9dc8-143">下列範例將說明以括號括住之運算式中的評估順序。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-143">The following examples illustrate the order of evaluation in parenthesized expressions.</span></span> <span data-ttu-id="e9dc8-144">如先範例所示，套用運算子之前會先評估運算元。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-144">As in previous examples, the operands are evaluated before the operator is applied.</span></span>  
  
|<span data-ttu-id="e9dc8-145">陳述式</span><span class="sxs-lookup"><span data-stu-id="e9dc8-145">Statement</span></span>|<span data-ttu-id="e9dc8-146">評估的順序</span><span class="sxs-lookup"><span data-stu-id="e9dc8-146">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = (b + c) * d`|<span data-ttu-id="e9dc8-147">a, b, c, +, d, \*, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-147">a, b, c, +, d, \*, =</span></span>|  
|`a = b - (c + d)`|<span data-ttu-id="e9dc8-148">a, b, c, d, +, -, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-148">a, b, c, d, +, -, =</span></span>|  
|`a = (b + c) * (d - e)`|<span data-ttu-id="e9dc8-149">a, b, c, +, d, e, -, \*, =</span><span class="sxs-lookup"><span data-stu-id="e9dc8-149">a, b, c, +, d, e, -, \*, =</span></span>|  
  
## <a name="operator-overloading"></a><span data-ttu-id="e9dc8-150">運算子多載</span><span class="sxs-lookup"><span data-stu-id="e9dc8-150">Operator overloading</span></span>

<span data-ttu-id="e9dc8-151">您可以定義自訂類別和結構的某些運算子行為。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-151">You can define the behavior of certain operators for custom classes and structs.</span></span> <span data-ttu-id="e9dc8-152">這個程序稱為「 *運算子多載*」(Operator Overloading)。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-152">This process is referred to as *operator overloading*.</span></span> <span data-ttu-id="e9dc8-153">如需詳細資訊，請參閱[多載運算子](overloadable-operators.md)和 [operator](../../language-reference/keywords/operator.md) 關鍵字文章。</span><span class="sxs-lookup"><span data-stu-id="e9dc8-153">For more information, see [Overloadable operators](overloadable-operators.md) and the [operator](../../language-reference/keywords/operator.md) keyword article.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e9dc8-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9dc8-154">See also</span></span>

- [<span data-ttu-id="e9dc8-155">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e9dc8-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e9dc8-156">陳述式、運算式和運算子</span><span class="sxs-lookup"><span data-stu-id="e9dc8-156">Statements, Expressions, and Operators</span></span>](index.md)
- [<span data-ttu-id="e9dc8-157">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="e9dc8-157">C# Operators</span></span>](../../language-reference/operators/index.md)
