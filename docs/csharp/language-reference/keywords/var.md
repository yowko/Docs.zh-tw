---
title: var - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 79a3fe331107a902957158a9631f607cb431be32
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610641"
---
# <a name="var-c-reference"></a><span data-ttu-id="ae726-102">var (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ae726-102">var (C# Reference)</span></span>

<span data-ttu-id="ae726-103">從 Visual C# 3.0 開始，在方法範圍內宣告的變數可以使用隱含的「類型」`var`。</span><span class="sxs-lookup"><span data-stu-id="ae726-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="ae726-104">隱含型別區域變數如同您自己宣告的類型一樣是強型別，但是編譯器會判斷類型。</span><span class="sxs-lookup"><span data-stu-id="ae726-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="ae726-105">下列兩個 `i` 宣告的功能相同：</span><span class="sxs-lookup"><span data-stu-id="ae726-105">The following two declarations of `i` are functionally equivalent:</span></span>

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

<span data-ttu-id="ae726-106">如需詳細資訊，請參閱[隱含型別區域變數](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和 [LINQ 查詢作業中的類型關聯性](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="ae726-106">For more information, see [Implicitly Typed Local Variables](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="ae726-107">範例</span><span class="sxs-lookup"><span data-stu-id="ae726-107">Example</span></span>

<span data-ttu-id="ae726-108">下例示範兩個查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="ae726-108">The following example shows two query expressions.</span></span> <span data-ttu-id="ae726-109">在第一個運算式中允許使用 `var`，但並非必要，因為查詢結果的類型可以明確陳述為 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="ae726-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="ae726-110">不過，在第二個運算式中，`var` 允許結果是匿名型別的集合，而且只有編譯器本身才能存取該型別的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae726-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="ae726-111">使用 `var` 就不需要建立結果的新類別。</span><span class="sxs-lookup"><span data-stu-id="ae726-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="ae726-112">請注意，在範例 #2 中，`foreach` 反覆運算變數 `item` 必須也是隱含型別。</span><span class="sxs-lookup"><span data-stu-id="ae726-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a><span data-ttu-id="ae726-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae726-113">See also</span></span>

- [<span data-ttu-id="ae726-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ae726-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ae726-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ae726-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ae726-116">隱含型別區域變數</span><span class="sxs-lookup"><span data-stu-id="ae726-116">Implicitly Typed Local Variables</span></span>](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)