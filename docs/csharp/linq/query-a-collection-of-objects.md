---
title: "查詢物件的集合"
description: "如何查詢集合。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e08f2e5877ffe24f5a238ab19abb9760cb442f2
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="39b36-104">查詢物件的集合</span><span class="sxs-lookup"><span data-stu-id="39b36-104">Query a collection of objects</span></span>
<span data-ttu-id="39b36-105">這個範例示範如何對 `Student` 物件清單執行簡單查詢。</span><span class="sxs-lookup"><span data-stu-id="39b36-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="39b36-106">每個 `Student` 物件都包含學生的一些基本資訊，以及一份代表學生四次考試分數的清單。</span><span class="sxs-lookup"><span data-stu-id="39b36-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="39b36-107">這個應用程式作為本節中使用相同 `students` 資料來源的許多其他範例的架構。</span><span class="sxs-lookup"><span data-stu-id="39b36-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39b36-108">範例</span><span class="sxs-lookup"><span data-stu-id="39b36-108">Example</span></span>  
 <span data-ttu-id="39b36-109">下列查詢會傳回第一次考試分數等於或高於 90 的學生。</span><span class="sxs-lookup"><span data-stu-id="39b36-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 <span data-ttu-id="39b36-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="39b36-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span></span>  
  
 <span data-ttu-id="39b36-111">此查詢是刻意簡單，好讓您進行體驗。</span><span class="sxs-lookup"><span data-stu-id="39b36-111">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="39b36-112">例如，您可以在 `where` 子句中嘗試多個條件，或使用 `orderby` 子句來排序結果。</span><span class="sxs-lookup"><span data-stu-id="39b36-112">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="39b36-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="39b36-113">See also</span></span>  
 [<span data-ttu-id="39b36-114">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="39b36-114">LINQ Query Expressions</span></span>](index.md)

