---
title: 多層式架構和遠端應用程式以及 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 70f6a6ee91761196b62b34f6dde73d11dbe6b39d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200598"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="fb565-102">多層式架構和遠端應用程式以及 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fb565-102">N-Tier and Remote Applications with LINQ to SQL</span></span>

<span data-ttu-id="fb565-103">您可以建立使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 N-Tier 或多層應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb565-103">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="fb565-104">一般而言， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 資料內容、實體類別和查詢結構邏輯都位於仲介層，作為資料存取層 (DAL) 。</span><span class="sxs-lookup"><span data-stu-id="fb565-104">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="fb565-105">商務邏輯以及任何非持續性資料則可完全實作在實體的部分類別和方法和資料內容，或可以實作在另外的類別中。</span><span class="sxs-lookup"><span data-stu-id="fb565-105">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>

 <span data-ttu-id="fb565-106">用戶端或展示層會在中介層的遠端介面上呼叫方法，而該層上的 DAL 將執行對應到 <xref:System.Data.Linq.DataContext> 方法的查詢或預存程序。</span><span class="sxs-lookup"><span data-stu-id="fb565-106">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="fb565-107">中介層一般會將資料以實體或 Proxy 物件的 XML 表示傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="fb565-107">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>

 <span data-ttu-id="fb565-108">在中介層上，實體是由資料內容建立的，資料內容會追蹤其狀態，以及管理資料庫的延後載入和提交變更。</span><span class="sxs-lookup"><span data-stu-id="fb565-108">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="fb565-109">這些實體會「附加」到 `DataContext`。</span><span class="sxs-lookup"><span data-stu-id="fb565-109">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="fb565-110">不過，實體在透過序列化 (Serialization) 傳送到另一層之後，就會中斷連結，表示 `DataContext` 不再追蹤其狀態。</span><span class="sxs-lookup"><span data-stu-id="fb565-110">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="fb565-111">用戶端傳回進行更新的實體必須重新附加到資料內容，如此 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 才能將變更提交至資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb565-111">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="fb565-112">在開放式並行存取檢查需要的情況下，用戶端會負責將原始值和/或時間戳記送回中介層。</span><span class="sxs-lookup"><span data-stu-id="fb565-112">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>

 <span data-ttu-id="fb565-113">在 ASP.NET 應用程式中，<xref:System.Web.UI.WebControls.LinqDataSource> 會負責這其中大多數複雜的作業。</span><span class="sxs-lookup"><span data-stu-id="fb565-113">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="fb565-114">如需詳細資訊，請參閱 [LinqDataSource Web 服務器控制項總覽](/previous-versions/aspnet/bb547113(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="fb565-114">For more information, see [LinqDataSource Web Server Control Overview](/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fb565-115">其他資源</span><span class="sxs-lookup"><span data-stu-id="fb565-115">Additional Resources</span></span>

 <span data-ttu-id="fb565-116">如需如何實作使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 N-Tier 應用程式，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="fb565-116">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>

- [<span data-ttu-id="fb565-117">LINQ to SQL 多層式架構與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fb565-117">LINQ to SQL N-Tier with ASP.NET</span></span>](linq-to-sql-n-tier-with-aspnet.md)

- [<span data-ttu-id="fb565-118">LINQ to SQL 多層式架構與 Web 服務</span><span class="sxs-lookup"><span data-stu-id="fb565-118">LINQ to SQL N-Tier with Web Services</span></span>](linq-to-sql-n-tier-with-web-services.md)

- [<span data-ttu-id="fb565-119">實作多層式架構 (N-Tier) 商務邏輯</span><span class="sxs-lookup"><span data-stu-id="fb565-119">Implementing N-Tier Business Logic</span></span>](implementing-business-logic-linq-to-sql.md)

- [<span data-ttu-id="fb565-120">多層式架構應用程式中的資料擷取和 CUD 作業 (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="fb565-120">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](data-retrieval-and-cud-operations-in-n-tier-applications.md)

 <span data-ttu-id="fb565-121">如需使用 ADO.NET 資料集之多層式應用程式的詳細資訊，請參閱使用多 [層式應用程式中的資料集](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)。</span><span class="sxs-lookup"><span data-stu-id="fb565-121">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb565-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb565-122">See also</span></span>

- [<span data-ttu-id="fb565-123">背景資訊</span><span class="sxs-lookup"><span data-stu-id="fb565-123">Background Information</span></span>](background-information.md)
