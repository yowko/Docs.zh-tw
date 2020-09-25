---
title: SQL Server 中的應用程式安全性案例
ms.date: 03/30/2017
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.openlocfilehash: 2d0e65f61939312bf29111e87c49366cd9e389be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197647"
---
# <a name="application-security-scenarios-in-sql-server"></a>SQL Server 中的應用程式安全性案例

並沒有單一的正確方式可建立安全的 SQL Server 用戶端應用程式。 每個應用程式的需求、部署環境與使用者母體都是唯一的。 一開始部署時相當安全的應用程式，其安全性可能會隨著時間過去而降低。 沒有任何方式能夠準確預測未來可能會出現什麼樣的威脅。  
  
 SQL Server 這個產品已經演變許多版本以納入最新的安全性功能，讓開發人員能建立安全的資料庫應用程式。 不過，安全性並不會無中生有，需要透過持續地監視及更新才能獲得。  
  
## <a name="common-threats"></a>常見威脅  

 開發人員必須了解安全性威脅、用來計算威脅的工具，以及如何避免自我造成的安全性漏洞。 我們可以將安全性視為一個鏈結，其中任何一個連結中斷都會危害整體的強度。 下列清單包含一些常見的安全性威脅，我們會在此節的主題中深入討論。  
  
### <a name="sql-injection"></a>SQL 插入  

 SQL 插入式攻擊是指惡意使用者輸入 Transact-SQL 陳述式，而非提供有效輸入的程序。 如果在未驗證的情況下將輸入直接傳遞至伺服器，而且應用程式不慎執行了以資料隱碼方式撰寫的程式碼，攻擊就可能會破壞或損毀資料。 您可以透過預存程序和參數化命令、避免動態 SQL 以及限制所有使用者的權限來防堵 SQL Server 插入式攻擊。  
  
### <a name="elevation-of-privilege"></a>提高權限  

 當使用者能夠取得像是擁有者或系統管理員等受信任帳戶的權限時，就會發生權限提高攻擊。 因此請一律使用具備最低權限的使用者帳戶來執行，並只指派需要的權限。 避免使用系統管理或擁有者帳戶來執行程式碼。 這可以限制攻擊成功時可能產生的破壞力。 執行需要額外權限的工作時，請只在工作期間使用程序簽署或模擬。 您可以用憑證來簽署預存程序，或使用模擬來暫時指派權限。  
  
### <a name="probing-and-intelligent-observation"></a>探查和智慧型觀測  

 探查攻擊可能會使用應用程式所產生的錯誤訊息來搜尋安全性弱點。 請在所有程序性程式碼中實作錯誤處理功能，以防止系統將 SQL Server 錯誤資訊傳回給終端使用者。  
  
### <a name="authentication"></a>驗證  

 如果以使用者輸入為基礎的連接字串是在執行階段所建構的，使用 SQL Server 登入時就可能會發生連接字串插入式攻擊。 如果未檢查連接字串是否包含有效的關鍵字組，攻擊者就可能會透過插入額外的字元，來存取伺服器上的機密資料或其他資源。 可能的話，請盡量使用 Windows 驗證。 如果您必須使用 SQL Server 登入，請使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder>，以在執行階段建立及驗證連接字串。  
  
### <a name="passwords"></a>密碼  

 許多攻擊能夠成功的原因在於入侵者能夠取得或猜出有特殊權限的使用者密碼。 密碼是對抗入侵者的第一道防線，因此，設定強式密碼對於系統的安全性很重要。 針對混合模式驗證建立並強制執行密碼原則。  
  
 即使使用「Windows 驗證」，也請一律指派強式密碼給 `sa` 帳戶。  
  
## <a name="in-this-section"></a>本節內容  

 [使用預存程序管理 SQL Server 中的權限](managing-permissions-with-stored-procedures-in-sql-server.md)  
 說明如何使用預存程序 (Stored Procedure) 管理權限並控制資料存取。 使用預存程序是許多安全性威脅的有效回應方式。  
  
 [在 SQL Server 撰寫安全動態 SQL](writing-secure-dynamic-sql-in-sql-server.md)  
 說明使用預存程序撰寫安全動態 SQL 的技術。  
  
 [在 SQL Server 中簽署預存程序](signing-stored-procedures-in-sql-server.md)  
 說明如何使用憑證簽署預存程序，讓使用者可以使用不能直接存取的資料。 如此預存程序就可以執行呼叫端並無直接執行權限的作業。  
  
 [在 SQL Server 中使用模擬來自訂權限](customizing-permissions-with-impersonation-in-sql-server.md)  
 說明如何使用 EXECUTE AS 子句模擬其他使用者。 模擬會將執行內容從呼叫端切換到指定的使用者。  
  
 [在 SQL Server 中授與資料列層級權限](granting-row-level-permissions-in-sql-server.md)  
 說明如何實作資料列層級權限以限制資料存取。  
  
 [在 SQL Server 中建立應用程式角色](creating-application-roles-in-sql-server.md)  
 說明應用程式角色的功能。  
  
 [在 SQL Server 中啟用跨資料庫存取](enabling-cross-database-access-in-sql-server.md)  
 說明如何在不危及安全性的前提下啟用跨資料庫存取。  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 安全性](sql-server-security.md)
- [SQL Server 安全性概觀](overview-of-sql-server-security.md)
- [設定 ADO.NET 應用程式的安全性](../securing-ado-net-applications.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
