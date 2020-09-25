---
title: 查詢資料庫
ms.date: 03/30/2017
ms.assetid: eefb8b0c-ff07-4e86-a3d3-567479523fe9
ms.openlocfilehash: b4ce48ee3d49769a353bf7371140b1f5a645f34e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184868"
---
# <a name="querying-the-database"></a><span data-ttu-id="7bf3b-102">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="7bf3b-102">Querying the Database</span></span>

<span data-ttu-id="7bf3b-103">這組主題描述如何在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案中開發和執行查詢。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-103">This group of topics describes how to develop and execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7bf3b-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="7bf3b-104">In This Section</span></span>  

 [<span data-ttu-id="7bf3b-105">作法：查詢資訊</span><span class="sxs-lookup"><span data-stu-id="7bf3b-105">How to: Query for Information</span></span>](how-to-query-for-information.md)  
 <span data-ttu-id="7bf3b-106">簡短顯示 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢基本上與 LINQ 查詢相同。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-106">Briefly shows how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are basically the same as LINQ queries generally.</span></span>  
  
 [<span data-ttu-id="7bf3b-107">作法：以唯讀形式擷取資訊</span><span class="sxs-lookup"><span data-stu-id="7bf3b-107">How to: Retrieve Information As Read-Only</span></span>](how-to-retrieve-information-as-read-only.md)  
 <span data-ttu-id="7bf3b-108">描述如何在未計劃變更資料的情況下增加查詢效能。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-108">Describes how to increase query performance when no change to the data is planned.</span></span>  
  
 [<span data-ttu-id="7bf3b-109">作法：控制擷取的相關資料多寡</span><span class="sxs-lookup"><span data-stu-id="7bf3b-109">How to: Control How Much Related Data Is Retrieved</span></span>](how-to-control-how-much-related-data-is-retrieved.md)  
 <span data-ttu-id="7bf3b-110">描述如何控制哪些相關資料要與主要目標一起擷取。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-110">Describes how to control which related data is retrieved together with the main target.</span></span>  
  
 [<span data-ttu-id="7bf3b-111">作法：篩選相關資料</span><span class="sxs-lookup"><span data-stu-id="7bf3b-111">How to: Filter Related Data</span></span>](how-to-filter-related-data.md)  
 <span data-ttu-id="7bf3b-112">描述如何使用子查詢來擷取相關資料。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-112">Describes how to retrieve related data by using a sub-query.</span></span>  
  
 [<span data-ttu-id="7bf3b-113">作法：關閉延後載入</span><span class="sxs-lookup"><span data-stu-id="7bf3b-113">How to: Turn Off Deferred Loading</span></span>](how-to-turn-off-deferred-loading.md)  
 <span data-ttu-id="7bf3b-114">描述如何關閉延後載入。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-114">Describes how to turn off deferred loading.</span></span>  
  
 [<span data-ttu-id="7bf3b-115">作法：直接執行 SQL 查詢</span><span class="sxs-lookup"><span data-stu-id="7bf3b-115">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)  
 <span data-ttu-id="7bf3b-116">描述如何使用 SQL 語言來送出查詢。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-116">Describes how to submit queries by using SQL language.</span></span>  
  
 [<span data-ttu-id="7bf3b-117">作法：儲存和重複使用查詢</span><span class="sxs-lookup"><span data-stu-id="7bf3b-117">How to: Store and Reuse Queries</span></span>](how-to-store-and-reuse-queries.md)  
 <span data-ttu-id="7bf3b-118">描述如何只編譯一次查詢，但多次將它與不同參數搭配使用。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-118">Describes how to compile a query one time but use it multiple times with different parameters.</span></span>  
  
 [<span data-ttu-id="7bf3b-119">作法：在查詢中處理複合索引鍵</span><span class="sxs-lookup"><span data-stu-id="7bf3b-119">How to: Handle Composite Keys in Queries</span></span>](how-to-handle-composite-keys-in-queries.md)  
 <span data-ttu-id="7bf3b-120">描述如何在查詢中包括多個資料行，而在這個查詢中，運算子只取用單一引數。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-120">Describes how to include more than one column in a query where the operator takes only a single argument.</span></span>  
  
 [<span data-ttu-id="7bf3b-121">作法：一次擷取多個物件</span><span class="sxs-lookup"><span data-stu-id="7bf3b-121">How to: Retrieve Many Objects At Once</span></span>](how-to-retrieve-many-objects-at-once.md)  
 <span data-ttu-id="7bf3b-122">說明如何使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-122">Describes how to use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="7bf3b-123">作法：在 DataContext 層級篩選</span><span class="sxs-lookup"><span data-stu-id="7bf3b-123">How to: Filter at the DataContext Level</span></span>](how-to-filter-at-the-datacontext-level.md)  
 <span data-ttu-id="7bf3b-124">描述另一種 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 使用方式。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-124">Describes another use of <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
 [<span data-ttu-id="7bf3b-125">查詢範例</span><span class="sxs-lookup"><span data-stu-id="7bf3b-125">Query Examples</span></span>](query-examples.md)  
 <span data-ttu-id="7bf3b-126">提供查詢的許多範例。</span><span class="sxs-lookup"><span data-stu-id="7bf3b-126">Provides many examples of queries.</span></span>
