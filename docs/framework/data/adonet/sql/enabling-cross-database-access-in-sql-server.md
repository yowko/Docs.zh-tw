---
title: "在 SQL Server 中啟用跨資料庫存取 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: 10
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 10
---
# 在 SQL Server 中啟用跨資料庫存取
當一個資料庫中的程序是依照另一個資料庫中的物件而定時，就會發生跨資料庫擁有權鏈結。  跨資料庫擁有權鏈結的運作方式與單一資料庫內的擁有權鏈結相同，但未中斷的擁有權鏈結需要所有的物件擁有者都對應至相同的登入帳戶。  如果來源資料庫中的來源物件以及目標資料庫中的目標物件是由相同的登入帳戶所擁有，則 SQL Server 不會檢查目標物件上的權限。  
  
## 預設關閉  
 跨資料庫的擁有權鏈結預設會關閉。  Microsoft 建議您停用跨資料庫的擁有權鏈結，因為這項功能會使您暴露於下列的安全性風險：  
  
-   資料庫擁有者、`db_ddladmin` 的成員或者 `db_owners` 資料庫角色都可以建立由其他使用者擁有的物件。  這些物件可能會以其他資料庫中的物件為目標。  這表示如果啟用跨資料庫的擁有權鏈結，則必須完全信任這些使用者使用所有資料庫中的資料。  
  
-   具有 CREATE DATABASE 權限的使用者可以建立新的資料庫及附加現有的資料庫。  如果啟用跨資料庫擁有權鏈結，這些使用者即可從其新建立或附加的資料庫，存取其他資料庫中他們可能並不擁有權限的物件。  
  
## 啟用跨資料庫擁有權鏈結  
 只有在可以完全信任高權限使用者的環境中，才應該啟用跨資料庫擁有權鏈結。  這項功能可在所有資料庫的安裝期間設定，或者使用 [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] 命令 `sp_configure` 和 `ALTER DATABASE` 選擇性地針對特定的資料庫設定。  
  
 若要選擇性地設定跨資料庫擁有權鏈結，請使用 `sp_configure` 關閉伺服器的這項功能。  然後使用具有 SET DB\_CHAINING ON 的 ALTER DATABASE 命令，僅針對需要此功能的資料庫設定跨資料庫擁有權鏈結。  
  
 下列範例會開啟所有資料庫的跨資料庫擁有權鏈結：  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 下列範例會開啟特定資料庫的跨資料庫擁有權鏈結：  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
  
```  
  
### 動態 SQL  
 在執行動態建立之 SQL 陳述式的情況中，無法使用跨資料庫擁有權鏈結，除非兩個資料庫中存在相同的使用者。  您可以在 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 中建立存取其他資料庫資料的預存程序，並使用存在於兩個資料庫中的憑證來簽署程序，藉此解決上述問題。  如此可以讓使用者存取該程序所使用的資料庫資源，而不必為其授與資料庫存取權或權限。  
  
## 外部資源  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------|--------|  
|[使用 EXECUTE AS 擴充資料庫模擬](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx)和[跨資料庫擁有權鏈結伺服器組態選項](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]線上叢書。|說明如何針對 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 的執行個體設定跨資料庫擁有權鏈結的主題。|  
  
## 請參閱  
 [保護 ADO.NET 應用程式](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server 安全性的概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)   
 [在 SQL Server 中使用預存程序管理權限](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)   
 [在 SQL Server 中撰寫安全的動態 SQL](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)   
 [在 SQL Server 中簽署預存程序](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)   
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)