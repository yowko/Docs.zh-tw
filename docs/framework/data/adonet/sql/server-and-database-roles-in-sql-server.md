---
title: "SQL Server 中的伺服器和資料庫角色"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5482dfdb-e498-4614-8652-b174829eed13
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1a9d8de6b3302684bd8769b7b1baaebedefb649c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="server-and-database-roles-in-sql-server"></a>SQL Server 中的伺服器和資料庫角色
所有的 SQL Server 版本都會使用角色架構的安全性，讓您可以將權限指派給角色或使用者群組，而不是個別的使用者。 固定伺服器角色和固定資料庫角色都指派有固定的權限組。  
  
## <a name="fixed-server-roles"></a>固定伺服器角色  
 固定伺服器角色擁有固定的權限組和整個伺服器的範圍， 這些角色專門用於管理 SQL Server，且指派給角色的權限都無法變更。 您可以將登入指派給固定伺服器角色，而不必擁有資料庫的使用者脹戶。  
  
> [!IMPORTANT]
>  `sysadmin` 固定伺服器角色涵蓋所有其他的角色，而且範圍不受限制。 除非高度信任主體的安全性，否則請勿將主體新增到此角色中。 `sysadmin` 角色成員對於所有的伺服器資料庫和資源都具有不可撤銷的管理權限。  
  
 當您要將使用者新增到固定伺服器角色時，請嚴加篩選。 例如，`bulkadmin` 角色可讓使用者加任何本機檔案的內容插入至資料表，因而可能危及資料完整性。 如需固定伺服器角色和權限的完整清單，請參閱《[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 線上叢書》。  
  
## <a name="fixed-database-roles"></a>固定資料庫角色  
 固定資料庫角色擁有預先定義的權限集合，其目的是讓您可以輕鬆地管理權限群組。 `db_owner` 角色的成員可以在資料庫上執行所有組態和維護活動。  
  
 如需 SQL Server 預先定義角色的詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[伺服器層級角色](http://msdn.microsoft.com/library/ms188659.aspx)和[固定的伺服器角色的權限](http://msdn.microsoft.com/library/ms175892.aspx)中[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]線上叢書 》|說明 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 中的固定伺服器角色和與其相關聯的權限。|  
|[資料庫層級角色](http://msdn.microsoft.com/library/ms189121.aspx)和[固定的資料庫角色的權限](http://msdn.microsoft.com/library/ms189612.aspx)中[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]線上叢書 》|說明 SQL Server 2005 中的固定資料庫角色和與其相關的權限。|  
  
## <a name="database-roles-and-users"></a>資料庫角色和使用者  
 登入必須對應至資料庫使用者帳戶，才能使用資料庫物件。 接著可以將資料庫使用者加入至資料庫角色、繼承任何與這些角色相關聯的權限集合。 所有權限都可授與。  
  
 當您為應用程式設計安全性時，也必須考慮 `public` 角色、`dbo` 使用者帳戶和 `guest` 帳戶。  
  
### <a name="the-public-role"></a>public 角色  
 `public` 角色包含在每個資料庫中，系統資料庫也不例外。 您無法加以卸除，也無法從其加入或移除使用者。 授與 `public` 角色的權限會由所有其他的使用者和角色繼承，因為這些權限依預設是屬於 `public` 角色。 請僅為 `public` 授與所有使用者都可擁有的權限。  
  
### <a name="the-dbo-user-account"></a>dbo 使用者帳戶  
 `dbo` (也稱為資料庫擁有者) 是使用者帳戶，擁有可在資料庫中執行所有活動的隱含權限。 `sysadmin` 固定伺服器角色的成員會自動對應至 `dbo`。  
  
> [!NOTE]
>  `dbo`也是名稱的結構描述中所述[擁有權和 SQL Server 中的使用者結構描述分隔](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)。  
  
 `dbo` 使用者帳戶經常會與 `db_owner` 固定資料庫角色混淆。 `db_owner` 的範圍是一個資料庫，而 `sysadmin` 的範圍是整個伺服器。 `db_owner` 角色中的成員資格不會授與 `dbo` 使用權限。  
  
### <a name="the-guest-user-account"></a>guest 使用者帳戶  
 使用者經過驗證並獲准登入 SQL Server 執行個體之後，每個資料庫中都必須要有另外的使用者帳戶。 之所以要求每個資料庫中都必須有使用者帳戶的原因，是這樣可以避免使用者連接到 SQL Server 執行個體 (Instance) 而存取伺服器上的所有資料庫。 資料庫中如果有 `guest` 使用者帳戶，則可以規避這項需求，因為這樣可以允許沒有資料庫使用者帳戶的登入對資料庫進行存取。  
  
 在所有版本的 SQL Server 中，`guest` 帳戶都是內建帳戶。 依預設，此帳戶在新資料庫中是停用狀態。 如果有啟用此帳戶，則可以藉由執行 Transact-SQL REVOKE CONNECT FROM GUEST 陳述式撤銷其 CONNECT 權限而加以停用。  
  
> [!IMPORTANT]
>  請避免使用 `guest` 帳戶；所有本身不具資料庫權限的登入，都會取得授與此帳戶的資料庫權限。 如果必須使用 `guest` 帳戶，請為其授與最小權限。  
  
 如需有關 SQL Server 登入、使用者和角色的詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[識別和存取控制](http://msdn.microsoft.com/library/bb510418.aspx)SQL Server 線上叢書中|包含說明主體、角色、認證、安全性實體和權限的主題連結。|  
|[主體](http://msdn.microsoft.com/library/ms181127.aspx)中[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]線上叢書 》|說明主體並包含說明伺服器和資料庫角色的主題連結。|  
  
## <a name="see-also"></a>請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [在 SQL Server 中進行驗證](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [SQL Server 中的擁有權和使用者結構描述分離](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 [SQL Server 中的授權和權限](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
