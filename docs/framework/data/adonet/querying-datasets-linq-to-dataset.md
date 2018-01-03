---
title: "查詢資料集 (LINQ to DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3793417502d359a9d05899f6e1d4306aac7ca88b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="bb549-102">查詢資料集 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="bb549-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="bb549-103">當 <xref:System.Data.DataSet> 物件已經填入 (Populate) 資料之後，您就可以開始查詢它。</span><span class="sxs-lookup"><span data-stu-id="bb549-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="bb549-104">使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來編寫查詢與針對其他啟用 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 的資料來源使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 很相似。</span><span class="sxs-lookup"><span data-stu-id="bb549-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="bb549-105">請記住，但是，當您使用[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]查詢經過一段<xref:System.Data.DataSet>您要查詢的列舉物件<xref:System.Data.DataRow>物件，而不是自訂類型的列舉。</span><span class="sxs-lookup"><span data-stu-id="bb549-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="bb549-106">這表示您可以使用任何成員的<xref:System.Data.DataRow>類別中您[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="bb549-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="bb549-107">這可讓您建立內容豐富且複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="bb549-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="bb549-108">如同其他實作[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]，您可以建立[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]兩種不同形式的查詢： 查詢運算式語法和以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="bb549-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="bb549-109">如需有關這兩種格式的詳細資訊，請參閱[撰寫 LINQ 入門](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)。</span><span class="sxs-lookup"><span data-stu-id="bb549-109">For more information about these two forms, see [Getting Started with LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).</span></span> <span data-ttu-id="bb549-110">您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。</span><span class="sxs-lookup"><span data-stu-id="bb549-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bb549-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="bb549-111">In This Section</span></span>  
 [<span data-ttu-id="bb549-112">單一資料表查詢</span><span class="sxs-lookup"><span data-stu-id="bb549-112">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="bb549-113">說明如何執行單一資料表查詢。</span><span class="sxs-lookup"><span data-stu-id="bb549-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="bb549-114">跨資料表查詢</span><span class="sxs-lookup"><span data-stu-id="bb549-114">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="bb549-115">說明如何執行跨資料表查詢。</span><span class="sxs-lookup"><span data-stu-id="bb549-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="bb549-116">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="bb549-116">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="bb549-117">說明如何查詢具型別 <xref:System.Data.DataSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="bb549-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb549-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb549-118">See Also</span></span>  
 [<span data-ttu-id="bb549-119">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="bb549-119">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="bb549-120">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="bb549-120">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
