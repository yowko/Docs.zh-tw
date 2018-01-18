---
title: "ASP.NET 應用程式中的 SqlDependency"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3481d0f0be5a52b33125e2a92849f402cce82d93
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="sqldependency-in-an-aspnet-application"></a><span data-ttu-id="c9102-102">ASP.NET 應用程式中的 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="c9102-102">SqlDependency in an ASP.NET Application</span></span>
<span data-ttu-id="c9102-103">本節中的範例將顯示如何藉由使用 ASP.NET <xref:System.Data.SqlClient.SqlDependency> 物件，間接使用 <xref:System.Web.Caching.SqlCacheDependency>。</span><span class="sxs-lookup"><span data-stu-id="c9102-103">The example in this section shows how to use <xref:System.Data.SqlClient.SqlDependency> indirectly by leveraging the ASP.NET <xref:System.Web.Caching.SqlCacheDependency> object.</span></span> <span data-ttu-id="c9102-104"><xref:System.Web.Caching.SqlCacheDependency> 物件會使用 <xref:System.Data.SqlClient.SqlDependency> 來接聽通知並正確地更新快取。</span><span class="sxs-lookup"><span data-stu-id="c9102-104">The <xref:System.Web.Caching.SqlCacheDependency> object uses a <xref:System.Data.SqlClient.SqlDependency> to listen for notifications and correctly update the cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9102-105">範例程式碼假設您已執行中的指令碼來啟用查詢通知[啟用查詢通知](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)。</span><span class="sxs-lookup"><span data-stu-id="c9102-105">The sample code assumes that you have enabled query notifications by executing the scripts in [Enabling Query Notifications](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md).</span></span>  
  
## <a name="about-the-sample-application"></a><span data-ttu-id="c9102-106">關於範例應用程式</span><span class="sxs-lookup"><span data-stu-id="c9102-106">About the Sample Application</span></span>  
 <span data-ttu-id="c9102-107">範例應用程式使用單一 ASP.NET 網頁，來顯示產品資訊**AdventureWorks**中的 SQL Server 資料庫<xref:System.Web.UI.WebControls.GridView>控制項。</span><span class="sxs-lookup"><span data-stu-id="c9102-107">The sample application uses a single ASP.NET Web page to display product information from the **AdventureWorks** SQL Server database in a <xref:System.Web.UI.WebControls.GridView> control.</span></span> <span data-ttu-id="c9102-108">載入頁面時，此程式碼會將目前時間寫入 <xref:System.Web.UI.WebControls.Label> 控制項。</span><span class="sxs-lookup"><span data-stu-id="c9102-108">When the page loads, the code writes the current time to a <xref:System.Web.UI.WebControls.Label> control.</span></span> <span data-ttu-id="c9102-109">然後會定義 <xref:System.Web.Caching.SqlCacheDependency> 物件，並在 <xref:System.Web.Caching.Cache> 物件上設定屬性，以儲存快取資料長達三分鐘。</span><span class="sxs-lookup"><span data-stu-id="c9102-109">It then defines a <xref:System.Web.Caching.SqlCacheDependency> object and sets properties on the <xref:System.Web.Caching.Cache> object to store the cache data for up to three minutes.</span></span> <span data-ttu-id="c9102-110">然後，此程式碼會連接到資料庫並擷取資料。</span><span class="sxs-lookup"><span data-stu-id="c9102-110">The code then connects to the database and retrieves the data.</span></span> <span data-ttu-id="c9102-111">當頁面已載入而且應用程式正在執行時，ASP.NET 將從快取中擷取資料，而且您可以注意頁面上的時間沒有變更來確認這點。</span><span class="sxs-lookup"><span data-stu-id="c9102-111">When the page is loaded and the application is running ASP.NET will retrieve data from the cache, which you can verify by noting that the time on the page does not change.</span></span> <span data-ttu-id="c9102-112">如果正在監視的資料有變更，ASP.NET 會讓快取無效並將新資料重新填入 `GridView` 控制項，而且更新 `Label` 控制項中顯示的時間。</span><span class="sxs-lookup"><span data-stu-id="c9102-112">If the data being monitored changes, ASP.NET invalidates the cache and repopulate the `GridView` control with fresh data, updating the time displayed in the `Label` control.</span></span>  
  
## <a name="creating-the-sample-application"></a><span data-ttu-id="c9102-113">建立範例應用程式</span><span class="sxs-lookup"><span data-stu-id="c9102-113">Creating the Sample Application</span></span>  
 <span data-ttu-id="c9102-114">請遵循下列步驟來建立並執行範例應用程式：</span><span class="sxs-lookup"><span data-stu-id="c9102-114">Follow these steps to create and run the sample application:</span></span>  
  
1.  <span data-ttu-id="c9102-115">建立新的 ASP.NET 網站。</span><span class="sxs-lookup"><span data-stu-id="c9102-115">Create a new ASP.NET Web site.</span></span>  
  
2.  <span data-ttu-id="c9102-116">將 <xref:System.Web.UI.WebControls.Label> 和 <xref:System.Web.UI.WebControls.GridView> 控制項加入至 Default.aspx 頁面。</span><span class="sxs-lookup"><span data-stu-id="c9102-116">Add a <xref:System.Web.UI.WebControls.Label> and a <xref:System.Web.UI.WebControls.GridView> control to the Default.aspx page.</span></span>  
  
