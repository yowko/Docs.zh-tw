---
title: 查詢物件集合 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 查詢集合。
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659804"
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="a25fd-103">查詢物件的集合</span><span class="sxs-lookup"><span data-stu-id="a25fd-103">Query a collection of objects</span></span>

<span data-ttu-id="a25fd-104">這個範例示範如何對 `Student` 物件清單執行簡單查詢。</span><span class="sxs-lookup"><span data-stu-id="a25fd-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="a25fd-105">每個 `Student` 物件都包含學生的一些基本資訊，以及一份代表學生四次考試分數的清單。</span><span class="sxs-lookup"><span data-stu-id="a25fd-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
<span data-ttu-id="a25fd-106">這個應用程式作為本節中使用相同 `students` 資料來源的許多其他範例的架構。</span><span class="sxs-lookup"><span data-stu-id="a25fd-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a25fd-107">範例</span><span class="sxs-lookup"><span data-stu-id="a25fd-107">Example</span></span>

<span data-ttu-id="a25fd-108">下列查詢會傳回第一次考試分數等於或高於 90 的學生。</span><span class="sxs-lookup"><span data-stu-id="a25fd-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
<span data-ttu-id="a25fd-109">此查詢是刻意簡單，好讓您進行體驗。</span><span class="sxs-lookup"><span data-stu-id="a25fd-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="a25fd-110">例如，您可以在 `where` 子句中嘗試多個條件，或使用 `orderby` 子句來排序結果。</span><span class="sxs-lookup"><span data-stu-id="a25fd-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25fd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a25fd-111">See also</span></span>

- [<span data-ttu-id="a25fd-112">語言綜合查詢（LINQ）</span><span class="sxs-lookup"><span data-stu-id="a25fd-112">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="a25fd-113">字串插補</span><span class="sxs-lookup"><span data-stu-id="a25fd-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
