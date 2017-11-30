---
title: "使用預存程序管理 SQL Server 中的權限"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 806cd23060dde3f7b466df0d4ce39162353380e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a><span data-ttu-id="8360e-102">使用預存程序管理 SQL Server 中的權限</span><span class="sxs-lookup"><span data-stu-id="8360e-102">Managing Permissions with Stored Procedures in SQL Server</span></span>
<span data-ttu-id="8360e-103">為資料庫建立多重防線的方法之一，就是使用預存程序 (Stored Procedure) 或使用者定義的函式來實作所有資料存取。</span><span class="sxs-lookup"><span data-stu-id="8360e-103">One method of creating multiple lines of defense around your database is to implement all data access using stored procedures or user-defined functions.</span></span> <span data-ttu-id="8360e-104">您可以撤銷或拒絕基礎物件 (例如資料表) 的所有權限，然後在預存程序上授與 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="8360e-104">You revoke or deny all permissions to underlying objects, such as tables, and grant EXECUTE permissions on stored procedures.</span></span> <span data-ttu-id="8360e-105">如此即可有效地在資料和資料庫物件周圍建立安全性防線。</span><span class="sxs-lookup"><span data-stu-id="8360e-105">This effectively creates a security perimeter around your data and database objects.</span></span>  
  
## <a name="stored-procedure-benefits"></a><span data-ttu-id="8360e-106">預存程序的優點</span><span class="sxs-lookup"><span data-stu-id="8360e-106">Stored Procedure Benefits</span></span>  
 <span data-ttu-id="8360e-107">預存程序有下列優點：</span><span class="sxs-lookup"><span data-stu-id="8360e-107">Stored procedures have the following benefits:</span></span>  
  
-   <span data-ttu-id="8360e-108">可以將資料邏輯和商務規則 (Business Rule) 加以封裝，如此使用者就只能以開發人員和資料庫系統管理員預期的方式來存取資料及物件。</span><span class="sxs-lookup"><span data-stu-id="8360e-108">Data logic and business rules can be encapsulated so that users can access data and objects only in ways that developers and database administrators intend.</span></span>  
  
-   <span data-ttu-id="8360e-109">可以使用會驗證所有使用者輸入的參數化預存程序來防堵 SQL 插入式攻擊。</span><span class="sxs-lookup"><span data-stu-id="8360e-109">Parameterized stored procedures that validate all user input can be used to thwart SQL injection attacks.</span></span> <span data-ttu-id="8360e-110">如果有使用動態 SQL，請務必將命令參數化，也絕對不要在查詢字串中直接包含參數值。</span><span class="sxs-lookup"><span data-stu-id="8360e-110">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into a query string.</span></span>  
  
-   <span data-ttu-id="8360e-111">可以拒絕臨機操作 (Ad Hoc) 的查詢和資料修改作業。</span><span class="sxs-lookup"><span data-stu-id="8360e-111">Ad hoc queries and data modifications can be disallowed.</span></span> <span data-ttu-id="8360e-112">如此可避免使用者因惡意或不慎而損毀資料，或執行會降低伺服器或網路效能的查詢。</span><span class="sxs-lookup"><span data-stu-id="8360e-112">This prevents users from maliciously or inadvertently destroying data or executing queries that impair performance on the server or the network.</span></span>  
  
-   <span data-ttu-id="8360e-113">可以處理程序程式碼中的錯誤，而不必將錯誤直接傳遞至用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="8360e-113">Errors can be handled in procedure code without being passed directly to client applications.</span></span> <span data-ttu-id="8360e-114">如此可避免傳回可能助長探查攻擊的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="8360e-114">This prevents error messages from being returned that could aid in a probing attack.</span></span> <span data-ttu-id="8360e-115">請在伺服器上記錄及處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="8360e-115">Log errors and handle them on the server.</span></span>  
  
-   <span data-ttu-id="8360e-116">預存程序只需寫入一次，即可由許多應用程式存取。</span><span class="sxs-lookup"><span data-stu-id="8360e-116">Stored procedures can be written once, and accessed by many applications.</span></span>  
  
-   <span data-ttu-id="8360e-117">用戶端應用程式不需要對基礎資料結構有任何了解。</span><span class="sxs-lookup"><span data-stu-id="8360e-117">Client applications do not need to know anything about the underlying data structures.</span></span> <span data-ttu-id="8360e-118">您可以對預存程序程式碼進行變更，而不需變更用戶端應用程式，只要這些變更不會影響參數清單或傳回的資料型別即可。</span><span class="sxs-lookup"><span data-stu-id="8360e-118">Stored procedure code can be changed without requiring changes in client applications as long as the changes do not affect parameter lists or returned data types.</span></span>  
  
