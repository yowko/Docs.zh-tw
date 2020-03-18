---
title: => 運算子 - C# 參考
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846245"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9d76b-102">=> 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9d76b-102">=> operator (C# reference)</span></span>

<span data-ttu-id="9d76b-103">權杖`=>`以兩種形式得到支援：作為[Lambda 運算子](#lambda-operator)，作為成員名稱的分隔符號和[運算式正文定義](#expression-body-definition)中的成員實現。</span><span class="sxs-lookup"><span data-stu-id="9d76b-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="9d76b-104">Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="9d76b-104">Lambda operator</span></span>

<span data-ttu-id="9d76b-105">在[lambda 運算式中](../../programming-guide/statements-expressions-operators/lambda-expressions.md)，lambda`=>`運算子將左側的輸入參數與右側的 lambda 主體分開。</span><span class="sxs-lookup"><span data-stu-id="9d76b-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="9d76b-106">下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：</span><span class="sxs-lookup"><span data-stu-id="9d76b-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="9d76b-107">lambda 運算式的輸入參數在編譯時進行強型別。</span><span class="sxs-lookup"><span data-stu-id="9d76b-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="9d76b-108">當編譯器可以推斷輸入參數的類型時（如前面的示例中所示）可以省略型別宣告。</span><span class="sxs-lookup"><span data-stu-id="9d76b-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="9d76b-109">如果需要指定輸入參數的類型，則必須為每個參數執行此操作，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="9d76b-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="9d76b-110">下面的示例演示如何定義沒有輸入參數的 lambda 運算式：</span><span class="sxs-lookup"><span data-stu-id="9d76b-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="9d76b-111">如需詳細資訊，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="9d76b-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="9d76b-112">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="9d76b-112">Expression body definition</span></span>

<span data-ttu-id="9d76b-113">運算式主體定義的一般語法如下︰</span><span class="sxs-lookup"><span data-stu-id="9d76b-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="9d76b-114">其中 `expression` 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="9d76b-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="9d76b-115">`expression` 的傳回型別必須可以隱含地轉換為成員的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9d76b-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="9d76b-116">如果成員的返回類型`void`是或成員是建構函式、終端子或屬性`set`訪問器，`expression`則必須是[*語句運算式*](~/_csharplang/spec/statements.md#expression-statements)，可以是任何類型的語句運算式。</span><span class="sxs-lookup"><span data-stu-id="9d76b-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements), which can be of any type.</span></span>

<span data-ttu-id="9d76b-117">下列範例顯示 `Person.ToString` 方法的運算式主體定義：</span><span class="sxs-lookup"><span data-stu-id="9d76b-117">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="9d76b-118">它是下列方法定義的簡短版：</span><span class="sxs-lookup"><span data-stu-id="9d76b-118">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="9d76b-119">從 C# 6 開始，支援方法、運算子和唯讀屬性的運算式正文定義。</span><span class="sxs-lookup"><span data-stu-id="9d76b-119">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="9d76b-120">支援建構函式、終端子、屬性和索引子訪問器的運算式正文定義，從 C# 7.0 開始。</span><span class="sxs-lookup"><span data-stu-id="9d76b-120">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="9d76b-121">如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="9d76b-121">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="9d76b-122">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="9d76b-122">Operator overloadability</span></span>

<span data-ttu-id="9d76b-123">無法多載 `=>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="9d76b-123">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9d76b-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="9d76b-124">C# language specification</span></span>

<span data-ttu-id="9d76b-125">有關 Lambda 運算子的詳細資訊，請參閱[C# 語言規範](~/_csharplang/spec/introduction.md)中的[匿名函數運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)部分。</span><span class="sxs-lookup"><span data-stu-id="9d76b-125">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d76b-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d76b-126">See also</span></span>

- [<span data-ttu-id="9d76b-127">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9d76b-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9d76b-128">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="9d76b-128">C# operators</span></span>](index.md)
