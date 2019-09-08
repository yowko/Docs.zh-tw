---
title: SQL Server 中的擁有權和使用者結構描述分離
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: f0aa0a67bfbc64124fe2510915d0945341aeb49e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791943"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a>SQL Server 中的擁有權和使用者結構描述分離
SQL Server 安全性的核心概念是物件的擁有者具有不可撤銷的物件管理權限。 您無法移除物件擁有者的權限，而使用者只要擁有資料庫中的物件，就無法將其從資料庫卸除。  
  
## <a name="user-schema-separation"></a>使用者結構描述分隔  
 使用者結構描述分隔可讓資料庫物件權限的管理更有彈性。 「*架構*」（schema）是資料庫物件的命名容器，可讓您將物件分組成不同的命名空間。 例如，AdventureWorks 範例資料庫包含 Production、Sales 和 HumanResources 的結構描述。  
  
 參考物件的四部分命名語法會指定結構描述名稱。  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a>結構描述擁有者和權限  
 結構描述可以由任何資料庫主體所擁有，而單一的主體可以擁有多個結構描述。 您可以將安全性規則套用至結構描述，而結構描述中的所有物件都會繼承這些規則。 一旦設定結構描述的存取權限之後，就會在新物件加入至結構描述時自動套用這些權限。 您可以為使用者指派預設的結構描述，而多個資料庫使用者可以共用相同的結構描述。  
  
 根據預設，當開發人員建立結構描述中的物件時，這些物件會由擁有該結構描述的安全性主體，而非開發人員所擁有。 物件擁有權可以使用 ALTER AUTHORIZATION Transact-SQL 陳述式轉移。 結構描述也可以包含由不同使用者所擁有的物件，且具備比指派給該結構描述更多的細微權限，但因為這樣會增加權限管理的複雜度，我們並不建議這麼做。 您可以在結構描述之間移動物件，也可以在主體之間轉移結構描述擁有權。 您可以卸除資料庫使用者，而不影響結構描述。  
  
### <a name="built-in-schemas"></a>內建結構描述  
 SQL Server 隨附十個預先定義的結構描述，其名稱與內建的資料庫使用者及角色相同。 這些主要是為了回溯相容性 (Backward Compatibility) 而提供。 如果不需要這些與固定資料庫角色具有相同名稱的結構描述，您可以加以卸除， 但下列結構描述是不能卸除的：  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 如果將這些結構描述從模型資料庫卸除，它們就不會出現在新資料庫中。  
  
> [!NOTE]
> `sys` 和 `INFORMATION_SCHEMA` 結構描述是保留給系統物件使用。 您無法在這些結構描述中建立物件，也無法加以卸除。  
  
#### <a name="the-dbo-schema"></a>dbo 結構描述  
 `dbo` 結構描述是新建立資料庫的預設結構描述。 `dbo` 結構描述是由 `dbo` 使用者帳戶所擁有。 依預設，使用 CREATE USER Transact-SQL 命令所建立的使用者都會將 `dbo` 當做預設的結構描述。  
  
 被指派 `dbo` 結構描述的使用者並不會繼承 `dbo` 使用者帳戶的權限。 使用者不會從結構描述繼承權限；結構描述權限是由結構描述中包含的資料庫物件所繼承。  
  
> [!NOTE]
> 當資料庫物件是使用一段式名稱來參考時，SQL Server 會先查看使用者的預設結構描述。 如果在該處找不到物件，SQL Server 接著會在 `dbo` 結構描述中尋找。 如果在 `dbo` 結構描述中也找不到物件，就會傳回錯誤。  
  
## <a name="external-resources"></a>外部資源  
 如需有關物件擁有權和結構描述的詳細資訊，請參閱下列資源。  
  
|Resource|描述|  
|--------------|-----------------|  
|[使用者架構分隔](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))|說明由使用者結構描述分隔引入的變更。 包括新增行為、對擁有權的影響、目錄檢視和權限。|  
  
## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../securing-ado-net-applications.md)
- [SQL Server 中的應用程式安全性案例](application-security-scenarios-in-sql-server.md)
- [在 SQL Server 中進行驗證](authentication-in-sql-server.md)
- [SQL Server 中的伺服器和資料庫角色](server-and-database-roles-in-sql-server.md)
- [SQL Server 中的授權和權限](authorization-and-permissions-in-sql-server.md)
- [ADO.NET 概觀](../ado-net-overview.md)
