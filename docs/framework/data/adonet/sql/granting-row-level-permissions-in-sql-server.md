---
title: 在 SQL Server 中授與資料列層級權限
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 891b5114551c5784b11504f2463525087125131f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973079"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="c2fb5-102">在 SQL Server 中授與資料列層級權限</span><span class="sxs-lookup"><span data-stu-id="c2fb5-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="c2fb5-103">在某些案例中，相較於單純地授與、撤銷或拒絕權限，您需要以更細微的層級來控制資料存取。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="c2fb5-104">例如，醫院資料庫應用程式可能需要限制個別醫生只能存取與其病患相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="c2fb5-105">類似的需求存在許多環境中，包括財務、法律、政府和軍事應用程式中。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="c2fb5-106">為了協助解決這些案例，SQL Server 2016 提供 [資料列層級安全性](/sql/relational-databases/security/row-level-security) 功能，以一個安全性原則來簡化並集中管理資料列層級存取邏輯。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="c2fb5-107">針對舊版 SQL Server，您可以使用檢視來制定資料列層級篩選，以達到類似的功能。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="c2fb5-108">實作資料列層級篩選</span><span class="sxs-lookup"><span data-stu-id="c2fb5-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="c2fb5-109">資料列層級會用於將資訊儲存在單一資料表中的應用程式，如上述醫院範例所示。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="c2fb5-110">為了實作資料列層級篩選，每個資料列都具有一個定義區別參數的資料行，例如使用者名稱、標籤或其他識別碼。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="c2fb5-111">您可以在資料表上建立安全性原則或檢視，篩選使用者可以存取的資料列。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="c2fb5-112">然後，您可以建立參數化預存程序，控制使用者可以執行的查詢類型。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="c2fb5-113">下列範例說明如何根據使用者或登入名稱來設定資料列層級篩選：</span><span class="sxs-lookup"><span data-stu-id="c2fb5-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="c2fb5-114">建立資料表，並加入儲存名稱的資料行。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="c2fb5-115">啟用資料列層級篩選：</span><span class="sxs-lookup"><span data-stu-id="c2fb5-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="c2fb5-116">如果您使用 SQL Server 2016 (含) 以上版本或 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/)，請建立一個安全性原則將述詞加入資料表中，以限制傳回的資料列必須符合目前的資料庫使用者 (使用 CURRENT_USER() 內建函式) 或目前的登入名稱 (使用 SUSER_SNAME() 內建函式)：</span><span class="sxs-lookup"><span data-stu-id="c2fb5-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
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

  - <span data-ttu-id="c2fb5-117">如果您使用 SQL Server 2016 之前的版本，可以透過檢視來達到類似的功能：</span><span class="sxs-lookup"><span data-stu-id="c2fb5-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="c2fb5-118">建立預存程序來選取、插入、更新及刪除資料。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="c2fb5-119">如果篩選是由安全性原則制定，預存程序應該在基底資料表上直接執行這些作業；如果篩選是由檢視制定，預存程序應該改為對檢視執行。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="c2fb5-120">安全性原則或檢視會自動篩選使用者查詢所傳回或修改的資料列，而預存程序會提供更嚴格的安全性界限，以防止具有直接查詢存取權的使用者成功執行可能推斷出已篩選資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="c2fb5-121">若為插入資料的預存程序，請使用在安全性原則或檢視中指定的相同函式來擷取使用者名稱，然後將該值插入 UserName 資料行。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="c2fb5-122">針對 `public` 角色拒絕資料表和檢視 (如果適用) 的所有權限。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="c2fb5-123">使用者將無法從其他資料庫角色中繼承權限，因為篩選述詞是以使用者或登入名稱 (而非角色) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="c2fb5-124">將預存程序的 EXECUTE 授與資料庫角色。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="c2fb5-125">使用者只能透過提供的預存程序來存取資料。</span><span class="sxs-lookup"><span data-stu-id="c2fb5-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2fb5-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2fb5-126">See also</span></span>

- [<span data-ttu-id="c2fb5-127">資料列層級安全性</span><span class="sxs-lookup"><span data-stu-id="c2fb5-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="c2fb5-128">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="c2fb5-128">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="c2fb5-129">SQL Server 安全性概觀</span><span class="sxs-lookup"><span data-stu-id="c2fb5-129">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [<span data-ttu-id="c2fb5-130">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="c2fb5-130">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="c2fb5-131">在 SQL Server 中使用預存程序來管理權限</span><span class="sxs-lookup"><span data-stu-id="c2fb5-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="c2fb5-132">在 SQL Server 中撰寫安全的動態 SQL</span><span class="sxs-lookup"><span data-stu-id="c2fb5-132">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="c2fb5-133">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="c2fb5-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
