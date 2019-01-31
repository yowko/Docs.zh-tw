---
title: =&gt; 運算子 - C# 參考
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: fa2e149f5b19e80e3171d08519be3ae249d2a112
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540802"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="da36b-102">=&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="da36b-102">=&gt; operator (C# Reference)</span></span>

<span data-ttu-id="da36b-103">支援兩種形式的 `=>` 語彙基元：作為 Lambda 運算子，以及作為運算式主體定義中成員名稱和成員實作的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="da36b-103">The `=>` token is supported in two forms: as the lambda operator and as a separator of a member name and the member implementation in an expression body definition.</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="da36b-104">Lambda 運算子</span><span class="sxs-lookup"><span data-stu-id="da36b-104">Lambda operator</span></span>

<span data-ttu-id="da36b-105">在 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)中，Lambda 運算子 `=>` 會分開右邊的 Lambda 主體和左邊的輸入變數。</span><span class="sxs-lookup"><span data-stu-id="da36b-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input variables on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="da36b-106">下列範例使用 [LINQ](../../programming-guide/concepts/linq/index.md) 功能並搭配方法語法來示範 Lambda 運算式的使用方式：</span><span class="sxs-lookup"><span data-stu-id="da36b-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#InferredTypes)]

<span data-ttu-id="da36b-107">Lambda 運算式的輸入變數在編譯時間為強型別。</span><span class="sxs-lookup"><span data-stu-id="da36b-107">Input variables of lambda expressions are strongly typed at compile time.</span></span> <span data-ttu-id="da36b-108">當編譯器可以推斷輸入變數的類型時 (如上述範例所示)，您可以省略型別宣告。</span><span class="sxs-lookup"><span data-stu-id="da36b-108">When the compiler can infer the types of input variables, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="da36b-109">如果您需要指定輸入變數的類型，您必須針對每個變數執行，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="da36b-109">If you need to specify the type of input variables, you must do that for each variable, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#ExplicitTypes)]

<span data-ttu-id="da36b-110">下列範例示範如何定義 Lambda 運算式而不需要輸入變數：</span><span class="sxs-lookup"><span data-stu-id="da36b-110">The following example shows how to define a lambda expression without input variables:</span></span>

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#WithoutInput)]

<span data-ttu-id="da36b-111">如需詳細資訊，請參閱 [Lambda 運算式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="da36b-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="da36b-112">運算式主體定義</span><span class="sxs-lookup"><span data-stu-id="da36b-112">Expression body definition</span></span>

<span data-ttu-id="da36b-113">運算式主體定義的一般語法如下︰</span><span class="sxs-lookup"><span data-stu-id="da36b-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="da36b-114">其中 *expression* 是有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="da36b-114">where *expression* is a valid expression.</span></span> <span data-ttu-id="da36b-115">請注意，只有在成員的傳回型別為 `void` 時，或成員為建構函式、完成項或屬性 `set` 存取子時，*expression* 才可以是「陳述式運算式」。</span><span class="sxs-lookup"><span data-stu-id="da36b-115">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor, a finalizer, or a property `set` accessor.</span></span>

<span data-ttu-id="da36b-116">下列範例顯示 `Person.ToString` 方法的運算式主體定義：</span><span class="sxs-lookup"><span data-stu-id="da36b-116">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="da36b-117">它是下列方法定義的簡短版：</span><span class="sxs-lookup"><span data-stu-id="da36b-117">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="da36b-118">從 C# 6 開始支援方法和唯讀屬性的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="da36b-118">Expression body definitions for methods and read-only properties are supported starting with C# 6.</span></span> <span data-ttu-id="da36b-119">從 C# 7.0 開始支援建構函式、完成項、屬性存取子和索引子的運算式主體定義。</span><span class="sxs-lookup"><span data-stu-id="da36b-119">Expression body definitions for constructors, finalizers, property accessors, and indexers are supported starting with C# 7.0.</span></span>

<span data-ttu-id="da36b-120">如需詳細資訊，請參閱[運算式主體成員](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="da36b-120">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="da36b-121">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="da36b-121">Operator overloadability</span></span>

<span data-ttu-id="da36b-122">無法多載 `=>` 運算子。</span><span class="sxs-lookup"><span data-stu-id="da36b-122">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="da36b-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="da36b-123">C# language specification</span></span>

<span data-ttu-id="da36b-124">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[匿名函式運算式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)一節。</span><span class="sxs-lookup"><span data-stu-id="da36b-124">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da36b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da36b-125">See also</span></span>

- [<span data-ttu-id="da36b-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="da36b-126">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="da36b-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="da36b-127">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="da36b-128">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="da36b-128">C# Operators</span></span>](index.md)
- [<span data-ttu-id="da36b-129">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="da36b-129">Lambda expressions</span></span>](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="da36b-130">運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="da36b-130">Expression-bodied members</span></span>](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)