---
title: let 子句 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 62294df7f0f2ebb3249dffd72ba4910fbae984c8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266624"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="9d8f5-102">let 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="9d8f5-102">let clause (C# Reference)</span></span>

<span data-ttu-id="9d8f5-103">在查詢運算式中，有時它十分適合儲存子運算式的結果，以將它用於後續子句。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="9d8f5-104">您可以使用 `let` 關鍵字執行這項作業，而此關鍵字會建立新的範圍變數，並使用您提供的運算式結果將它初始化。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="9d8f5-105">使用值初始化之後，就不能使用範圍變數來儲存另一個值。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="9d8f5-106">不過，如果範圍變數保留可查詢類型，則可以進行查詢。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="9d8f5-107">範例</span><span class="sxs-lookup"><span data-stu-id="9d8f5-107">Example</span></span>

<span data-ttu-id="9d8f5-108">在下列範例中，以兩種方式使用 `let`：</span><span class="sxs-lookup"><span data-stu-id="9d8f5-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="9d8f5-109">建立本身可進行查詢的可列舉類型。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="9d8f5-110">讓查詢只對範圍變數 `word` 呼叫一次 `ToLower`。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="9d8f5-111">如果不使用 `let`，則您需要在 `where` 子句的每個述詞中呼叫 `ToLower`。</span><span class="sxs-lookup"><span data-stu-id="9d8f5-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="9d8f5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d8f5-112">See also</span></span>

- [<span data-ttu-id="9d8f5-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="9d8f5-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9d8f5-114">查詢關鍵字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9d8f5-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="9d8f5-115">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9d8f5-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="9d8f5-116">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="9d8f5-116">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="9d8f5-117">處理查詢運算式中的例外狀況</span><span class="sxs-lookup"><span data-stu-id="9d8f5-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)