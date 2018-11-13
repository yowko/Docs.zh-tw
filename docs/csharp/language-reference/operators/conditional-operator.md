---
title: '?: 運算子 (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980618"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c907d-102">?: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c907d-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="c907d-103">條件運算子 (`?:`) 通稱為三元條件運算式，是根據布林運算式的值傳回兩個值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="c907d-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="c907d-104">以下是條件運算子的語法。</span><span class="sxs-lookup"><span data-stu-id="c907d-104">Following is the syntax for the conditional operator.</span></span>  

```csharp
condition ? first_expression : second_expression;  
```

<span data-ttu-id="c907d-105">從 C# 7.2 開始，`first_expression` 及 `second_expression` 可以是 [`ref` 運算式](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md)：</span><span class="sxs-lookup"><span data-stu-id="c907d-105">Beginning with C# 7.2, the `first_expression` and `second_expression` my be [`ref` expressions](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span></span>

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

<span data-ttu-id="c907d-106">結果可能指派給 `ref` 或 `ref readonly` 變數，或是沒有這兩個修飾詞的變數。</span><span class="sxs-lookup"><span data-stu-id="c907d-106">The result may be assigned to a `ref` or `ref readonly` variable, or to a variable with neither modifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="c907d-107">備註</span><span class="sxs-lookup"><span data-stu-id="c907d-107">Remarks</span></span>

<span data-ttu-id="c907d-108">`condition` 必須判斷值為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="c907d-108">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="c907d-109">如果 `condition` 為 `true`，則會評估 `first_expression` 並產生結果。</span><span class="sxs-lookup"><span data-stu-id="c907d-109">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="c907d-110">如果 `condition` 為 `false`，則會評估 `second_expression` 並產生結果。</span><span class="sxs-lookup"><span data-stu-id="c907d-110">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="c907d-111">只會評估兩個運算式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="c907d-111">Only one of the two expressions is evaluated.</span></span> <span data-ttu-id="c907d-112">這對結果為 `ref` 的運算式特別重要，而下列語法有效：</span><span class="sxs-lookup"><span data-stu-id="c907d-112">This is particularly important for expressions where the result is a `ref`, as the following is valid:</span></span>

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

<span data-ttu-id="c907d-113">當 `storage` 為 null 時，就不會求 `storage` 的參考值。</span><span class="sxs-lookup"><span data-stu-id="c907d-113">The reference to `storage` is not evaluated when `storage` is null.</span></span>

<span data-ttu-id="c907d-114">當結果為值時，`first_expression` 及 `second_expression` 的型別必須相同，或必須為來自兩者其中一種型別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c907d-114">When the result is a value, the type of `first_expression` and `second_expression` must be the same, or there must be an implicit conversion from one type to the other.</span></span> <span data-ttu-id="c907d-115">當結果為 `ref` 時，`first_expression` 及 `second_expression` 的型別必須相同。</span><span class="sxs-lookup"><span data-stu-id="c907d-115">When the result is a `ref`, the type of `first_expression` and `second_expression` must be the same.</span></span>

<span data-ttu-id="c907d-116">你可以使用條件運算子更精確地表示可能需要 `if-else` 建構的計算。</span><span class="sxs-lookup"><span data-stu-id="c907d-116">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="c907d-117">例如，下列程式碼會先使用 `if` 陳述式，再使用條件運算子將整數分類為正數或負數。</span><span class="sxs-lookup"><span data-stu-id="c907d-117">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

<span data-ttu-id="c907d-118">條件運算子是右向關聯。</span><span class="sxs-lookup"><span data-stu-id="c907d-118">The conditional operator is right-associative.</span></span> <span data-ttu-id="c907d-119">運算式 `a ? b : c ? d : e` 會判斷值為 `a ? b : (c ? d : e)`，而不是 `(a ? b : c) ? d : e`。</span><span class="sxs-lookup"><span data-stu-id="c907d-119">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
<span data-ttu-id="c907d-120">條件運算子不能多載。</span><span class="sxs-lookup"><span data-stu-id="c907d-120">The conditional operator cannot be overloaded.</span></span>
  
## <a name="example"></a><span data-ttu-id="c907d-121">範例</span><span class="sxs-lookup"><span data-stu-id="c907d-121">Example</span></span>

<span data-ttu-id="c907d-122">下列範例顯示了結果為值的條件式運算子：</span><span class="sxs-lookup"><span data-stu-id="c907d-122">The following example shows the conditional operator whose result is a value:</span></span>

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

<span data-ttu-id="c907d-123">下列另一種方式顯示了結果為參考的條件式運算子：</span><span class="sxs-lookup"><span data-stu-id="c907d-123">The following alternative shows the conditional operator where the result is a reference:</span></span>

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a><span data-ttu-id="c907d-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="c907d-124">See Also</span></span>

- [<span data-ttu-id="c907d-125">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c907d-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c907d-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c907d-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c907d-127">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="c907d-127">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="c907d-128">if-else</span><span class="sxs-lookup"><span data-stu-id="c907d-128">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
- <span data-ttu-id="c907d-129">[?. 和 ?[] 運算子](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="c907d-129">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
- [<span data-ttu-id="c907d-130">??運算子</span><span class="sxs-lookup"><span data-stu-id="c907d-130">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