3.  <span data-ttu-id="c9102-117">開啟頁面的類別模組，並加入下列指示詞：</span><span class="sxs-lookup"><span data-stu-id="c9102-117">Open the page's class module and add the following directives:</span></span>  
  
    ```vb  
    Option Strict On  
    Option Explicit On  
  
    Imports System.Data.SqlClient  
    ```  
  
    ```csharp  
    using System.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4.  <span data-ttu-id="c9102-118">將下列程式碼加入至頁面的 `Page_Load` 事件：</span><span class="sxs-lookup"><span data-stu-id="c9102-118">Add the following code in the page's `Page_Load` event:</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#1)]
     [!code-vb[DataWorks SqlDependency.AspNet#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#1)]  
  
5.  <span data-ttu-id="c9102-119">加入兩個 Helper 方法：`GetConnectionString` 及 `GetSQL`。</span><span class="sxs-lookup"><span data-stu-id="c9102-119">Add two helper methods, `GetConnectionString` and `GetSQL`.</span></span> <span data-ttu-id="c9102-120">定義的連接字串會使用整合安全性。</span><span class="sxs-lookup"><span data-stu-id="c9102-120">The connection string defined uses integrated security.</span></span> <span data-ttu-id="c9102-121">您必須確認您使用的帳戶具有必要的資料庫使用權限，且範例資料庫中， **AdventureWorks**，已啟用通知。</span><span class="sxs-lookup"><span data-stu-id="c9102-121">You will need to verify that the account you are using has the necessary database permissions and that the sample database, **AdventureWorks**, has notifications enabled.</span></span> <span data-ttu-id="c9102-122">如需詳細資訊，請參閱[特殊考量時使用查詢通知](http://msdn.microsoft.com/en-us/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7)。</span><span class="sxs-lookup"><span data-stu-id="c9102-122">For more information, see [Special Considerations When Using Query Notifications](http://msdn.microsoft.com/en-us/a83c8dc8-4fb9-4ffd-a2a5-c07cf4a203c7).</span></span>  
  
     [!code-csharp[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/CS/Default.aspx.cs#2)]
     [!code-vb[DataWorks SqlDependency.AspNet#2](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlDependency.AspNet/VB/Default.aspx.vb#2)]  
  
### <a name="testing-the-application"></a><span data-ttu-id="c9102-123">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="c9102-123">Testing the Application</span></span>  
 <span data-ttu-id="c9102-124">應用程式會快取顯示在 Web Form 上的資料，並每隔三分鐘重新整理它一次 (如果沒有任何活動的話)。</span><span class="sxs-lookup"><span data-stu-id="c9102-124">The application caches the data displayed on the Web form and refreshes it every three minutes if there is no activity.</span></span> <span data-ttu-id="c9102-125">如果資料庫發生變更，就會立即重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="c9102-125">If a change occurs to the database, the cache is refreshed immediately.</span></span> <span data-ttu-id="c9102-126">從 Visual Studio 執行應用程式，以便將頁面載入瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="c9102-126">Run the application from Visual Studio, which loads the page into the browser.</span></span> <span data-ttu-id="c9102-127">顯示的快取重新整理時間表示上次重新整理快取的時間。</span><span class="sxs-lookup"><span data-stu-id="c9102-127">The cache refresh time displayed indicates when the cache was last refreshed.</span></span> <span data-ttu-id="c9102-128">等候三分鐘，然後重新整理頁面，以便發生回傳事件。</span><span class="sxs-lookup"><span data-stu-id="c9102-128">Wait three minutes, and then refresh the page, causing a postback event to occur.</span></span> <span data-ttu-id="c9102-129">請注意，顯示在頁面上的時間已經變更。</span><span class="sxs-lookup"><span data-stu-id="c9102-129">Note that the time displayed on the page has changed.</span></span> <span data-ttu-id="c9102-130">如果您在三分鐘以內便重新整理頁面，顯示在頁面上的時間將維持不變。</span><span class="sxs-lookup"><span data-stu-id="c9102-130">If you refresh the page in less than three minutes, the time displayed on the page will remain the same.</span></span>  
  
 <span data-ttu-id="c9102-131">現在，請使用 Transact-SQL UPDATE 命令來更新資料庫中的資料，並重新整理頁面。</span><span class="sxs-lookup"><span data-stu-id="c9102-131">Now update the data in the database, using a Transact-SQL UPDATE command and refresh the page.</span></span> <span data-ttu-id="c9102-132">此時顯示的時間表示已使用資料庫的新資料來重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="c9102-132">The time displayed now indicates that the cache was refreshed with the new data from the database.</span></span> <span data-ttu-id="c9102-133">請注意，雖然快取已更新，但是顯示在頁面上的時間要等到發生回傳事件之後才會變更。</span><span class="sxs-lookup"><span data-stu-id="c9102-133">Note that although the cache is updated, the time displayed on the page does not change until a postback event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9102-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9102-134">See Also</span></span>  
 [<span data-ttu-id="c9102-135">SQL Server 中的查詢通知</span><span class="sxs-lookup"><span data-stu-id="c9102-135">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)  
 [<span data-ttu-id="c9102-136">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c9102-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
