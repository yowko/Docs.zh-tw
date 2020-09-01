---
description: orderby 子句 - C# 參考
title: orderby 子句 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 2f64b45ff252c7cc02e56c465da21ccc5e861aec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142345"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="be926-103">orderby 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="be926-103">orderby clause (C# Reference)</span></span>

<span data-ttu-id="be926-104">在查詢運算式中，`orderby` 子句可讓傳回的序列或子序列 (群組) 以遞增或遞減順序排序。</span><span class="sxs-lookup"><span data-stu-id="be926-104">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="be926-105">您可以指定多個索引鍵，以便執行一或多個次要排序作業。</span><span class="sxs-lookup"><span data-stu-id="be926-105">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="be926-106">排序是由項目類型的預設比較子執行。</span><span class="sxs-lookup"><span data-stu-id="be926-106">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="be926-107">預設排序順序為遞增。</span><span class="sxs-lookup"><span data-stu-id="be926-107">The default sort order is ascending.</span></span> <span data-ttu-id="be926-108">您也可以指定自訂比較子。</span><span class="sxs-lookup"><span data-stu-id="be926-108">You can also specify a custom comparer.</span></span> <span data-ttu-id="be926-109">不過，它只有在使用以方法為基礎的語法時才可用。</span><span class="sxs-lookup"><span data-stu-id="be926-109">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="be926-110">如需詳細資訊，請參閱[排序資料](../../programming-guide/concepts/linq/sorting-data.md)。</span><span class="sxs-lookup"><span data-stu-id="be926-110">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="be926-111">範例</span><span class="sxs-lookup"><span data-stu-id="be926-111">Example</span></span>

<span data-ttu-id="be926-112">在下列範例中，第一個查詢會依照從 A 開始的字母順序排序字組，第二個查詢則以遞減順序排序相同的字組</span><span class="sxs-lookup"><span data-stu-id="be926-112">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="be926-113">(`ascending` 關鍵字是預設排序值，而且可以省略)。</span><span class="sxs-lookup"><span data-stu-id="be926-113">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="be926-114">範例</span><span class="sxs-lookup"><span data-stu-id="be926-114">Example</span></span>

<span data-ttu-id="be926-115">下列範例會對學生的姓氏執行主要排序，然後對其名字執行次要排序。</span><span class="sxs-lookup"><span data-stu-id="be926-115">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="be926-116">備註</span><span class="sxs-lookup"><span data-stu-id="be926-116">Remarks</span></span>

<span data-ttu-id="be926-117">在編譯時期，`orderby` 子句會轉譯為 <xref:System.Linq.Enumerable.OrderBy%2A> 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="be926-117">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="be926-118">`orderby` 子句中的多個索引鍵翻譯為 <xref:System.Linq.Enumerable.ThenBy%2A> 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="be926-118">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="be926-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be926-119">See also</span></span>

- [<span data-ttu-id="be926-120">C # 參考</span><span class="sxs-lookup"><span data-stu-id="be926-120">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be926-121">LINQ)  (查詢關鍵字 </span><span class="sxs-lookup"><span data-stu-id="be926-121">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="be926-122">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="be926-122">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="be926-123">group 子句</span><span class="sxs-lookup"><span data-stu-id="be926-123">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="be926-124">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="be926-124">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
