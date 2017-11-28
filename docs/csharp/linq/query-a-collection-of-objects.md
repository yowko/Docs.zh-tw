---
title: "查詢物件的集合"
description: "如何查詢集合。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="5219a-104">查詢物件的集合</span><span class="sxs-lookup"><span data-stu-id="5219a-104">Query a collection of objects</span></span>
<span data-ttu-id="5219a-105">這個範例示範如何對 `Student` 物件清單執行簡單查詢。</span><span class="sxs-lookup"><span data-stu-id="5219a-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="5219a-106">每個 `Student` 物件都包含學生的一些基本資訊，以及一份代表學生四次考試分數的清單。</span><span class="sxs-lookup"><span data-stu-id="5219a-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="5219a-107">這個應用程式作為本節中使用相同 `students` 資料來源的許多其他範例的架構。</span><span class="sxs-lookup"><span data-stu-id="5219a-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5219a-108">範例</span><span class="sxs-lookup"><span data-stu-id="5219a-108">Example</span></span>  
 <span data-ttu-id="5219a-109">下列查詢會傳回第一次考試分數等於或高於 90 的學生。</span><span class="sxs-lookup"><span data-stu-id="5219a-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="5219a-110">此查詢是刻意簡單，好讓您進行體驗。</span><span class="sxs-lookup"><span data-stu-id="5219a-110">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="5219a-111">例如，您可以在 `where` 子句中嘗試多個條件，或使用 `orderby` 子句來排序結果。</span><span class="sxs-lookup"><span data-stu-id="5219a-111">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="5219a-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="5219a-112">See also</span></span>  
 [<span data-ttu-id="5219a-113">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="5219a-113">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="5219a-114">字串插值</span><span class="sxs-lookup"><span data-stu-id="5219a-114">Interpolated Strings</span></span>](../language-reference/keywords/interpolated-strings.md)