-   <span data-ttu-id="8360e-119">預存程序可以將多項作業結合成單一的程序呼叫，藉此降低網路流量。</span><span class="sxs-lookup"><span data-stu-id="8360e-119">Stored procedures can reduce network traffic by combining multiple operations into one procedure call.</span></span>  
  
## <a name="stored-procedure-execution"></a><span data-ttu-id="8360e-120">預存程序的執行</span><span class="sxs-lookup"><span data-stu-id="8360e-120">Stored Procedure Execution</span></span>  
 <span data-ttu-id="8360e-121">預存程序可以利用擁有權鏈結提供對資料的存取，如此使用者即使沒有明確的權限，也可以存取資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="8360e-121">Stored procedures take advantage of ownership chaining to provide access to data so that users do not need to have explicit permission to access database objects.</span></span> <span data-ttu-id="8360e-122">當循序彼此存取的物件是由同一個使用者所擁有時，即構成擁有權鏈結。</span><span class="sxs-lookup"><span data-stu-id="8360e-122">An ownership chain exists when objects that access each other sequentially are owned by the same user.</span></span> <span data-ttu-id="8360e-123">例如，預存程序可以呼叫其他的預存程序，或者預存程序也可以存取多個資料表。</span><span class="sxs-lookup"><span data-stu-id="8360e-123">For example, a stored procedure can call other stored procedures, or a stored procedure can access multiple tables.</span></span> <span data-ttu-id="8360e-124">如果執行鏈結中的所有物件都具有相同的擁有者，則 SQL Server 只會檢查呼叫端的 EXECUTE 權限，而不會檢查呼叫端對其他物件的權限。</span><span class="sxs-lookup"><span data-stu-id="8360e-124">If all objects in the chain of execution have the same owner, then SQL Server only checks the EXECUTE permission for the caller, not the caller's permissions on other objects.</span></span> <span data-ttu-id="8360e-125">因此您只需要授與預存程序上的 EXECUTE 權限，而可以撤銷或拒絕基礎資料表上的所有權限。</span><span class="sxs-lookup"><span data-stu-id="8360e-125">Therefore you need to grant only EXECUTE permissions on stored procedures; you can revoke or deny all permissions on the underlying tables.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="8360e-126">最佳作法</span><span class="sxs-lookup"><span data-stu-id="8360e-126">Best Practices</span></span>  
 <span data-ttu-id="8360e-127">單靠撰寫預存程序並不能夠確保應用程式的安全性。</span><span class="sxs-lookup"><span data-stu-id="8360e-127">Simply writing stored procedures isn't enough to adequately secure your application.</span></span> <span data-ttu-id="8360e-128">您也應該考量下列潛在的安全性漏洞。</span><span class="sxs-lookup"><span data-stu-id="8360e-128">You should also consider the following potential security holes.</span></span>  
  
-   <span data-ttu-id="8360e-129">針對想要用來存取資料的資料庫角色，授與預存程序上的 EXECUTE 權限。</span><span class="sxs-lookup"><span data-stu-id="8360e-129">Grant EXECUTE permissions on the stored procedures for database roles you want to be able to access the data.</span></span>  
  
-   <span data-ttu-id="8360e-130">針對資料庫中所有的角色和使用者 (包括 `public` 角色)，撤銷或拒絕對基礎資料表的所有權限。</span><span class="sxs-lookup"><span data-stu-id="8360e-130">Revoke or deny all permissions to the underlying tables for all roles and users in the database, including the `public` role.</span></span> <span data-ttu-id="8360e-131">所有的使用者都會從 public 繼承權限。</span><span class="sxs-lookup"><span data-stu-id="8360e-131">All users inherit permissions from public.</span></span> <span data-ttu-id="8360e-132">因此，拒絕對 `public` 的權限即表示只有擁有者和 `sysadmin` 成員具有存取權；所有其他使用者都無法從其他角色中的成員資格繼承權限。</span><span class="sxs-lookup"><span data-stu-id="8360e-132">Therefore denying permissions to `public` means that only owners and `sysadmin` members have access; all other users will be unable to inherit permissions from membership in other roles.</span></span>  
  
