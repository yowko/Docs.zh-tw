---
title: 使用預存程序管理 SQL Server 中的權限
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 0688157b45892cacb73f858dffb93836da9fc91d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229988"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>使用預存程序管理 SQL Server 中的權限
為資料庫建立多重防線的方法之一，就是使用預存程序 (Stored Procedure) 或使用者定義的函式來實作所有資料存取。 您可以撤銷或拒絕基礎物件 (例如資料表) 的所有權限，然後在預存程序上授與 EXECUTE 權限。 如此即可有效地在資料和資料庫物件周圍建立安全性防線。  
  
## <a name="stored-procedure-benefits"></a>預存程序的優點  
 預存程序有下列優點：  
  
-   可以將資料邏輯和商務規則 (Business Rule) 加以封裝，如此使用者就只能以開發人員和資料庫系統管理員預期的方式來存取資料及物件。  
  
-   可以使用會驗證所有使用者輸入的參數化預存程序來防堵 SQL 插入式攻擊。 如果有使用動態 SQL，請務必將命令參數化，也絕對不要在查詢字串中直接包含參數值。  
  
-   可以拒絕臨機操作 (Ad Hoc) 的查詢和資料修改作業。 如此可避免使用者因惡意或不慎而損毀資料，或執行會降低伺服器或網路效能的查詢。  
  
-   可以處理程序程式碼中的錯誤，而不必將錯誤直接傳遞至用戶端應用程式。 如此可避免傳回可能助長探查攻擊的錯誤訊息。 請在伺服器上記錄及處理錯誤。  
  
-   預存程序只需寫入一次，即可由許多應用程式存取。  
  
-   用戶端應用程式不需要對基礎資料結構有任何了解。 您可以對預存程序程式碼進行變更，而不需變更用戶端應用程式，只要這些變更不會影響參數清單或傳回的資料型別即可。  
  
-   預存程序可以將多項作業結合成單一的程序呼叫，藉此降低網路流量。  
  
## <a name="stored-procedure-execution"></a>預存程序的執行  
 預存程序可以利用擁有權鏈結提供對資料的存取，如此使用者即使沒有明確的權限，也可以存取資料庫物件。 當循序彼此存取的物件是由同一個使用者所擁有時，即構成擁有權鏈結。 例如，預存程序可以呼叫其他的預存程序，或者預存程序也可以存取多個資料表。 如果執行鏈結中的所有物件都具有相同的擁有者，則 SQL Server 只會檢查呼叫端的 EXECUTE 權限，而不會檢查呼叫端對其他物件的權限。 因此您只需要授與預存程序上的 EXECUTE 權限，而可以撤銷或拒絕基礎資料表上的所有權限。  
  
## <a name="best-practices"></a>最佳作法  
 單靠撰寫預存程序並不能夠確保應用程式的安全性。 您也應該考量下列潛在的安全性漏洞。  
  
-   針對想要用來存取資料的資料庫角色，授與預存程序上的 EXECUTE 權限。  
  
-   針對資料庫中所有的角色和使用者 (包括 `public` 角色)，撤銷或拒絕對基礎資料表的所有權限。 所有的使用者都會從 public 繼承權限。 因此，拒絕對 `public` 的權限即表示只有擁有者和 `sysadmin` 成員具有存取權；所有其他使用者都無法從其他角色中的成員資格繼承權限。  
  
-   請勿將使用者或角色加入至 `sysadmin` 或 `db_owner` 角色。 系統管理員和資料庫擁有者可以存取所有的資料庫物件。  
  
-   停用 `guest` 帳戶。 這樣可避免匿名使用者連接至資料庫。 預設會在新資料庫中停用來賓帳戶。  
  
-   實作錯誤處理並記錄錯誤。  
  
-   建立會驗證所有使用者輸入的參數化預存程序。 將所有的使用者輸入都視為未受信任的。  
  
-   避免使用動態 SQL，除非絕對必要。 請使用 Transact-SQL QUOTENAME() 函式來分隔字串值，且逸出任何出現在輸入字串中的分隔符號 (Delimiter)。  
  
## <a name="external-resources"></a>外部資源  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|《SQL Server 線上叢書》中的[預存程序](/sql/relational-databases/stored-procedures/stored-procedures-database-engine)和 [SQL 插入](https://go.microsoft.com/fwlink/?LinkId=98234)|說明如何建立預存程序以及「SQL 插入」運作方式的主題。|  
  
## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [在 SQL Server 中撰寫安全的動態 SQL](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [在 SQL Server 中簽署預存程序](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [在 SQL Server 中使用模擬來自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [使用預存程序修改資料](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
