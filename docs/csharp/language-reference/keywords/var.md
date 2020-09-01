---
description: var - C# 參考
title: var - C# 參考
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141708"
---
# <a name="var-c-reference"></a><span data-ttu-id="ec9bb-103">var (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ec9bb-103">var (C# Reference)</span></span>

<span data-ttu-id="ec9bb-104">從 Visual C# 3.0 開始，在方法範圍內宣告的變數可以使用隱含的「類型」`var`。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-104">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="ec9bb-105">隱含型別區域變數如同您自己宣告的類型一樣是強型別，但是編譯器會判斷類型。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-105">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="ec9bb-106">下列兩個 `i` 宣告的功能相同：</span><span class="sxs-lookup"><span data-stu-id="ec9bb-106">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="ec9bb-107">如需詳細資訊，請參閱[LINQ 查詢作業中](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)的[隱含類型區域變數](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和類型關聯性。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-107">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec9bb-108">當 `var` 與可為 null 的參考型別搭配使用時，即使運算式型別不可為 null，它一律隱含表示可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-108">When `var` is used with nullable reference types enabled, it always implies a nullable reference type even if the expression type isn't nullable.</span></span>

## <a name="example"></a><span data-ttu-id="ec9bb-109">範例</span><span class="sxs-lookup"><span data-stu-id="ec9bb-109">Example</span></span>

<span data-ttu-id="ec9bb-110">下例示範兩個查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-110">The following example shows two query expressions.</span></span> <span data-ttu-id="ec9bb-111">在第一個運算式中允許使用 `var`，但並非必要，因為查詢結果的類型可以明確陳述為 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-111">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="ec9bb-112">不過，在第二個運算式中，`var` 允許結果是匿名型別的集合，而且只有編譯器本身才能存取該型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-112">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="ec9bb-113">使用 `var` 就不需要建立結果的新類別。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-113">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="ec9bb-114">請注意，在範例 #2 中，`foreach` 反覆運算變數 `item` 必須也是隱含型別。</span><span class="sxs-lookup"><span data-stu-id="ec9bb-114">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="ec9bb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec9bb-115">See also</span></span>

- [<span data-ttu-id="ec9bb-116">C # 參考</span><span class="sxs-lookup"><span data-stu-id="ec9bb-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ec9bb-117">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ec9bb-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ec9bb-118">隱含類型區域變數</span><span class="sxs-lookup"><span data-stu-id="ec9bb-118">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
