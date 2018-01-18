---
title: "在 SQL Server 中啟用跨資料庫存取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2a31bddfec44ad4b33f1b595c2746d1a0e841b82
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="fb5ab-102">在 SQL Server 中啟用跨資料庫存取</span><span class="sxs-lookup"><span data-stu-id="fb5ab-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="fb5ab-103">當一個資料庫中的程序是依照另一個資料庫中的物件而定時，就會發生跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="fb5ab-104">跨資料庫擁有權鏈結的運作方式與單一資料庫內的擁有權鏈結相同，但未中斷的擁有權鏈結需要所有的物件擁有者都對應至相同的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="fb5ab-105">如果來源資料庫中的來源物件以及目標資料庫中的目標物件是由相同的登入帳戶所擁有，則 SQL Server 不會檢查目標物件上的權限。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="fb5ab-106">預設關閉</span><span class="sxs-lookup"><span data-stu-id="fb5ab-106">Off By Default</span></span>  
 <span data-ttu-id="fb5ab-107">跨資料庫的擁有權鏈結預設會關閉。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="fb5ab-108">Microsoft 建議您停用跨資料庫的擁有權鏈結，因為這項功能會使您暴露於下列的安全性風險：</span><span class="sxs-lookup"><span data-stu-id="fb5ab-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
-   <span data-ttu-id="fb5ab-109">資料庫擁有者、`db_ddladmin` 的成員或者 `db_owners` 資料庫角色都可以建立由其他使用者擁有的物件。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="fb5ab-110">這些物件可能會以其他資料庫中的物件為目標。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="fb5ab-111">這表示如果啟用跨資料庫的擁有權鏈結，則必須完全信任這些使用者使用所有資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
-   <span data-ttu-id="fb5ab-112">具有 CREATE DATABASE 權限的使用者可以建立新的資料庫及附加現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="fb5ab-113">如果啟用跨資料庫擁有權鏈結，這些使用者即可從其新建立或附加的資料庫，存取其他資料庫中他們可能並不擁有權限的物件。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="fb5ab-114">啟用跨資料庫擁有權鏈結</span><span class="sxs-lookup"><span data-stu-id="fb5ab-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="fb5ab-115">只有在可以完全信任高權限使用者的環境中，才應該啟用跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="fb5ab-116">這項功能可在所有資料庫的安裝期間設定，或者使用 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 命令 `sp_configure` 和 `ALTER DATABASE` 選擇性地針對特定的資料庫設定。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-116">It can be configured during setup for all databases, or selectively for specific databases using the [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="fb5ab-117">若要選擇性地設定跨資料庫擁有權鏈結，請使用 `sp_configure` 關閉伺服器的這項功能。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="fb5ab-118">然後使用具有 SET DB_CHAINING ON 的 ALTER DATABASE 命令，僅針對需要此功能的資料庫設定跨資料庫擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="fb5ab-119">下列範例會開啟所有資料庫的跨資料庫擁有權鏈結：</span><span class="sxs-lookup"><span data-stu-id="fb5ab-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="fb5ab-120">下列範例會開啟特定資料庫的跨資料庫擁有權鏈結：</span><span class="sxs-lookup"><span data-stu-id="fb5ab-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="fb5ab-121">動態 SQL</span><span class="sxs-lookup"><span data-stu-id="fb5ab-121">Dynamic SQL</span></span>  
 <span data-ttu-id="fb5ab-122">在執行動態建立之 SQL 陳述式的情況中，無法使用跨資料庫擁有權鏈結，除非兩個資料庫中存在相同的使用者。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="fb5ab-123">您可以在 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 中建立存取其他資料庫資料的預存程序，並使用存在於兩個資料庫中的憑證來簽署程序，藉此解決上述問題。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-123">You can work around this in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="fb5ab-124">如此可以讓使用者存取該程序所使用的資料庫資源，而不必為其授與資料庫存取權或權限。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="fb5ab-125">外部資源</span><span class="sxs-lookup"><span data-stu-id="fb5ab-125">External Resources</span></span>  
 <span data-ttu-id="fb5ab-126">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="fb5ab-127">資源</span><span class="sxs-lookup"><span data-stu-id="fb5ab-127">Resource</span></span>|<span data-ttu-id="fb5ab-128">描述</span><span class="sxs-lookup"><span data-stu-id="fb5ab-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="fb5ab-129">[使用 EXECUTE AS 擴充資料庫模擬](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx)和[Cross DB Ownership Chaining 選項](http://msdn.microsoft.com/library/ms188694.aspx)[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]線上叢書 》。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-129">[Extending Database Impersonation by Using EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) and [Cross DB Ownership Chaining Option](http://msdn.microsoft.com/library/ms188694.aspx)[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>|<span data-ttu-id="fb5ab-130">說明如何針對 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 的執行個體設定跨資料庫擁有權鏈結的主題。</span><span class="sxs-lookup"><span data-stu-id="fb5ab-130">Topics describe how to configure cross-database ownership chaining for an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb5ab-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="fb5ab-131">See Also</span></span>  
 [<span data-ttu-id="fb5ab-132">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="fb5ab-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="fb5ab-133">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="fb5ab-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="fb5ab-134">在 SQL Server 中使用預存程序來管理權限</span><span class="sxs-lookup"><span data-stu-id="fb5ab-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="fb5ab-135">在 SQL Server 中撰寫安全的動態 SQL</span><span class="sxs-lookup"><span data-stu-id="fb5ab-135">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="fb5ab-136">在 SQL Server 中簽署預存程序</span><span class="sxs-lookup"><span data-stu-id="fb5ab-136">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="fb5ab-137">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="fb5ab-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
