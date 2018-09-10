---
title: into (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 6d46ae67dd84650172125c62ea70dc109671a89b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507839"
---
# <a name="into-c-reference"></a><span data-ttu-id="7817e-102">into (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="7817e-102">into (C# Reference)</span></span>

<span data-ttu-id="7817e-103">`into` 內容關鍵字可以用來建立暫時識別碼，以將 [group](group-clause.md)、[join](join-clause.md) 或 [select](select-clause.md) 子句結果儲存至新的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7817e-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="7817e-104">這個識別碼本身可以是其他查詢命令的產生器。</span><span class="sxs-lookup"><span data-stu-id="7817e-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="7817e-105">用於 `group` 或 `select` 子句時，使用 new 識別碼有時稱為「接續」。</span><span class="sxs-lookup"><span data-stu-id="7817e-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="7817e-106">範例</span><span class="sxs-lookup"><span data-stu-id="7817e-106">Example</span></span>

<span data-ttu-id="7817e-107">下列範例示範如何使用 `into` 關鍵字啟用推斷類型為 `IGrouping` 的暫時識別碼 `fruitGroup`。</span><span class="sxs-lookup"><span data-stu-id="7817e-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="7817e-108">使用識別碼，即可在每個群組上叫用 <xref:System.Linq.Enumerable.Count%2A> 方法，並且只選取包含兩個以上單字的群組。</span><span class="sxs-lookup"><span data-stu-id="7817e-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="7817e-109">只有在您想要對每個群組執行其他查詢作業時，才需要在 `group` 子句中使用 `into`。</span><span class="sxs-lookup"><span data-stu-id="7817e-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="7817e-110">如需詳細資訊，請參閱 [group 子句](group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="7817e-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="7817e-111">如需在 `join` 子句中使用 `into` 的範例，請參閱 [join 子句](join-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="7817e-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7817e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7817e-112">See also</span></span>

- [<span data-ttu-id="7817e-113">查詢關鍵字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7817e-113">Query Keywords (LINQ)</span></span>](query-keywords.md)  
- [<span data-ttu-id="7817e-114">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="7817e-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="7817e-115">group 子句</span><span class="sxs-lookup"><span data-stu-id="7817e-115">group clause</span></span>](group-clause.md)  