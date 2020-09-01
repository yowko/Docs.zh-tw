---
description: => 運算子 - C# 參考
title: => 運算子 - C# 參考
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 6a4df3a4bd358b87f98ff1bd5a3f624b1029a73b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128357"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a0a17-103">=> 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a0a17-103">=> operator (C# reference)</span></span>

<span data-ttu-id="a0a17-104">`=>`標記的支援方式有兩種：做為[Lambda 運算子](#lambda-operator)，以及做為成員名稱和[運算式主體定義](#expression-body-definition)中成員實作為分隔符號的形式。</span><span class="sxs-lookup"><span data-stu-id="a0a17-104">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="a0a17-105">Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="a0a17-105">Lambda operator</span></span>

<span data-ttu-id="a0a17-106">在 [lambda 運算式](lambda-expressions.md)中，Lambda 運算子會將 `=>` 左側的輸入參數與右邊的 lambda 主體分隔開來。</span><span class="sxs-lookup"><span data-stu-id="a0a17-106">In [lambda expressions](lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="a0a17-107">下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：</span><span class="sxs-lookup"><span data-stu-id="a0a17-107">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="a0a17-108">Lambda 運算式的輸入參數在編譯時期是強型別。</span><span class="sxs-lookup"><span data-stu-id="a0a17-108">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="a0a17-109">當編譯器可以推斷輸入參數的類型時（如上述範例所示），您可能會省略類型宣告。</span><span class="sxs-lookup"><span data-stu-id="a0a17-109">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="a0a17-110">如果您需要指定輸入參數的類型，您必須針對每個參數執行此動作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a0a17-110">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="a0a17-111">下列範例顯示如何定義沒有輸入參數的 lambda 運算式：</span><span class="sxs-lookup"><span data-stu-id="a0a17-111">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="a0a17-112">如需詳細資訊，請參閱 [Lambda 運算式](lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a17-112">For more information, see [Lambda expressions](lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="a0a17-113">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="a0a17-113">Expression body definition</span></span>

<span data-ttu-id="a0a17-114">運算式主體定義的一般語法如下︰</span><span class="sxs-lookup"><span data-stu-id="a0a17-114">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="a0a17-115">其中 `expression` 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="a0a17-115">where `expression` is a valid expression.</span></span> <span data-ttu-id="a0a17-116">`expression` 的傳回型別必須可以隱含地轉換為成員的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="a0a17-116">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="a0a17-117">如果成員的傳回型別是 `void` ，或是如果成員是一個函式、完成項或屬性或索引子 `set` 存取子，則 `expression` 必須是 [*語句運算式*](~/_csharplang/spec/statements.md#expression-statements)。</span><span class="sxs-lookup"><span data-stu-id="a0a17-117">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property or indexer `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements).</span></span> <span data-ttu-id="a0a17-118">因為會捨棄運算式的結果，所以該運算式的傳回型別可以是任何型別。</span><span class="sxs-lookup"><span data-stu-id="a0a17-118">Because the expression's result is discarded, the return type of that expression can be any type.</span></span>

<span data-ttu-id="a0a17-119">下列範例顯示 `Person.ToString` 方法的運算式主體定義：</span><span class="sxs-lookup"><span data-stu-id="a0a17-119">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="a0a17-120">它是下列方法定義的簡短版：</span><span class="sxs-lookup"><span data-stu-id="a0a17-120">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="a0a17-121">從 c # 6 開始支援方法、運算子和唯讀屬性的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="a0a17-121">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="a0a17-122">從 c # 7.0 開始支援函式、完成項和屬性和索引子存取子的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="a0a17-122">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="a0a17-123">如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a17-123">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a0a17-124">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="a0a17-124">Operator overloadability</span></span>

<span data-ttu-id="a0a17-125">無法多載 `=>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="a0a17-125">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a0a17-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a0a17-126">C# language specification</span></span>

<span data-ttu-id="a0a17-127">如需 Lambda 運算子的詳細資訊，請參閱[c # 語言規格](~/_csharplang/spec/introduction.md)的「[匿名函數運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)」一節。</span><span class="sxs-lookup"><span data-stu-id="a0a17-127">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0a17-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0a17-128">See also</span></span>

- [<span data-ttu-id="a0a17-129">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="a0a17-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a0a17-130">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="a0a17-130">C# operators and expressions</span></span>](index.md)
