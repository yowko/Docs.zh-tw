---
title: => 運算子 - C# 參考
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b72b058c1709e7a643a70233cc3289d5d9165ca4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916804"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ee501-102">=> 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ee501-102">=> operator (C# reference)</span></span>

<span data-ttu-id="ee501-103">`=>`標記的支援方式有兩種：做為[Lambda 運算子](#lambda-operator)，以及[運算式主體定義](#expression-body-definition)中成員名稱和成員實作為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="ee501-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="ee501-104">Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="ee501-104">Lambda operator</span></span>

<span data-ttu-id="ee501-105">在[lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)中，Lambda 運算子會將 `=>` 左側的輸入參數與右側的 lambda 主體隔開。</span><span class="sxs-lookup"><span data-stu-id="ee501-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="ee501-106">下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：</span><span class="sxs-lookup"><span data-stu-id="ee501-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="ee501-107">Lambda 運算式的輸入參數是在編譯時期的強型別。</span><span class="sxs-lookup"><span data-stu-id="ee501-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="ee501-108">當編譯器可以推斷輸入參數的類型（如上述範例所示）時，您可能會省略類型宣告。</span><span class="sxs-lookup"><span data-stu-id="ee501-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="ee501-109">如果您需要指定輸入參數的類型，您必須針對每個參數執行此動作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ee501-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="ee501-110">下列範例顯示如何定義不含輸入參數的 lambda 運算式：</span><span class="sxs-lookup"><span data-stu-id="ee501-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="ee501-111">如需詳細資訊，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ee501-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="ee501-112">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="ee501-112">Expression body definition</span></span>

<span data-ttu-id="ee501-113">運算式主體定義的一般語法如下︰</span><span class="sxs-lookup"><span data-stu-id="ee501-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="ee501-114">其中 `expression` 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="ee501-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="ee501-115">`expression` 的傳回型別必須可以隱含地轉換為成員的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="ee501-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="ee501-116">如果成員的傳回型別是 `void` ，或者如果成員是一個函式、完成項或屬性或索引子 `set` 存取子，則 `expression` 必須是[*語句運算式*](~/_csharplang/spec/statements.md#expression-statements)。</span><span class="sxs-lookup"><span data-stu-id="ee501-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property or indexer `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements).</span></span> <span data-ttu-id="ee501-117">由於運算式的結果會被捨棄，因此該運算式的傳回類型可以是任何類型。</span><span class="sxs-lookup"><span data-stu-id="ee501-117">Because the expression's result is discarded, the return type of that expression can be any type.</span></span>

<span data-ttu-id="ee501-118">下列範例顯示 `Person.ToString` 方法的運算式主體定義：</span><span class="sxs-lookup"><span data-stu-id="ee501-118">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="ee501-119">它是下列方法定義的簡短版：</span><span class="sxs-lookup"><span data-stu-id="ee501-119">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="ee501-120">從 c # 6 開始支援方法、運算子和唯讀屬性的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="ee501-120">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="ee501-121">從 c # 7.0 開始支援函式、完成項和屬性和索引子存取子的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="ee501-121">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="ee501-122">如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="ee501-122">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ee501-123">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="ee501-123">Operator overloadability</span></span>

<span data-ttu-id="ee501-124">無法多載 `=>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="ee501-124">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ee501-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ee501-125">C# language specification</span></span>

<span data-ttu-id="ee501-126">如需 Lambda 運算子的詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的[匿名函數運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="ee501-126">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee501-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee501-127">See also</span></span>

- [<span data-ttu-id="ee501-128">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="ee501-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ee501-129">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="ee501-129">C# operators and expressions</span></span>](index.md)
