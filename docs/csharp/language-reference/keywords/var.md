---
description: 'var-c # 參考'
title: 'var-c # 參考'
ms.date: 10/02/2020
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d04bea9bcf5be726d3e81a1a53abed31f59330a0
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608708"
---
# <a name="var-c-reference"></a><span data-ttu-id="16526-103">var (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="16526-103">var (C# reference)</span></span>

<span data-ttu-id="16526-104">從 c # 3 開始，在方法範圍內宣告的變數可以有隱含的 "type" `var` 。</span><span class="sxs-lookup"><span data-stu-id="16526-104">Beginning with C# 3, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="16526-105">隱含型別區域變數如同您自己宣告的類型一樣是強型別，但是編譯器會判斷類型。</span><span class="sxs-lookup"><span data-stu-id="16526-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="16526-106">下列兩個 `i` 宣告的功能相同：</span><span class="sxs-lookup"><span data-stu-id="16526-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

> [!IMPORTANT]
> <span data-ttu-id="16526-107">當 `var` 與 [可為 null 的參考](../builtin-types/nullable-reference-types.md) 型別搭配使用時，即使運算式型別不可為 null，它一律隱含表示可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="16526-107">When `var` is used with [nullable reference types](../builtin-types/nullable-reference-types.md) enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

<span data-ttu-id="16526-108">關鍵字的常見用法是使用「函式 `var` 調用運算式」。</span><span class="sxs-lookup"><span data-stu-id="16526-108">A common use of the `var` keyword is with constructor invocation expressions.</span></span> <span data-ttu-id="16526-109">使用可 `var` 讓您不在變數宣告和物件具現化中重複類型名稱，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="16526-109">The use of `var` allows you to not repeat a type name in a variable declaration and object instantiation, as the following example shows:</span></span>

```csharp
var xs = new List<int>();
```

<span data-ttu-id="16526-110">從 c # 9.0 開始，您可以使用目標型別[ `new` 運算式](../operators/new-operator.md)做為替代方案：</span><span class="sxs-lookup"><span data-stu-id="16526-110">Beginning with C# 9.0, you can use a target-typed [`new` expression](../operators/new-operator.md) as an alternative:</span></span>

```csharp
List<int> xs = new();
List<int>? ys = new();
```

## <a name="example"></a><span data-ttu-id="16526-111">範例</span><span class="sxs-lookup"><span data-stu-id="16526-111">Example</span></span>

<span data-ttu-id="16526-112">下例示範兩個查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="16526-112">The following example shows two query expressions.</span></span> <span data-ttu-id="16526-113">在第一個運算式中允許使用 `var`，但並非必要，因為查詢結果的類型可以明確陳述為 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="16526-113">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="16526-114">不過，在第二個運算式中，`var` 允許結果是匿名型別的集合，而且只有編譯器本身才能存取該型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="16526-114">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="16526-115">使用 `var` 就不需要建立結果的新類別。</span><span class="sxs-lookup"><span data-stu-id="16526-115">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="16526-116">請注意，在範例 #2 中，`foreach` 反覆運算變數 `item` 必須也是隱含型別。</span><span class="sxs-lookup"><span data-stu-id="16526-116">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="16526-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16526-117">See also</span></span>

- [<span data-ttu-id="16526-118">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="16526-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="16526-119">隱含類型區域變數</span><span class="sxs-lookup"><span data-stu-id="16526-119">Implicitly typed local variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
- [<span data-ttu-id="16526-120">LINQ 查詢作業中的類型關聯性</span><span class="sxs-lookup"><span data-stu-id="16526-120">Type relationships in LINQ query operations</span></span>](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
