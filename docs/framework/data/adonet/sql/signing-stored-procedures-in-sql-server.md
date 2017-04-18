---
title: "在 SQL Server 中簽署預存程序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# 在 SQL Server 中簽署預存程序
您可以使用憑證或非對稱金鑰來簽署預存程序。  這是針對無法透過擁有權鏈結繼承權限或擁有權鏈結中斷 \(例如動態 SQL\) 的案例所設計。  然後，您可以建立對應至憑證的使用者，並授與該預存程序需要存取之物件的權限給憑證使用者。  
  
 執行此預存程序時，SQL Server 會結合憑證使用者的權限與呼叫端的權限。  與 EXECUTE AS 子句不同的是，它不會變更程序的執行內容。  傳回登入和使用者名稱的內建函式會傳回呼叫端的名稱，而非憑證使用者名稱。  
  
 數位簽章是指使用簽署者之私密金鑰 \(Private Key\) 加密的資料摘要。  私密金鑰可確保數位簽章對於其 Bearer 或擁有者而言是唯一的。  您可以簽署預存程序、函式或觸發程序 \(Trigger\)。  
  
> [!NOTE]
>  您可以在 master 資料庫中建立憑證，以便授與伺服器層級權限。  
  
## 建立憑證  
 當您使用憑證來簽署預存程序時，系統會使用私密金鑰來建立資料摘要，其中包含預存程序程式碼的加密雜湊。  在執行階段中，系統會使用公開金鑰 \(Public Key\) 來解密資料摘要，並與預存程序的雜湊值 \(Hash Value\) 進行比較。  修改預存程序會讓雜湊值無效，因而導致數位簽章不再相符。  這樣做可防止沒有私密金鑰存取權的人員變更預存程序程式碼。  因此，每次修改程序時，您就必須重新簽署程序。  
  
 簽署模組包含四個步驟：  
  
1.  使用 Transact\-SQL `CREATE CERTIFICATE [certificateName]` 陳述式來建立憑證。  這個陳述式具有許多設定開始和結束日期與密碼的選項。  預設的到期日是一年。  
  
2.  使用 Transact\-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` 陳述式來建立與憑證相關聯的資料庫使用者。  這位使用者僅存在資料庫中，而且與登入沒有任何關聯。  
  
3.  授與資料庫物件的必要權限給憑證使用者。  
  
> [!NOTE]
>  憑證無法授與權限給擁有使用 DENY 陳述式撤銷之權限的使用者。  DENY 的優先順序永遠高於 GRANT，可防止呼叫端繼承授與憑證使用者的權限。  
  
1.  使用 Transact\-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` 陳述式並搭配憑證來簽署程序。  
  
## 外部資源  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------|--------|  
|《SQL Server 線上叢書》的[模組簽署](http://go.microsoft.com/fwlink/?LinkId=98590)|說明模組簽署，並提供範例案例以及相關 Transact\-SQL 主題的連結。|  
|《SQL Server 線上叢書》的[使用憑證簽署預存程序](http://msdn.microsoft.com/library/bb283630.aspx)|提供使用憑證來簽署預存程序的教學課程。|  
  
## 請參閱  
 [保護 ADO.NET 應用程式](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server 安全性的概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)   
 [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)   
 [在 SQL Server 中使用預存程序管理權限](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)   
 [在 SQL Server 中撰寫安全的動態 SQL](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)   
 [使用 SQL Server 中的模擬來自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)   
 [使用預存程序修改資料](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)