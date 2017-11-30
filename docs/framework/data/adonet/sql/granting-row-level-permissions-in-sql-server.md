---
title: "在 SQL Server 中授與資料列層級權限"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6e71511286ce7451b2967e9c66ea2209549a356
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="7072e-102">在 SQL Server 中授與資料列層級權限</span><span class="sxs-lookup"><span data-stu-id="7072e-102">Granting Row-Level Permissions in SQL Server</span></span>
<span data-ttu-id="7072e-103">在某些案例中，相較於單純地授與、撤銷或拒絕權限，您需要以更細微的層級來控制資料存取。</span><span class="sxs-lookup"><span data-stu-id="7072e-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="7072e-104">例如，醫院資料庫應用程式可能需要限制個別醫生只能存取與其病患相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="7072e-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="7072e-105">類似的需求存在許多環境中，包括財務、法律、政府和軍事應用程式中。</span><span class="sxs-lookup"><span data-stu-id="7072e-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="7072e-106">為了協助解決這些案例，SQL Server 2016 提供 [資料列層級安全性](https://msdn.microsoft.com/library/dn765131.aspx) 功能，以一個安全性原則來簡化並集中管理資料列層級存取邏輯。</span><span class="sxs-lookup"><span data-stu-id="7072e-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="7072e-107">針對舊版 SQL Server，您可以使用檢視來制定資料列層級篩選，以達到類似的功能。</span><span class="sxs-lookup"><span data-stu-id="7072e-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>  
  
## <a name="implementing-row-level-filtering"></a><span data-ttu-id="7072e-108">實作資料列層級篩選</span><span class="sxs-lookup"><span data-stu-id="7072e-108">Implementing Row-level Filtering</span></span>  
 <span data-ttu-id="7072e-109">資料列層級會用於將資訊儲存在單一資料表中的應用程式，如上述醫院範例所示。</span><span class="sxs-lookup"><span data-stu-id="7072e-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="7072e-110">為了實作資料列層級篩選，每個資料列都具有一個定義區別參數的資料行，例如使用者名稱、標籤或其他識別碼。</span><span class="sxs-lookup"><span data-stu-id="7072e-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="7072e-111">您可以在資料表上建立安全性原則或檢視，篩選使用者可以存取的資料列。</span><span class="sxs-lookup"><span data-stu-id="7072e-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="7072e-112">然後，您可以建立參數化預存程序，控制使用者可以執行的查詢類型。</span><span class="sxs-lookup"><span data-stu-id="7072e-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>  
  
 <span data-ttu-id="7072e-113">下列範例說明如何根據使用者或登入名稱來設定資料列層級篩選：</span><span class="sxs-lookup"><span data-stu-id="7072e-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>  
  
-   <span data-ttu-id="7072e-114">建立資料表，並加入儲存名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="7072e-114">Create the table, adding a column to store the name.</span></span>  
  
-   <span data-ttu-id="7072e-115">啟用資料列層級篩選：</span><span class="sxs-lookup"><span data-stu-id="7072e-115">Enable row-level filtering:</span></span>  
  
    -   <span data-ttu-id="7072e-116">如果您使用 SQL Server 2016 或更新版本，或[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/)，建立安全性原則，將 限制資料列的資料表上的述詞傳回那些符合目前的資料庫使用者 （使用 CURRENT_USER()內建函式） 或目前的登入名稱 （使用 suser_sname （） 內建函式）：</span><span class="sxs-lookup"><span data-stu-id="7072e-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>  
  
        ```tsql  
        CREATE SCHEMA Security  
        GO  
  
        CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)  
            RETURNS TABLE  
            WITH SCHEMABINDING  
        AS  
            RETURN SELECT 1 AS accessResult  
            WHERE @UserName = SUSER_SNAME()  
        GO  
  
        CREATE SECURITY POLICY Security.userAccessPolicy  
            ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,  
            ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable  
        GO  
        ```  
  
    -   <span data-ttu-id="7072e-117">如果您使用 SQL Server 2016 之前的版本，可以透過檢視來達到類似的功能：</span><span class="sxs-lookup"><span data-stu-id="7072e-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   <span data-ttu-id="7072e-118">建立預存程序來選取、插入、更新及刪除資料。</span><span class="sxs-lookup"><span data-stu-id="7072e-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="7072e-119">如果篩選是由安全性原則制定，預存程序應該在基底資料表上直接執行這些作業；如果篩選是由檢視制定，預存程序應該改為對檢視執行。</span><span class="sxs-lookup"><span data-stu-id="7072e-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="7072e-120">安全性原則或檢視會自動篩選使用者查詢所傳回或修改的資料列，而預存程序會提供更嚴格的安全性界限，以防止具有直接查詢存取權的使用者成功執行可能推斷出已篩選資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="7072e-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>  
  
-   <span data-ttu-id="7072e-121">若為插入資料的預存程序，請使用在安全性原則或檢視中指定的相同函式來擷取使用者名稱，然後將該值插入 UserName 資料行。</span><span class="sxs-lookup"><span data-stu-id="7072e-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>  
  
-   <span data-ttu-id="7072e-122">針對 `public` 角色拒絕資料表和檢視 (如果適用) 的所有權限。</span><span class="sxs-lookup"><span data-stu-id="7072e-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="7072e-123">使用者將無法從其他資料庫角色中繼承權限，因為篩選述詞是以使用者或登入名稱 (而非角色) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="7072e-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>  
  
-   <span data-ttu-id="7072e-124">將預存程序的 EXECUTE 授與資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="7072e-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="7072e-125">使用者只能透過提供的預存程序來存取資料。</span><span class="sxs-lookup"><span data-stu-id="7072e-125">Users can only access data through the stored procedures provided.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="7072e-126">外部資源</span><span class="sxs-lookup"><span data-stu-id="7072e-126">External Resources</span></span>  
 <span data-ttu-id="7072e-127">如需詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="7072e-127">For more information, see the following resource.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7072e-128">SQL Server TechCenter 網站上的[使用 SQL Server 2005 在分類資料庫中實作資料列和資料格層級安全性](http://go.microsoft.com/fwlink/?LinkId=98227) 。</span><span class="sxs-lookup"><span data-stu-id="7072e-128">[Implementing Row- and Cell-Level Security in Classified Databases Using SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) on the SQL Server TechCenter site.</span></span>|<span data-ttu-id="7072e-129">說明如何使用列和資料格層級安全性來符合分類資料庫的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="7072e-129">Describes how to use row- and cell-level security to meet classified database security requirements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7072e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7072e-130">See Also</span></span>  
 [<span data-ttu-id="7072e-131">資料列層級安全性</span><span class="sxs-lookup"><span data-stu-id="7072e-131">Row-Level Security</span></span>](https://msdn.microsoft.com/library/dn765131.aspx)  
 [<span data-ttu-id="7072e-132">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="7072e-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="7072e-133">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="7072e-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="7072e-134">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="7072e-134">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="7072e-135">管理 SQL Server 中的預存程序的權限</span><span class="sxs-lookup"><span data-stu-id="7072e-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="7072e-136">撰寫安全動態 SQL，SQL Server</span><span class="sxs-lookup"><span data-stu-id="7072e-136">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="7072e-137">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="7072e-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
