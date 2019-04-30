---
title: 在 SQL Server 中授與資料列層級權限
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 891b5114551c5784b11504f2463525087125131f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033900"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>在 SQL Server 中授與資料列層級權限

在某些案例中，相較於單純地授與、撤銷或拒絕權限，您需要以更細微的層級來控制資料存取。 例如，醫院資料庫應用程式可能需要限制個別醫生只能存取與其病患相關的資訊。 類似的需求存在許多環境中，包括財務、法律、政府和軍事應用程式中。 為了協助解決這些案例，SQL Server 2016 提供 [資料列層級安全性](/sql/relational-databases/security/row-level-security) 功能，以一個安全性原則來簡化並集中管理資料列層級存取邏輯。 針對舊版 SQL Server，您可以使用檢視來制定資料列層級篩選，以達到類似的功能。

## <a name="implementing-row-level-filtering"></a>實作資料列層級篩選

資料列層級會用於將資訊儲存在單一資料表中的應用程式，如上述醫院範例所示。 為了實作資料列層級篩選，每個資料列都具有一個定義區別參數的資料行，例如使用者名稱、標籤或其他識別碼。 您可以在資料表上建立安全性原則或檢視，篩選使用者可以存取的資料列。 然後，您可以建立參數化預存程序，控制使用者可以執行的查詢類型。

下列範例說明如何根據使用者或登入名稱來設定資料列層級篩選：

- 建立資料表，並加入儲存名稱的資料行。

- 啟用資料列層級篩選：

  - 如果您使用 SQL Server 2016 (含) 以上版本或 [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/)，請建立一個安全性原則將述詞加入資料表中，以限制傳回的資料列必須符合目前的資料庫使用者 (使用 CURRENT_USER() 內建函式) 或目前的登入名稱 (使用 SUSER_SNAME() 內建函式)：

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

  - 如果您使用 SQL Server 2016 之前的版本，可以透過檢視來達到類似的功能：

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- 建立預存程序來選取、插入、更新及刪除資料。 如果篩選是由安全性原則制定，預存程序應該在基底資料表上直接執行這些作業；如果篩選是由檢視制定，預存程序應該改為對檢視執行。 安全性原則或檢視會自動篩選使用者查詢所傳回或修改的資料列，而預存程序會提供更嚴格的安全性界限，以防止具有直接查詢存取權的使用者成功執行可能推斷出已篩選資料的查詢。

- 若為插入資料的預存程序，請使用在安全性原則或檢視中指定的相同函式來擷取使用者名稱，然後將該值插入 UserName 資料行。

- 針對 `public` 角色拒絕資料表和檢視 (如果適用) 的所有權限。 使用者將無法從其他資料庫角色中繼承權限，因為篩選述詞是以使用者或登入名稱 (而非角色) 為基礎。

- 將預存程序的 EXECUTE 授與資料庫角色。 使用者只能透過提供的預存程序來存取資料。

## <a name="see-also"></a>另請參閱

- [資料列層級安全性](/sql/relational-databases/security/row-level-security)
- [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [在 SQL Server 中使用預存程序來管理權限](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [在 SQL Server 中撰寫安全的動態 SQL](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
