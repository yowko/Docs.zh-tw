---
title: SQL Server 中的擁有權和使用者結構描述分離
description: 瞭解使用者架構分隔如何讓管理 SQL Server 資料庫物件許可權更有彈性。 架構會將物件分組到不同的命名空間。
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 97e742979785fedd922dc887295b63e2d93bd147
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286258"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="f398e-104">SQL Server 中的擁有權和使用者結構描述分離</span><span class="sxs-lookup"><span data-stu-id="f398e-104">Ownership and User-Schema Separation in SQL Server</span></span>
<span data-ttu-id="f398e-105">SQL Server 安全性的核心概念是物件的擁有者具有不可撤銷的物件管理權限。</span><span class="sxs-lookup"><span data-stu-id="f398e-105">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="f398e-106">您無法移除物件擁有者的權限，而使用者只要擁有資料庫中的物件，就無法將其從資料庫卸除。</span><span class="sxs-lookup"><span data-stu-id="f398e-106">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="f398e-107">使用者結構描述分隔</span><span class="sxs-lookup"><span data-stu-id="f398e-107">User-Schema Separation</span></span>  
 <span data-ttu-id="f398e-108">使用者結構描述分隔可讓資料庫物件權限的管理更有彈性。</span><span class="sxs-lookup"><span data-stu-id="f398e-108">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="f398e-109">「*架構*」（schema）是資料庫物件的命名容器，可讓您將物件分組成不同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f398e-109">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="f398e-110">例如，AdventureWorks 範例資料庫包含 Production、Sales 和 HumanResources 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="f398e-110">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="f398e-111">參考物件的四部分命名語法會指定結構描述名稱。</span><span class="sxs-lookup"><span data-stu-id="f398e-111">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```text
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="f398e-112">結構描述擁有者和權限</span><span class="sxs-lookup"><span data-stu-id="f398e-112">Schema Owners and Permissions</span></span>  
 <span data-ttu-id="f398e-113">結構描述可以由任何資料庫主體所擁有，而單一的主體可以擁有多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="f398e-113">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="f398e-114">您可以將安全性規則套用至結構描述，而結構描述中的所有物件都會繼承這些規則。</span><span class="sxs-lookup"><span data-stu-id="f398e-114">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="f398e-115">一旦設定結構描述的存取權限之後，就會在新物件加入至結構描述時自動套用這些權限。</span><span class="sxs-lookup"><span data-stu-id="f398e-115">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="f398e-116">您可以為使用者指派預設的結構描述，而多個資料庫使用者可以共用相同的結構描述。</span><span class="sxs-lookup"><span data-stu-id="f398e-116">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="f398e-117">根據預設，當開發人員建立結構描述中的物件時，這些物件會由擁有該結構描述的安全性主體，而非開發人員所擁有。</span><span class="sxs-lookup"><span data-stu-id="f398e-117">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="f398e-118">物件擁有權可以使用 ALTER AUTHORIZATION Transact-SQL 陳述式轉移。</span><span class="sxs-lookup"><span data-stu-id="f398e-118">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="f398e-119">結構描述也可以包含由不同使用者所擁有的物件，且具備比指派給該結構描述更多的細微權限，但因為這樣會增加權限管理的複雜度，我們並不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="f398e-119">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="f398e-120">您可以在結構描述之間移動物件，也可以在主體之間轉移結構描述擁有權。</span><span class="sxs-lookup"><span data-stu-id="f398e-120">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="f398e-121">您可以卸除資料庫使用者，而不影響結構描述。</span><span class="sxs-lookup"><span data-stu-id="f398e-121">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="f398e-122">內建結構描述</span><span class="sxs-lookup"><span data-stu-id="f398e-122">Built-In Schemas</span></span>  
 <span data-ttu-id="f398e-123">SQL Server 隨附十個預先定義的結構描述，其名稱與內建的資料庫使用者及角色相同。</span><span class="sxs-lookup"><span data-stu-id="f398e-123">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="f398e-124">這些主要是為了回溯相容性 (Backward Compatibility) 而提供。</span><span class="sxs-lookup"><span data-stu-id="f398e-124">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="f398e-125">如果不需要這些與固定資料庫角色具有相同名稱的結構描述，您可以加以卸除，</span><span class="sxs-lookup"><span data-stu-id="f398e-125">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="f398e-126">但下列結構描述是不能卸除的：</span><span class="sxs-lookup"><span data-stu-id="f398e-126">You cannot drop the following schemas:</span></span>  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="f398e-127">如果將這些結構描述從模型資料庫卸除，它們就不會出現在新資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f398e-127">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f398e-128">`sys` 和 `INFORMATION_SCHEMA` 結構描述是保留給系統物件使用。</span><span class="sxs-lookup"><span data-stu-id="f398e-128">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="f398e-129">您無法在這些結構描述中建立物件，也無法加以卸除。</span><span class="sxs-lookup"><span data-stu-id="f398e-129">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="f398e-130">dbo 結構描述</span><span class="sxs-lookup"><span data-stu-id="f398e-130">The dbo Schema</span></span>  
 <span data-ttu-id="f398e-131">`dbo` 結構描述是新建立資料庫的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="f398e-131">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="f398e-132">`dbo` 結構描述是由 `dbo` 使用者帳戶所擁有。</span><span class="sxs-lookup"><span data-stu-id="f398e-132">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="f398e-133">依預設，使用 CREATE USER Transact-SQL 命令所建立的使用者都會將 `dbo` 當做預設的結構描述。</span><span class="sxs-lookup"><span data-stu-id="f398e-133">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="f398e-134">被指派 `dbo` 結構描述的使用者並不會繼承 `dbo` 使用者帳戶的權限。</span><span class="sxs-lookup"><span data-stu-id="f398e-134">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="f398e-135">使用者不會從結構描述繼承權限；結構描述權限是由結構描述中包含的資料庫物件所繼承。</span><span class="sxs-lookup"><span data-stu-id="f398e-135">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f398e-136">當資料庫物件是使用一段式名稱來參考時，SQL Server 會先查看使用者的預設結構描述。</span><span class="sxs-lookup"><span data-stu-id="f398e-136">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="f398e-137">如果在該處找不到物件，SQL Server 接著會在 `dbo` 結構描述中尋找。</span><span class="sxs-lookup"><span data-stu-id="f398e-137">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="f398e-138">如果在 `dbo` 結構描述中也找不到物件，就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="f398e-138">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="f398e-139">外部資源</span><span class="sxs-lookup"><span data-stu-id="f398e-139">External Resources</span></span>  
 <span data-ttu-id="f398e-140">如需有關物件擁有權和結構描述的詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="f398e-140">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="f398e-141">資源</span><span class="sxs-lookup"><span data-stu-id="f398e-141">Resource</span></span>|<span data-ttu-id="f398e-142">描述</span><span class="sxs-lookup"><span data-stu-id="f398e-142">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f398e-143">[使用者結構描述分隔](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="f398e-143">[User-Schema Separation](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span></span>|<span data-ttu-id="f398e-144">說明由使用者結構描述分隔引入的變更。</span><span class="sxs-lookup"><span data-stu-id="f398e-144">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="f398e-145">包括新增行為、對擁有權的影響、目錄檢視和權限。</span><span class="sxs-lookup"><span data-stu-id="f398e-145">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f398e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f398e-146">See also</span></span>

- [<span data-ttu-id="f398e-147">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="f398e-147">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="f398e-148">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="f398e-148">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="f398e-149">在 SQL Server 中進行驗證</span><span class="sxs-lookup"><span data-stu-id="f398e-149">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="f398e-150">SQL Server 中的伺服器和資料庫角色</span><span class="sxs-lookup"><span data-stu-id="f398e-150">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="f398e-151">SQL Server 中的授權和權限</span><span class="sxs-lookup"><span data-stu-id="f398e-151">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- <span data-ttu-id="f398e-152">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="f398e-152">[ADO.NET Overview](../ado-net-overview.md)</span></span>
