---
title: SQL Server 中的應用程式安全性案例
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 42afe27c11eadff935e162128b3d5f18c1cba8a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687449"
---
# <a name="application-security-scenarios-in-sql-server"></a>SQL Server 中的應用程式安全性案例
並不只有一種正確方式可以建立安全的 SQL Server 用戶端應用程式。 每個應用程式的需求、部署環境及使用者對象都有其獨特性。 初次部署時還相當安全的應用程式，隨著時間流逝，也可能變得不再那麼安全。 要精確預測未來可能發生什麼威脅是不可能的事。  
  
 SQL Server 這項產品已經歷經多個版本的演變，納入了最新的安全性功能，可以讓開發人員建立安全的資料庫應用程式。 不過，安全性並沒有單純的解決方案，而是需要持續的監控和更新。  
  
## <a name="common-threats"></a>常見威脅  
 開發人員需要了解安全性威脅、針對防禦這些威脅而提供的工具，以及如何避免自身造成的安全性漏洞。 安全性如同鏈結，任何環節的中斷都會危及整體的強度。 下列清單包含一些常見的安全性威脅，在本節的主題中將加以詳細討論。  
  
### <a name="sql-injection"></a>SQL 插入  
 「SQL 插入」(SQL Injection) 是指惡意的使用者用來輸入 Transact-SQL 陳述式 (而非有效輸入) 的流程。 如果該輸入未經驗證而直接傳遞至伺服器，而且應用程式不慎而執行了插入的程式碼，則攻擊就可能會危及或損毀資料。 您可以藉由使用預存程序 (Stored Procedure) 和參數化命令、避免動態 SQL 以及限制所有使用者的權限，來防堵 SQL Server 插入式攻擊。  
  
### <a name="elevation-of-privilege"></a>權限提高  
 權限提高攻擊會發生在使用者能夠取得受信任帳戶 (例如擁有者或系統管理員) 的權限時。 請務必在最小權限的帳戶下執行，並只指派必要的權限。 請避免使用系統管理員或擁有者帳戶執行程式碼。 如此就算攻擊成功，也可限制造成的傷害。 在執行需要其他權限的工作時，請只在工作期間才使用程序簽章或模擬。 您可以使用憑證來簽署預存程序，或使用模擬來暫時指派權限。  
  
### <a name="probing-and-intelligent-observation"></a>探查和智慧型觀測  
 探查攻擊可能會使用應用程式產生的錯誤訊息來搜尋安全性漏洞。 在所有程序性程式碼中實作錯誤處理，以避免 SQL Server 錯誤資訊傳回給使用者。  
  
### <a name="authentication"></a>驗證  
 如果以使用者輸入為基礎的連接字串是在執行階段建構，則在使用 SQL Server 登入時可能會發生連接字串插入攻擊。 如果沒有檢查連接字串是否具有有效的關鍵字字組，則攻擊者可以插入多餘的字元，而可能得以存取伺服器上的機密資料或其他資源。 請盡量使用 Windows 驗證。 如果必須使用 SQL Server 登入，請使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 在執行階段建立及驗證連接字串。  
  
### <a name="passwords"></a>密碼  
 許多攻擊之所以成功，都是因為侵入者得以取得或猜出授權使用者的密碼。 密碼是在面對侵入者時的第一道防線，所以設定強式密碼對於系統安全性而言十分關鍵。 針對混合模式驗證建立密碼原則並加以強制執行。  
  
 即使在使用「Windows 驗證」時，也請務必為 `sa` 帳戶指派強式密碼。  
  
## <a name="in-this-section"></a>本節內容  
 [在 SQL Server 中使用預存程序來管理權限](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 說明如何使用預存程序 (Stored Procedure) 管理權限並控制資料存取。 使用預存程序是許多安全性威脅的有效回應方式。  
  
 [在 SQL Server 中撰寫安全的動態 SQL](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 說明使用預存程序撰寫安全動態 SQL 的技巧。  
  
 [在 SQL Server 中簽署預存程序](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 說明如何使用憑證簽署預存程序，讓使用者可以使用不能直接存取的資料。 如此預存程序就可以執行呼叫端並無直接執行權限的作業。  
  
 [在 SQL Server 中使用模擬來自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 說明如何使用 EXECUTE AS 子句模擬其他使用者。 模擬會將執行內容從呼叫端切換到指定的使用者。  
  
 [在 SQL Server 中授與資料列層級權限](../../../../../docs/framework/data/adonet/sql/granting-row-level-permissions-in-sql-server.md)  
 說明如何實作資料列層級權限以限制資料存取。  
  
 [在 SQL Server 中建立應用程式角色](../../../../../docs/framework/data/adonet/sql/creating-application-roles-in-sql-server.md)  
 說明應用程式角色的功能。  
  
 [在 SQL Server 中啟用跨資料庫存取](../../../../../docs/framework/data/adonet/sql/enabling-cross-database-access-in-sql-server.md)  
 說明如何在不危及安全性的前提下啟用跨資料庫存取。  
  
## <a name="see-also"></a>另請參閱
- [SQL Server 安全性](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
