---
title: ASP.NET 應用程式中的 SqlDependency
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.openlocfilehash: 2ec9415f63151443d5008fbce471fabeb89cdb91
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656167"
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="47d78-102">ASP.NET 應用程式中的 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="47d78-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="47d78-103">此節的範例示範如何利用 ASP.NET <xref:System.Web.Caching.SqlCacheDependency> 物件，間接使用 <xref:System.Data.SqlClient.SqlDependency>。</span><span class="sxs-lookup"><span data-stu-id="47d78-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="47d78-104"><xref:System.Web.Caching.SqlCacheDependency> 物件會使用 <xref:System.Data.SqlClient.SqlDependency> 來接聽通知，並正確更新快取。</span><span class="sxs-lookup"><span data-stu-id="47d78-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47d78-105">範例程式碼假設您已啟用查詢通知，方法是在 [啟用查詢通知](enabling-query-notifications.md)的情況下執行腳本。</span><span class="sxs-lookup"><span data-stu-id="47d78-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="47d78-106">關於範例應用程式</span><span class="sxs-lookup"><span data-stu-id="47d78-106">About the Sample Application</span></span>  
 <span data-ttu-id="47d78-107">此範例應用程式會使用單一 ASP.NET 網頁，在 <xref:System.Web.UI.WebControls.GridView> 控制項中顯示 **AdventureWorks** SQL Server 資料庫的產品資訊。</span><span class="sxs-lookup"><span data-stu-id="47d78-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="47d78-108">當頁面載入時，程式碼會將目前的時間寫入至 <xref:System.Web.UI.WebControls.Label> 控制項。</span><span class="sxs-lookup"><span data-stu-id="47d78-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="47d78-109">然後會定義 <xref:System.Web.Caching.SqlCacheDependency> 物件，並在 <xref:System.Web.Caching.Cache> 物件上設定屬性，以儲存快取資料長達三分鐘。</span><span class="sxs-lookup"><span data-stu-id="47d78-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="47d78-110">然後，程式碼會連線到資料庫並擷取資料。</span><span class="sxs-lookup"><span data-stu-id="47d78-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="47d78-111">當頁面載入且應用程式正在執行時，ASP.NET 將從快取中擷取資料，您可以透過注意頁面上的時間不會變更來驗證這一點。</span><span class="sxs-lookup"><span data-stu-id="47d78-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="47d78-112">如果監視的資料變更，ASP.NET 就會讓快取失效，並以全新的資料重新填入 `GridView` 控制項，進而更新 `Label` 控制項中顯示的時間。</span><span class="sxs-lookup"><span data-stu-id="47d78-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="47d78-113">建立範例應用程式</span><span class="sxs-lookup"><span data-stu-id="47d78-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="47d78-114">遵循下列步驟，以建立並執行範例應用程式：</span><span class="sxs-lookup"><span data-stu-id="47d78-114">Follow these steps to create and run the sample application:</span></span>  
  
1. <span data-ttu-id="47d78-115">建立新的 ASP.NET 網站。</span><span class="sxs-lookup"><span data-stu-id="47d78-115">Create a new ASP.NET Web site.</span></span>  
  
2. <span data-ttu-id="47d78-116">將 <xref:System.Web.UI.WebControls.Label> 和 <xref:System.Web.UI.WebControls.GridView> 控制項新增至 Default.aspx 頁面。</span><span class="sxs-lookup"><span data-stu-id="47d78-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3. <span data-ttu-id="47d78-117">開啟頁面的類別模組並新增下列指示詞：</span><span class="sxs-lookup"><span data-stu-id="47d78-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. <span data-ttu-id="47d78-118">在頁面的 `Page_Load` 事件中新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="47d78-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5. <span data-ttu-id="47d78-119">新增兩個協助程式方法：`GetConnectionString` 和 `GetSQL`。</span><span class="sxs-lookup"><span data-stu-id="47d78-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="47d78-120">定義的連接字串會使用整合式安全性。</span><span class="sxs-lookup"><span data-stu-id="47d78-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="47d78-121">您需要驗證所使用的帳戶具有必要的資料庫使用權限，且範例資料庫 **AdventureWorks** 已啟用通知。</span><span class="sxs-lookup"><span data-stu-id="47d78-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span>
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="47d78-122">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="47d78-122">Testing the Application</span></span>  
 <span data-ttu-id="47d78-123">應用程式會快取 Web 表單上顯示的資料，如果沒有任何活動，則每隔三分鐘就會重新整理一次。</span><span class="sxs-lookup"><span data-stu-id="47d78-123">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="47d78-124">如果資料庫發生變更，就會立即重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="47d78-124">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="47d78-125">從 Visual Studio 執行應用程式，以將頁面載入瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="47d78-125">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="47d78-126">顯示的快取重新整理時間表示上次重新整理快取的時間。</span><span class="sxs-lookup"><span data-stu-id="47d78-126">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="47d78-127">等候三分鐘，然後重新整理頁面，即會導致回傳事件發生。</span><span class="sxs-lookup"><span data-stu-id="47d78-127">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="47d78-128">請注意，頁面上顯示的時間已經變更。</span><span class="sxs-lookup"><span data-stu-id="47d78-128">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="47d78-129">如果您在三分鐘內重新整理頁面，則頁面上顯示的時間將維持不變。</span><span class="sxs-lookup"><span data-stu-id="47d78-129">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="47d78-130">現在，使用 Transact-SQL UPDATE 命令來更新資料庫中的資料，並重新整理頁面。</span><span class="sxs-lookup"><span data-stu-id="47d78-130">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="47d78-131">顯示的時間現在表示已使用資料庫的新資料來重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="47d78-131">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="47d78-132">請注意，雖然快取已更新，但在發生回傳事件之前，頁面上顯示的時間不會變更。</span><span class="sxs-lookup"><span data-stu-id="47d78-132">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  

## <a name="distributed-cache-synchronization-using-sql-dependency"></a><span data-ttu-id="47d78-133">使用 SQL 相依性的分散式快取同步處理</span><span class="sxs-lookup"><span data-stu-id="47d78-133">Distributed cache synchronization using SQL Dependency</span></span>

<span data-ttu-id="47d78-134">某些協力廠商分散式快取（例如 [NCache](https://www.alachisoft.com/ncache) ）提供使用 [sql](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html)相依性來同步處理 SQL database 和快取的支援。</span><span class="sxs-lookup"><span data-stu-id="47d78-134">Some of the third-party distributed caches such as [NCache](https://www.alachisoft.com/ncache) provide support to synchronize the SQL database and cache using [SQL Dependency](https://www.alachisoft.com/resources/docs/ncache/prog-guide/sql-dependency.html).</span></span> <span data-ttu-id="47d78-135">如需詳細資訊和原始程式碼執行範例，請參閱 [分散式](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency)快取 SQL 相依性範例。</span><span class="sxs-lookup"><span data-stu-id="47d78-135">For more information and an example source code implementation, see [Distributed cache SQL Dependency sample](https://github.com/Alachisoft/NCache-Samples/tree/master/dotnet/Dependencies/SQLDependency).</span></span>

## <a name="see-also"></a><span data-ttu-id="47d78-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47d78-136">See also</span></span>

- [<span data-ttu-id="47d78-137">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="47d78-137">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- <span data-ttu-id="47d78-138">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="47d78-138">[ADO.NET Overview](../ado-net-overview.md)</span></span>
