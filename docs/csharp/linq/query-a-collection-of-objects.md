---
title: 查詢物件集合 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 查詢集合。
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 7bc59e7009f9ae8d8f66c24e9519d9100404c9c4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480916"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="b2662-103">查詢物件的集合</span><span class="sxs-lookup"><span data-stu-id="b2662-103">Query a collection of objects</span></span>

<span data-ttu-id="b2662-104">這個範例示範如何對 `Student` 物件清單執行簡單查詢。</span><span class="sxs-lookup"><span data-stu-id="b2662-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="b2662-105">每個 `Student` 物件都包含學生的一些基本資訊，以及一份代表學生四次考試分數的清單。</span><span class="sxs-lookup"><span data-stu-id="b2662-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="b2662-106">這個應用程式作為本節中使用相同 `students` 資料來源的許多其他範例的架構。</span><span class="sxs-lookup"><span data-stu-id="b2662-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2662-107">範例</span><span class="sxs-lookup"><span data-stu-id="b2662-107">Example</span></span>

<span data-ttu-id="b2662-108">下列查詢會傳回第一次考試分數等於或高於 90 的學生。</span><span class="sxs-lookup"><span data-stu-id="b2662-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="b2662-109">此查詢是刻意簡單，好讓您進行體驗。</span><span class="sxs-lookup"><span data-stu-id="b2662-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="b2662-110">例如，您可以在 `where` 子句中嘗試多個條件，或使用 `orderby` 子句來排序結果。</span><span class="sxs-lookup"><span data-stu-id="b2662-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2662-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2662-111">See also</span></span>

- [<span data-ttu-id="b2662-112">Language-Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b2662-112">Language Integrated Query (LINQ)</span></span>](index.md)  
- [<span data-ttu-id="b2662-113">字串內插補點</span><span class="sxs-lookup"><span data-stu-id="b2662-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)