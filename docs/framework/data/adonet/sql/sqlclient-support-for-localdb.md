---
title: LocalDB 的 SqlClient 支援
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 55ab1346de6f5c14f15d01344a984c18edf30e02
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824476"
---
# <a name="sqlclient-support-for-localdb"></a><span data-ttu-id="cf718-102">LocalDB 的 SqlClient 支援</span><span class="sxs-lookup"><span data-stu-id="cf718-102">SqlClient Support for LocalDB</span></span>

<span data-ttu-id="cf718-103">本文討論如何連接至 LocalDB 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf718-103">This article discusses how to connect to a LocalDB database.</span></span> <span data-ttu-id="cf718-104">LocalDB 是 SQL Server 的輕量版本。</span><span class="sxs-lookup"><span data-stu-id="cf718-104">LocalDB is a lightweight version of SQL Server.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="cf718-105">備註</span><span class="sxs-lookup"><span data-stu-id="cf718-105">Remarks</span></span>
  
 <span data-ttu-id="cf718-106">摘要說明您可以使用 LocalDB 執行的作業：</span><span class="sxs-lookup"><span data-stu-id="cf718-106">To summarize what you can do with LocalDB:</span></span>  
  
- <span data-ttu-id="cf718-107">使用 sqllocaldb.exe 或您的 app.config 檔案來建立及啟動 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="cf718-107">Create and start LocalDB instances with sqllocaldb.exe or your app.config file.</span></span>  
  
- <span data-ttu-id="cf718-108">使用 sqlcmd.exe 可在 LocalDB 執行個體中新增和修改資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf718-108">Use sqlcmd.exe to add and modify databases in a LocalDB instance.</span></span> <span data-ttu-id="cf718-109">例如： `sqlcmd -S (localdb)\myinst` 。</span><span class="sxs-lookup"><span data-stu-id="cf718-109">For example, `sqlcmd -S (localdb)\myinst`.</span></span>  
  
- <span data-ttu-id="cf718-110">使用 `AttachDBFilename` 連接字串關鍵字，將資料庫新增至您的 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="cf718-110">Use the `AttachDBFilename` connection string keyword to add a database to your LocalDB instance.</span></span> <span data-ttu-id="cf718-111">使用 `AttachDBFilename` 時，如果您沒有使用 `Database` 連接字串關鍵字來指定資料庫的名稱，系統就會在應用程式關閉時從 LocalDB 執行個體中移除資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf718-111">When using `AttachDBFilename`, if you do not specify the name of the database with the `Database` connection string keyword, the database will be removed from the LocalDB instance when the application closes.</span></span>  
  
- <span data-ttu-id="cf718-112">請在連接字串中指定 LocalDB 執行個體。</span><span class="sxs-lookup"><span data-stu-id="cf718-112">Specify a LocalDB instance in your connection string.</span></span> <span data-ttu-id="cf718-113">例如，您的執行個體名稱是 `myInstance`，連接字串就會包含：</span><span class="sxs-lookup"><span data-stu-id="cf718-113">For example, your instance name is `myInstance`, the connection string would include:</span></span>  
  
    `server=(localdb)\\myInstance`  
  
 <span data-ttu-id="cf718-114">連線到 LocalDB 資料庫時，不允許使用 `User Instance=True`。</span><span class="sxs-lookup"><span data-stu-id="cf718-114">`User Instance=True` is not allowed when connecting to a LocalDB database.</span></span>  
  
<span data-ttu-id="cf718-115">如需安裝 LocalDB 的詳細資訊，請參閱 [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb)。</span><span class="sxs-lookup"><span data-stu-id="cf718-115">For information about installing LocalDB, see [SQL Server Express LocalDB](/sql/database-engine/configure-windows/sql-server-express-localdb).</span></span>
  
## <a name="programmatically-create-a-named-instance"></a><span data-ttu-id="cf718-116">以程式設計方式建立具名執行個體</span><span class="sxs-lookup"><span data-stu-id="cf718-116">Programmatically Create a Named Instance</span></span>  

 <span data-ttu-id="cf718-117">應用程式可以建立具名執行個體，並指定資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cf718-117">An application can create a named instance and specify a database as follows:</span></span>  
  
- <span data-ttu-id="cf718-118">指定要在 app.config 檔案中建立的 LocalDB 執行個體，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cf718-118">Specify the LocalDB instances to create in the app.config file, as follows.</span></span>  <span data-ttu-id="cf718-119">執行個體的版本號碼應該與您 LocalDB 安裝的版本號碼相同。</span><span class="sxs-lookup"><span data-stu-id="cf718-119">The version number of the instance should be the same as the version number of your LocalDB installation.</span></span>  
  
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
  
- <span data-ttu-id="cf718-120">使用 `server` 連接字串關鍵字來指定執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="cf718-120">Specify the name of the instance using the `server` connection string keyword.</span></span>  <span data-ttu-id="cf718-121">在 `server` 連接字串關鍵字中指定的執行個體名稱，必須與 app.config 檔案指定的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="cf718-121">The instance name specified in the `server` connection string keyword must match the name specified in the app.config file.</span></span>  
  
- <span data-ttu-id="cf718-122">使用 `AttachDBFilename` 連接字串關鍵字來指定 .MDF 檔案。</span><span class="sxs-lookup"><span data-stu-id="cf718-122">Use the `AttachDBFilename` connection string keyword to specify the .MDF file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf718-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="cf718-123">See also</span></span>

- [<span data-ttu-id="cf718-124">SQL Server 功能和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cf718-124">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)
- <span data-ttu-id="cf718-125">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="cf718-125">[ADO.NET Overview](../ado-net-overview.md)</span></span>
