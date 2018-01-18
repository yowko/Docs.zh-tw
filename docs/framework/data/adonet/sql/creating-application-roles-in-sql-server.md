---
title: "在 SQL Server 中建立應用程式角色"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27442435-dfb2-4062-8c59-e2960833a638
caps.latest.revision: "9"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a6c8027e3cbf7bcef3bbe36ba381a08b650516bc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="creating-application-roles-in-sql-server"></a>在 SQL Server 中建立應用程式角色
應用程式角色可以用於將權限指派給應用程式，而不是資料庫角色或使用者。 使用者可以連接到資料庫、啟動應用程式角色，並採用授與應用程式的權限。 授與應用程式角色的權限在連接期間內都會維持有效。  
  
> [!IMPORTANT]
>  當用戶端應用程式在連接字串中提供應用程式角色名稱和密碼時，就會啟動應用程式角色。 這些角色在雙層 (Two-Tier) 應用程式中會造成安全性弱點，因為密碼必須儲存在用戶端電腦上。 在三層 (Three-Tier) 應用程式中，則可以用應用程式使用者無法存取的方式來儲存密碼。  
  
## <a name="application-role-features"></a>應用程式角色功能  
 應用程式角色有下列功能：  
  
-   不同於資料庫角色，應用程式角色不包含任何成員。  
  
-   當用戶端應用程式為 `sp_setapprole` 系統預存程序 (Stored Procedure) 提供應用程式角色名稱和密碼時，就會啟動應用程式角色。  
  
-   密碼必須儲存在用戶端電腦上，並在執行階段提供；您無法從 SQL Server 內部啟動應用程式角色。  
  
-   密碼不會加密。 參數密碼會儲存為單向雜湊。  
  
-   透過應用程式角色所取得的權限一旦啟動，在連接期間內都會維持有效。  
  
-   應用程式會繼承授與 `public` 角色的權限。  
  
-   如果 `sysadmin` 固定伺服器角色的成員啟動了應用程式角色，則安全性內容會在連接期間切換至應用程式角色的安全性內容。  
  
-   如果在具有應用程式角色的資料庫中建立 `guest` 帳戶，則不需要針對該應用程式角色或叫用 (Invoke) 該角色的登入而建立資料庫使用者帳戶。 只有當 `guest` 帳戶存在於第二個資料庫中的時候，應用程式角色才可以直接存取其他資料庫。  
  
-   傳回登入名稱 (例如 SYSTEM_USER) 的內建功能會傳回叫用應用程式角色的登入名稱； 傳回資料庫使用者名稱的內建功能則會傳回應用程式角色的名稱。  
  
### <a name="the-principle-of-least-privilege"></a>最小權限的原則  
 應用程式角色僅能被授與必要的權限，以免密碼遭到破解。 在所有使用應用程式角色的資料庫中，則應該額銷 `public` 角色的權限。 請在不想讓應用程式角色的呼叫端存取的資料庫中，停用 `guest` 帳戶。  
  
### <a name="application-role-enhancements"></a>應用程式角色加強功能  
 啟用應用程式角色之後，可以將執行內容切換回原始呼叫端，免除了停用連線集區的需要。 `sp_setapprole` 程序具有建立 Cookie 的新選項，Cookie 中可包含有關呼叫端的內容資訊。 您可以呼叫 `sp_unsetapprole` 程序並將 Cookie 傳送給它，藉此還原工作階段 (Session)。  
  
## <a name="application-role-alternatives"></a>應用程式角色替代方案  
 應用程式角色仰賴密碼的安全性，而這點可能會造成安全性弱點。 密碼可能會因內嵌在應用程式程式碼或儲存在磁碟中而外洩。  
  
 您可能要考慮以下的替代方案。  
  
-   藉由 EXECUTE AS 陳述式 (使用 NO REVERT 和 WITH COOKIE 子句) 使用內容切換。 您可以在資料庫中建立不與登入對應的使用者帳戶， 然後再將權限指派給這個帳戶。 以無登入的使用者來使用 EXECUTE AS 比較安全，因為這種方式是以權限為基礎，而不是以密碼為基礎。 如需詳細資訊，請參閱[模擬 SQL Server 中的自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)。  
  
-   使用憑證來簽署預存程序，且僅授與執行程序的權限。 如需詳細資訊，請參閱[SQL Server 中簽署預存程序](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)。  
  
## <a name="external-resources"></a>外部資源  
 如需詳細資訊，請參閱下列資源。  
  
|資源|描述|  
|--------------|-----------------|  
|[應用程式角色](http://msdn.microsoft.com/library/ms190998.aspx)SQL Server 線上叢書中|說明如何在 SQL Server 2008 中建立及使用應用程式角色。|  
  
## <a name="see-also"></a>請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
