---
title: "查詢計畫快取 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 814b4451d5e08d5f9df4d370b2127d971f3fdd1d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="5c888-102">查詢計畫快取 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5c888-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="5c888-103">每當嘗試執行查詢時，查詢管線就會查閱它的查詢快取計畫，以查看精確的查詢是否已編譯且可用。</span><span class="sxs-lookup"><span data-stu-id="5c888-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="5c888-104">如果確實如此，它會重複使用快取的計畫，而不是建立新的計畫。</span><span class="sxs-lookup"><span data-stu-id="5c888-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="5c888-105">如果查詢計畫快取中找不到相符項目，就會編譯及快取此查詢。</span><span class="sxs-lookup"><span data-stu-id="5c888-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="5c888-106">查詢是由它的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 文字和參數集合 (名稱和型別) 所識別。</span><span class="sxs-lookup"><span data-stu-id="5c888-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="5c888-107">所有的文字比較都會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="5c888-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="5c888-108">組態</span><span class="sxs-lookup"><span data-stu-id="5c888-108">Configuration</span></span>  
 <span data-ttu-id="5c888-109">查詢計畫快取可透過 <xref:System.Data.EntityClient.EntityCommand> 來設定。</span><span class="sxs-lookup"><span data-stu-id="5c888-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="5c888-110">若要透過 <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType> 來啟用或停用查詢計畫快取，請將此屬性設定為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="5c888-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="5c888-111">針對不太可能使用一次以上的個別動態查詢停用計畫快取時，將會提升效能。</span><span class="sxs-lookup"><span data-stu-id="5c888-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="5c888-112">您可以透過 <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A> 來啟用查詢計畫快取。</span><span class="sxs-lookup"><span data-stu-id="5c888-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="5c888-113">建議的作法</span><span class="sxs-lookup"><span data-stu-id="5c888-113">Recommended Practice</span></span>  
 <span data-ttu-id="5c888-114">一般來說，應該避免動態查詢。</span><span class="sxs-lookup"><span data-stu-id="5c888-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="5c888-115">下列動態查詢範例容易受到 SQL 插入式攻擊的侵害，因為它會在沒有任何驗證的情況下直接接受使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="5c888-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="5c888-116">如果您使用動態產生的查詢，請考慮停用查詢計畫快取，避免針對不太可能重複使用的快取項目產生不必要的記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="5c888-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="5c888-117">靜態查詢和參數化查詢上的查詢計畫快取可提供效能方面的優點。</span><span class="sxs-lookup"><span data-stu-id="5c888-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="5c888-118">下列是靜態查詢的範例：</span><span class="sxs-lookup"><span data-stu-id="5c888-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="5c888-119">如果是查詢計畫快取所要適當比對的查詢，這些查詢應該要符合以下規定：</span><span class="sxs-lookup"><span data-stu-id="5c888-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
-   <span data-ttu-id="5c888-120">查詢文字應該是固定模式，最好是某個固定字串或資源。</span><span class="sxs-lookup"><span data-stu-id="5c888-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
-   <span data-ttu-id="5c888-121">每當必須傳遞使用者提供的值時，就應該使用 <xref:System.Data.EntityClient.EntityParameter> 或 <xref:System.Data.Objects.ObjectParameter>。</span><span class="sxs-lookup"><span data-stu-id="5c888-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="5c888-122">您應該避免下列查詢模式，這樣會耗用查詢計畫快取中的位置，而這是不必要的：</span><span class="sxs-lookup"><span data-stu-id="5c888-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
-   <span data-ttu-id="5c888-123">變更為文字中的字母大小寫。</span><span class="sxs-lookup"><span data-stu-id="5c888-123">Changes to letter case in the text.</span></span>  
  
-   <span data-ttu-id="5c888-124">變更為泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="5c888-124">Changes to white space.</span></span>  
  
-   <span data-ttu-id="5c888-125">變更為常值。</span><span class="sxs-lookup"><span data-stu-id="5c888-125">Changes to literal values.</span></span>  
  
-   <span data-ttu-id="5c888-126">變更為註解內的文字。</span><span class="sxs-lookup"><span data-stu-id="5c888-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c888-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c888-127">See Also</span></span>  
 [<span data-ttu-id="5c888-128">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="5c888-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