-   <span data-ttu-id="8360e-133">請勿將使用者或角色加入至 `sysadmin` 或 `db_owner` 角色。</span><span class="sxs-lookup"><span data-stu-id="8360e-133">Do not add users or roles to the `sysadmin` or `db_owner` roles.</span></span> <span data-ttu-id="8360e-134">系統管理員和資料庫擁有者可以存取所有的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="8360e-134">System administrators and database owners can access all database objects.</span></span>  
  
-   <span data-ttu-id="8360e-135">停用 `guest` 帳戶。</span><span class="sxs-lookup"><span data-stu-id="8360e-135">Disable the `guest` account.</span></span> <span data-ttu-id="8360e-136">這樣可避免匿名使用者連接至資料庫。</span><span class="sxs-lookup"><span data-stu-id="8360e-136">This will prevent anonymous users from connecting to the database.</span></span> <span data-ttu-id="8360e-137">預設會在新資料庫中停用來賓帳戶。</span><span class="sxs-lookup"><span data-stu-id="8360e-137">The guest account is disabled by default in new databases.</span></span>  
  
-   <span data-ttu-id="8360e-138">實作錯誤處理並記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="8360e-138">Implement error handling and log errors.</span></span>  
  
-   <span data-ttu-id="8360e-139">建立會驗證所有使用者輸入的參數化預存程序。</span><span class="sxs-lookup"><span data-stu-id="8360e-139">Create parameterized stored procedures that validate all user input.</span></span> <span data-ttu-id="8360e-140">將所有的使用者輸入都視為未受信任的。</span><span class="sxs-lookup"><span data-stu-id="8360e-140">Treat all user input as untrusted.</span></span>  
  
-   <span data-ttu-id="8360e-141">避免使用動態 SQL，除非絕對必要。</span><span class="sxs-lookup"><span data-stu-id="8360e-141">Avoid dynamic SQL unless absolutely necessary.</span></span> <span data-ttu-id="8360e-142">請使用 Transact-SQL QUOTENAME() 函式來分隔字串值，且逸出任何出現在輸入字串中的分隔符號 (Delimiter)。</span><span class="sxs-lookup"><span data-stu-id="8360e-142">Use the Transact-SQL QUOTENAME() function to delimit a string value and escape any occurrence of the delimiter in the input string.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="8360e-143">外部資源</span><span class="sxs-lookup"><span data-stu-id="8360e-143">External Resources</span></span>  
 <span data-ttu-id="8360e-144">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="8360e-144">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="8360e-145">資源</span><span class="sxs-lookup"><span data-stu-id="8360e-145">Resource</span></span>|<span data-ttu-id="8360e-146">說明</span><span class="sxs-lookup"><span data-stu-id="8360e-146">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="8360e-147">[預存程序](http://msdn.microsoft.com/library/ms190782.aspx)和[SQL 資料隱碼](http://go.microsoft.com/fwlink/?LinkId=98234)SQL Server 線上叢書中</span><span class="sxs-lookup"><span data-stu-id="8360e-147">[Stored Procedures](http://msdn.microsoft.com/library/ms190782.aspx) and [SQL Injection](http://go.microsoft.com/fwlink/?LinkId=98234) in SQL Server Books Online</span></span>|<span data-ttu-id="8360e-148">說明如何建立預存程序以及「SQL 插入」運作方式的主題。</span><span class="sxs-lookup"><span data-stu-id="8360e-148">Topics describe how to create stored procedures and how SQL Injection works.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8360e-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8360e-149">See Also</span></span>  
 [<span data-ttu-id="8360e-150">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="8360e-150">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="8360e-151">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="8360e-151">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="8360e-152">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="8360e-152">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="8360e-153">撰寫安全動態 SQL，SQL Server</span><span class="sxs-lookup"><span data-stu-id="8360e-153">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="8360e-154">簽署 SQL Server 中的預存程序</span><span class="sxs-lookup"><span data-stu-id="8360e-154">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="8360e-155">自訂 SQL Server 中的模擬權限</span><span class="sxs-lookup"><span data-stu-id="8360e-155">Customizing Permissions with Impersonation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [<span data-ttu-id="8360e-156">使用預存程序修改資料</span><span class="sxs-lookup"><span data-stu-id="8360e-156">Modifying Data with Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [<span data-ttu-id="8360e-157">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="8360e-157">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
