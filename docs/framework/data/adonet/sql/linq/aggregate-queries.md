---
title: 彙總查詢
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: 8dfe24a84c707b6d21afb7ccfc57ac7b0423942f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161538"
---
# <a name="aggregate-queries"></a><span data-ttu-id="07cab-102">彙總查詢</span><span class="sxs-lookup"><span data-stu-id="07cab-102">Aggregate Queries</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="07cab-103">支援 `Average`、`Count`、`Max`、`Min` 和 `Sum` 彙總運算子。</span><span class="sxs-lookup"><span data-stu-id="07cab-103">supports the `Average`, `Count`, `Max`, `Min`, and `Sum` aggregate operators.</span></span> <span data-ttu-id="07cab-104">請注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的彙總運算子有下列特性：</span><span class="sxs-lookup"><span data-stu-id="07cab-104">Note the following characteristics of aggregate operators in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="07cab-105">彙總查詢會立即執行。</span><span class="sxs-lookup"><span data-stu-id="07cab-105">Aggregate queries are executed immediately.</span></span>  
  
     <span data-ttu-id="07cab-106">如需詳細資訊，請參閱 [LINQ 查詢簡介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="07cab-106">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
- <span data-ttu-id="07cab-107">彙總查詢通常會傳回數字，而不是集合。</span><span class="sxs-lookup"><span data-stu-id="07cab-107">Aggregate queries typically return a number instead of a collection.</span></span>  
  
     <span data-ttu-id="07cab-108">如需詳細資訊，請參閱 [匯總作業](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="07cab-108">For more information, see [Aggregation Operations](/previous-versions/visualstudio/visual-studio-2013/bb546138(v=vs.120)).</span></span>  
  
- <span data-ttu-id="07cab-109">您不可以對匿名型別呼叫彙總。</span><span class="sxs-lookup"><span data-stu-id="07cab-109">You cannot call aggregates against anonymous types.</span></span>  
  
 <span data-ttu-id="07cab-110">下列主題中的範例衍生自 Northwind 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="07cab-110">The examples in the following topics derive from the Northwind sample database.</span></span> <span data-ttu-id="07cab-111">如需詳細資訊，請參閱 [下載範例資料庫](downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="07cab-111">For more information, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07cab-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="07cab-112">In This Section</span></span>  

 [<span data-ttu-id="07cab-113">傳回數值序列的平均值</span><span class="sxs-lookup"><span data-stu-id="07cab-113">Return the Average Value From a Numeric Sequence</span></span>](return-the-average-value-from-a-numeric-sequence.md)  
 <span data-ttu-id="07cab-114">示範如何使用 <xref:System.Linq.Enumerable.Average%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="07cab-114">Demonstrates how to use the <xref:System.Linq.Enumerable.Average%2A> operator.</span></span>  
  
 [<span data-ttu-id="07cab-115">計算序列中的項目數目</span><span class="sxs-lookup"><span data-stu-id="07cab-115">Count the Number of Elements in a Sequence</span></span>](count-the-number-of-elements-in-a-sequence.md)  
 <span data-ttu-id="07cab-116">示範如何使用 <xref:System.Linq.Enumerable.Count%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="07cab-116">Demonstrates how to use the <xref:System.Linq.Enumerable.Count%2A> operator.</span></span>  
  
 [<span data-ttu-id="07cab-117">尋找數值序列中的最大值</span><span class="sxs-lookup"><span data-stu-id="07cab-117">Find the Maximum Value in a Numeric Sequence</span></span>](find-the-maximum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="07cab-118">示範如何使用 <xref:System.Linq.Enumerable.Max%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="07cab-118">Demonstrates how to use the <xref:System.Linq.Enumerable.Max%2A> operator.</span></span>  
  
 [<span data-ttu-id="07cab-119">尋找數值序列中的最小值</span><span class="sxs-lookup"><span data-stu-id="07cab-119">Find the Minimum Value in a Numeric Sequence</span></span>](find-the-minimum-value-in-a-numeric-sequence.md)  
 <span data-ttu-id="07cab-120">示範如何使用 <xref:System.Linq.Enumerable.Min%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="07cab-120">Demonstrates how to use the <xref:System.Linq.Enumerable.Min%2A> operator.</span></span>  
  
 [<span data-ttu-id="07cab-121">如何：計算數值序列中各值的總和</span><span class="sxs-lookup"><span data-stu-id="07cab-121">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <span data-ttu-id="07cab-122">示範如何使用 <xref:System.Linq.Enumerable.Sum%2A> 運算子。</span><span class="sxs-lookup"><span data-stu-id="07cab-122">Demonstrates how to use the <xref:System.Linq.Enumerable.Sum%2A> operator.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="07cab-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="07cab-123">Related Sections</span></span>  

 [<span data-ttu-id="07cab-124">查詢範例</span><span class="sxs-lookup"><span data-stu-id="07cab-124">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="07cab-125">提供 Visual Basic 和 C# 中之 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢的連結。</span><span class="sxs-lookup"><span data-stu-id="07cab-125">Provides links to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries in Visual Basic and C#.</span></span>  
  
 [<span data-ttu-id="07cab-126">查詢概念</span><span class="sxs-lookup"><span data-stu-id="07cab-126">Query Concepts</span></span>](query-concepts.md)  
 <span data-ttu-id="07cab-127">提供主題的連結，這些主題說明在中設計 LINQ 查詢的概念 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="07cab-127">Provides links to topics that explain concepts for designing LINQ queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="07cab-128">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="07cab-128">Introduction to LINQ Queries (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="07cab-129">說明查詢在 LINQ 中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="07cab-129">Explains how queries work in LINQ.</span></span>
