---
title: 查詢資料集 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: a1c316811ce08141999bcec4c9c8504f86c2e285
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165239"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="0d73e-102">查詢資料集 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0d73e-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="0d73e-103">當 <xref:System.Data.DataSet> 物件已經填入 (Populate) 資料之後，您就可以開始查詢它。</span><span class="sxs-lookup"><span data-stu-id="0d73e-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="0d73e-104">使用 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 來編寫查詢與針對其他啟用 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 的資料來源使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 很相似。</span><span class="sxs-lookup"><span data-stu-id="0d73e-104">Formulating queries with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] is similar to using [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] against other [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-enabled data sources.</span></span> <span data-ttu-id="0d73e-105">記住，不過，當您使用[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]透過查詢<xref:System.Data.DataSet>物件，您要查詢的列舉<xref:System.Data.DataRow>物件，而不是自訂類型的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="0d73e-105">Remember, however, that when you use [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries over a <xref:System.Data.DataSet> object you are querying an enumeration of <xref:System.Data.DataRow> objects, instead of an enumeration of a custom type.</span></span> <span data-ttu-id="0d73e-106">這表示，您可以使用任何的成員清單<xref:System.Data.DataRow>類別中您[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="0d73e-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="0d73e-107">這可讓您建立內容豐富且複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="0d73e-107">This lets you to create rich, complex queries.</span></span>  
  
 <span data-ttu-id="0d73e-108">與其他實作的一樣[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]，您可以建立[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]兩種不同形式的查詢： 查詢運算式語法和以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="0d73e-108">As with other implementations of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], you can create [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="0d73e-109">您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。</span><span class="sxs-lookup"><span data-stu-id="0d73e-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d73e-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="0d73e-110">In This Section</span></span>  
 [<span data-ttu-id="0d73e-111">單一資料表查詢</span><span class="sxs-lookup"><span data-stu-id="0d73e-111">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="0d73e-112">說明如何執行單一資料表查詢。</span><span class="sxs-lookup"><span data-stu-id="0d73e-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="0d73e-113">跨資料表查詢</span><span class="sxs-lookup"><span data-stu-id="0d73e-113">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="0d73e-114">說明如何執行跨資料表查詢。</span><span class="sxs-lookup"><span data-stu-id="0d73e-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="0d73e-115">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="0d73e-115">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 <span data-ttu-id="0d73e-116">說明如何查詢具型別 <xref:System.Data.DataSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="0d73e-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d73e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d73e-117">See also</span></span>

- [<span data-ttu-id="0d73e-118">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="0d73e-118">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="0d73e-119">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="0d73e-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
