---
title: LocalDB 的 SqlClient 支援
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 841c455605b0b32668d26cab16a6207dc1c0f716
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203419"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="9526d-102">LocalDB 的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="9526d-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="9526d-103">從 SQL Server 代號名稱 Denali 開始，將會提供稱為 LocalDB 的輕量版 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="9526d-103">Beginning in SQL Server code name Denali, a lightweight version of SQL Server, called LocalDB, will be available.</span></span> <span data-ttu-id="9526d-104">此主題將討論如何連線到 LocalDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9526d-104">This topic discusses how to connect to a LocalDB database.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9526d-105">備註</span><span class="sxs-lookup"><span data-stu-id="9526d-105">Remarks</span></span>  

 <span data-ttu-id="9526d-106">如需 LocalDB 的詳細資訊，包括如何安裝 LocalDB 和設定 LocalDB 執行個體，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="9526d-106">For more information about LocalDB, including how to install LocalDB and configure your LocalDB instance, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="9526d-107">摘要說明您可以使用 LocalDB 執行的作業：</span><span class="sxs-lookup"><span data-stu-id="9526d-107">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="9526d-108">使用 sqllocaldb.exe 或您的 app.config 檔案來建立及啟動 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9526d-108">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="9526d-109">使用 sqlcmd.exe 可在 LocalDB 執行個體中新增和修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="9526d-109">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="9526d-110">例如 `sqlcmd -S (localdb)\myinst`。</span><span class="sxs-lookup"><span data-stu-id="9526d-110">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="9526d-111">使用 `AttachDBFilename` 連接字串關鍵字，將資料庫新增至您的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9526d-111">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="9526d-112">使用 `AttachDBFilename` 時，如果您沒有使用 `Database` 連接字串關鍵字來指定資料庫的名稱，系統就會在應用程式關閉時從 LocalDB 執行個體中移除資料庫。</span><span class="sxs-lookup"><span data-stu-id="9526d-112">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="9526d-113">請在連接字串中指定 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9526d-113">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="9526d-114">例如，您的執行個體名稱是 `myInstance`，連接字串就會包含：</span><span class="sxs-lookup"><span data-stu-id="9526d-114">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="9526d-115">連線到 LocalDB 資料庫時，不允許使用 `User Instance=True`。</span><span class="sxs-lookup"><span data-stu-id="9526d-115">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
 <span data-ttu-id="9526d-116">您可以從 [Microsoft SQL Server 2012 功能套件](https://www.microsoft.com/download/en/details.aspx?id=29065)下載 LocalDB。</span><span class="sxs-lookup"><span data-stu-id="9526d-116">You can download LocalDB from [Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065).</span></span> <span data-ttu-id="9526d-117">如果您將使用 sqlcmd.exe 來修改 LocalDB 執行個體中的資料，您將需要 SQL Server 2012 中的 sqlcmd，您也可以從 SQL Server 2012 功能套件取得 sqlcmd。</span><span class="sxs-lookup"><span data-stu-id="9526d-117">If you will use sqlcmd.exe to modify data in your LocalDB instance, you will need sqlcmd from SQL Server 2012, which you can also get from the SQL Server 2012 Feature Pack.</span></span>  
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="9526d-118">以程式設計方式建立具名執行個體</span><span class="sxs-lookup"><span data-stu-id="9526d-118">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="9526d-119">應用程式可以建立具名執行個體，並指定資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9526d-119">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="9526d-120">指定要在 app.config 檔案中建立的 LocalDB 執行個體，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9526d-120">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="9526d-121">執行個體的版本號碼應該與您 LocalDB 安裝的版本號碼相同。</span><span class="sxs-lookup"><span data-stu-id="9526d-121">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="9526d-122">使用 `server` 連接字串關鍵字來指定執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="9526d-122">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="9526d-123">在 `server` 連接字串關鍵字中指定的執行個體名稱，必須與 app.config 檔案指定的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="9526d-123">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="9526d-124">使用 `AttachDBFilename` 連接字串關鍵字來指定 .MDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="9526d-124">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9526d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9526d-125">See also</span></span>

- [<span data-ttu-id="9526d-126">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9526d-126">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- <span data-ttu-id="9526d-127">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="9526d-127">[ADO.NET Overview](../ado-net-overview.md)</span></span>
