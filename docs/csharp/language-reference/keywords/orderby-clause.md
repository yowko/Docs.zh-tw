---
title: orderby 子句 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: b62634c0f61e17c046cd474670fddf437287ab7a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634100"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="08d7c-102">orderby 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="08d7c-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="08d7c-103">在查詢運算式中，`orderby` 子句可讓傳回的序列或子序列 (群組) 以遞增或遞減順序排序。</span><span class="sxs-lookup"><span data-stu-id="08d7c-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="08d7c-104">您可以指定多個索引鍵，以便執行一或多個次要排序作業。</span><span class="sxs-lookup"><span data-stu-id="08d7c-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="08d7c-105">排序是由項目類型的預設比較子執行。</span><span class="sxs-lookup"><span data-stu-id="08d7c-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="08d7c-106">預設的排序次序為遞增。</span><span class="sxs-lookup"><span data-stu-id="08d7c-106">The default sort order is ascending.</span></span> <span data-ttu-id="08d7c-107">您也可以指定自訂比較子。</span><span class="sxs-lookup"><span data-stu-id="08d7c-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="08d7c-108">不過，它只有在使用以方法為基礎的語法時才可用。</span><span class="sxs-lookup"><span data-stu-id="08d7c-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="08d7c-109">如需詳細資訊，請參閱[排序資料](../../programming-guide/concepts/linq/sorting-data.md)。</span><span class="sxs-lookup"><span data-stu-id="08d7c-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="08d7c-110">範例</span><span class="sxs-lookup"><span data-stu-id="08d7c-110">Example</span></span>

<span data-ttu-id="08d7c-111">在下列範例中，第一個查詢會依照從 A 開始的字母順序排序字組，第二個查詢則以遞減順序排序相同的字組</span><span class="sxs-lookup"><span data-stu-id="08d7c-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="08d7c-112">(`ascending` 關鍵字是預設排序值，而且可以省略)。</span><span class="sxs-lookup"><span data-stu-id="08d7c-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="08d7c-113">範例</span><span class="sxs-lookup"><span data-stu-id="08d7c-113">Example</span></span>

<span data-ttu-id="08d7c-114">下列範例會對學生的姓氏執行主要排序，然後對其名字執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="08d7c-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="08d7c-115">備註</span><span class="sxs-lookup"><span data-stu-id="08d7c-115">Remarks</span></span>

<span data-ttu-id="08d7c-116">在編譯時期，`orderby` 子句會轉譯為 <xref:System.Linq.Enumerable.OrderBy%2A> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="08d7c-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="08d7c-117">`orderby` 子句中的多個索引鍵翻譯為 <xref:System.Linq.Enumerable.ThenBy%2A> 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="08d7c-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="08d7c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08d7c-118">See also</span></span>

- [<span data-ttu-id="08d7c-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="08d7c-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="08d7c-120">查詢關鍵字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="08d7c-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="08d7c-121">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="08d7c-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="08d7c-122">group 子句</span><span class="sxs-lookup"><span data-stu-id="08d7c-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="08d7c-123">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="08d7c-123">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
