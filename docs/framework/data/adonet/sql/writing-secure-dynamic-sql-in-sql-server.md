---
title: 在 SQL Server 中撰寫安全的動態 SQL
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: 0dc372b4e5554623d51a4add9a43f33d4a320f18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>在 SQL Server 中撰寫安全的動態 SQL
「SQL 插入」(SQL Injection) 是指惡意的使用者用來輸入 Transact-SQL 陳述式 (而非有效輸入) 的流程。 如果該輸入未經驗證而直接傳遞至伺服器，而且應用程式不慎執行了插入的程式碼，則攻擊就可能會危及或損毀資料。  
  
 您應該檢閱建構 SQL 陳述式的任何程序是否有插入弱點，因為 SQL Server 將會執行所有它收到的語法有效查詢。 即使是參數化的資料也可能會被富有技巧且果決的攻擊者所操作。 如果有使用動態 SQL，請務必將命令參數化，也絕對不要在查詢字串中直接包含參數值。  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>SQL 插入式攻擊的分析  
 插入程序的運作方式是不當地結束文字字串並附加新的命令。 由於插入的命令可能會在執行之前附加其他字串，因此攻擊者會使用註解標記 "--" 來結束插入的字串。 如此一來，系統會在執行時忽略後續文字。 攻擊者可能會使用分號 (;) 分隔符號 (Delimiter) 來插入多個命令。  
  
 只要插入的 SQL 程式碼語法正確，您就無法以程式設計方式來偵測出是否遭竄改。 因此，您必須驗證所有使用者輸入並仔細地檢閱在您目前使用之伺服器上執行建構 SQL 命令的程式碼。 絕對不要串連未經驗證的使用者輸入。 字串串連是指令碼攻擊的主要進入點。  
  
 下面是一些有用的方針：  
  
-   絕對不要直接根據使用者輸入來建立 Transact-SQL 陳述式，請使用預存程序 (Stored Procedure) 來驗證使用者輸入。  
  
-   透過測試型別、長度、格式和範圍，驗證使用者輸入。 請使用 Transact-SQL QUOTENAME() 函式來逸出系統名稱或使用 REPLACE() 函式來逸出字串中的任何字元。  
  
-   在每個應用程式層中實作多個驗證層。  
  
-   測試輸入的大小和資料型別並強制執行適當的限制。 這樣做有助於防止故意的緩衝區滿溢。  
  
-   測試字串變數的內容並僅接受預期的值。 請拒絕包含二進位資料、逸出序列 (Escape Sequence) 和註解字元的項目。  
  
-   如果您要使用 XML 文件，請在資料進入時，針對結構描述來驗證所有資料。  
  
-   在多層環境中，所有資料都應該先進行驗證，然後才能進入受信任的區域。  
  
-   在可用以建構檔案名稱的欄位中，不接受下列字串：AUX、CLOCK$、COM1 到 COM8、CON、CONFIG$、LPT1 到 LPT8、NUL 和 PRN。  
  
-   請使用 <xref:System.Data.SqlClient.SqlParameter> 物件搭配預存程序和命令來提供型別檢查 (Type Checking) 和長度驗證。  
  
-   請在用戶端程式碼中使用 <xref:System.Text.RegularExpressions.Regex> 運算式來篩選無效的字元。  
  
## <a name="dynamic-sql-strategies"></a>動態 SQL 策略  
 在程序性程式碼中執行動態建立的 SQL 陳述式會中斷擁有權鏈結，進而導致 SQL Server 針對動態 SQL 所存取的物件，檢查呼叫端的權限。  
  
 SQL Server 提供兩種方法，可使用執行動態 SQL 的預存程序和使用者定義函式，來授與資料存取權給使用者。  
  
-   使用模擬搭配 TRANSACT-SQL EXECUTE AS 子句中所述[模擬 SQL Server 中的自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)。  
  
-   簽署憑證，預存程序中所述[SQL Server 中簽署預存程序](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)。  
  
### <a name="execute-as"></a>EXECUTE AS  
 EXECUTE AS 子句會將呼叫端的權限取代成 EXECUTE AS 子句中指定之使用者的權限。 巢狀預存程序或觸發程序 (Trigger) 會在 Proxy 使用者的安全性內容底下執行。 這樣會中斷仰賴列層級安全性或需要稽核的應用程式。 傳回使用者識別的某些函式會傳回 EXECUTE AS 子句中指定的使用者，而非原始呼叫端。 只有在執行此程序之後，或發出 REVERT 陳述式時，執行內容才會還原成原始呼叫端。  
  
### <a name="certificate-signing"></a>憑證簽署  
 當您執行已經使用某個憑證簽署的預存程序時，授與憑證使用者的權限就會與呼叫端的權限合併。 雖然執行內容維持不變，但是憑證使用者無法模擬呼叫端。 簽署預存程序需要實作許多步驟。 每次修改此程序時，您就必須重新簽署程序。  
  
### <a name="cross-database-access"></a>跨資料庫存取  
 在執行動態建立之 SQL 陳述式的情況中，跨資料庫擁有權鏈結沒有作用。 您可以解決此 SQL Server 中建立預存程序，以便存取另一個資料庫中的資料，並簽署的憑證，這兩個資料庫中有程序。 如此可以讓使用者存取該程序所使用的資料庫資源，而不必為其授與資料庫存取權或權限。  
  
## <a name="external-resources"></a>外部資源  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[預存程序](http://go.microsoft.com/fwlink/?LinkId=98233)和[SQL 資料隱碼](http://go.microsoft.com/fwlink/?LinkId=98234)SQL Server 線上叢書中|說明如何建立預存程序以及「SQL 插入」運作方式的主題。|  
|[新的 SQL 截斷攻擊和如何加以避免](http://msdn.microsoft.com/msdnmag/issues/06/11/SQLSecurity/)MSDN Magazine 中。|說明如何分隔字元和字串、SQL 插入和截斷攻擊的修改。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [在 SQL Server 中使用預存程序來管理權限](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [在 SQL Server 中簽署預存程序](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [在 SQL Server 中使用模擬來自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
