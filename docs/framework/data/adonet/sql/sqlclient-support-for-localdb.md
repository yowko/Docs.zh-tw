---
title: LocalDB 的 SqlClient 支援
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 1ef75def3f3de44b5e23cb1197a4410dcf6b547f
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492635"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="6b0eb-102">LocalDB 的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="6b0eb-102">SqlClient Support for LocalDB</span></span>
<span data-ttu-id="6b0eb-103">從 SQL Server 代號 Denali，輕量版的 SQL Server，名為 LocalDB，將可。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="6b0eb-104">本主題討論如何連接到 LocalDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b0eb-105">備註</span><span class="sxs-lookup"><span data-stu-id="6b0eb-105">Remarks</span></span>  
 <span data-ttu-id="6b0eb-106">如需有關 LocalDB 的詳細資訊，包括如何安裝 LocalDB 和設定您的 LocalDB 執行個體，請參閱 SQL Server 線上叢書 》。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="6b0eb-107">LocalDB 功能摘要：</span><span class="sxs-lookup"><span data-stu-id="6b0eb-107">To summarize what you can do with LocalDB:</span></span>  
  
-   <span data-ttu-id="6b0eb-108">以 sqllocaldb.exe 或您的 app.config 檔建立及啟動 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
-   <span data-ttu-id="6b0eb-109">使用 sqlcmd.exe 新增及修改 LocalDB 執行個體中的資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="6b0eb-110">例如， `sqlcmd -S (localdb)\myinst`。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
-   <span data-ttu-id="6b0eb-111">使用 `AttachDBFilename` 連接字串關鍵字將資料庫新增到 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="6b0eb-112">使用 `AttachDBFilename`時，如果您不以 `Database` 連接字串關鍵字指定資料庫名稱，當應用程式關閉時，會將資料庫從 LocalDB 執行個體中移除。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
-   <span data-ttu-id="6b0eb-113">在連接字串中指定 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="6b0eb-114">例如，您的執行個體名稱是 `myInstance`，連接字串將包括：</span><span class="sxs-lookup"><span data-stu-id="6b0eb-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 <span data-ttu-id="6b0eb-115">連接至 LocalDB 資料庫時不允許`User Instance=True` 。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="6b0eb-116">您可以下載從 LocalDB [Microsoft SQL Server 2012 功能套件](https://www.microsoft.com/download/en/details.aspx?id=29065)。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="6b0eb-117">如果您將使用 sqlcmd.exe 來修改 LocalDB 執行個體中的資料，您必須從 SQL Server 2012，您也可以從 SQL Server 2012 功能套件取得 sqlcmd。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="6b0eb-118">以程式設計方式建立具名執行個體</span><span class="sxs-lookup"><span data-stu-id="6b0eb-118">Programmatically Create a Named Instance</span></span>  
 <span data-ttu-id="6b0eb-119">應用程式可以建立具名執行個體並指定資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6b0eb-119">An application can create a named instance and specify a database as follows:</span></span>  
  
-   <span data-ttu-id="6b0eb-120">在 app.config 檔中指定要建立的 LocalDB 執行個體，如下所示。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="6b0eb-121">執行個體的版本號碼應與 LocalDB 安裝的版本號碼相同。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="6b0eb-122">使用 `server` 連接字串關鍵字指定執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="6b0eb-123">在 `server` 連接字串關鍵字中指定的執行個體名稱，必須與 app.config 檔中指定的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
-   <span data-ttu-id="6b0eb-124">使用 `AttachDBFilename` 連接字串關鍵字來指定 .MDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="6b0eb-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b0eb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b0eb-125">See Also</span></span>  
 [<span data-ttu-id="6b0eb-126">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6b0eb-126">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [<span data-ttu-id="6b0eb-127">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6b0eb-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
