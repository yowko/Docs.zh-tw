---
title: 在 SQL Server 中簽署預存程序
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 2c2076294c0e06ec411ceb1f5b1238dc3d7eb304
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313914"
---
# <a name="signing-stored-procedures-in-sql-server"></a>在 SQL Server 中簽署預存程序
 數位簽章是指使用簽署者之私密金鑰 (Private Key) 加密的資料摘要。 私密金鑰可確保數位簽章對於其 Bearer 或擁有者而言是唯一的。 您可以簽署預存程序、 函式 （除了內嵌資料表值函式）、 觸發程序，以及組件。  
  
 您可以使用憑證或非對稱金鑰來簽署預存程序。 這是針對無法透過擁有權鏈結繼承權限或擁有權鏈結中斷 (例如動態 SQL) 的案例所設計。 然後您可以建立對應至憑證的使用者授與憑證的預存程序需要存取的物件上的使用者權限。  

 您可以也建立登入對應到相同的憑證，然後授與任何必要的伺服器層級權限，該登入，或新增的登入一或多個固定的伺服器角色。 這為了避免在`TRUSTWORTHY`資料庫所需較高的層級權限的情況下的設定。  
  
 執行預存程序時，SQL Server 會結合憑證使用者和/或登入的權限與呼叫端。 不同於`EXECUTE AS`子句，它不會變更的程序的執行內容。 傳回登入和使用者名稱的內建函式會傳回呼叫端的名稱，而非憑證使用者名稱。  
  
## <a name="creating-certificates"></a>建立憑證  
 當您登入時使用憑證或非對稱金鑰加密的預存程序程式碼，以及執行的雜湊所組成的資料摘要的預存程序-身為使用者，會使用建立的私密金鑰。 在執行階段中，系統會使用公開金鑰 (Public Key) 來解密資料摘要，並與預存程序的雜湊值 (Hash Value) 進行比較。 變更 execute-因為使用者會使數位簽章不再相符，導致無效的雜湊值。 修改預存程序會卸除簽章完全，這可防止沒有私密金鑰存取權變更的預存程序程式碼的人。 在任一情況下，您必須重新簽署程序每次變更的程式碼或 execute-以使用者身分。  
  
 簽署模組是兩個所需的步驟：  
  
1. 使用 Transact-SQL `CREATE CERTIFICATE [certificateName]` 陳述式來建立憑證。 這個陳述式具有許多設定開始和結束日期與密碼的選項。 預設的到期日是一年。  
  
1. 使用 Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` 陳述式並搭配憑證來簽署程序。  

一旦已簽署的模組，一或多個主體，就必須建立以便保存應與憑證相關聯的額外權限。  

如果此模組需要額外的資料庫層級權限：  
  
1. 使用 Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` 陳述式來建立與憑證相關聯的資料庫使用者。 這位使用者只會在資料庫中存在，而且不與登入相關聯，除非也從相同的憑證建立登入。  
  
1. 授與憑證使用者必要的資料庫層級權限。  
  
如果此模組需要額外的伺服器層級權限：  
  
1. 若要將憑證複製`master`資料庫。  
 
1. 建立與使用 TRANSACT-SQL 該憑證相關聯的登入`CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]`陳述式。  
  
1. 授與憑證登入需要的伺服器層級權限。  
  
> [!NOTE]  
>  憑證無法授與權限給擁有使用 DENY 陳述式撤銷之權限的使用者。 DENY 的優先順序永遠高於 GRANT，可防止呼叫端繼承授與憑證使用者的權限。  
  
## <a name="external-resources"></a>外部資源  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[模組簽署](https://go.microsoft.com/fwlink/?LinkId=98590)中 SQL Server 線上叢書|說明模組簽署，並提供範例案例以及相關 Transact-SQL 主題的連結。|  
|[簽署憑證的預存程序](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)中 SQL Server 線上叢書|提供使用憑證來簽署預存程序的教學課程。|  
  
## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [在 SQL Server 中使用預存程序來管理權限](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [在 SQL Server 中撰寫安全的動態 SQL](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [在 SQL Server 中使用模擬來自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [使用預存程序修改資料](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
