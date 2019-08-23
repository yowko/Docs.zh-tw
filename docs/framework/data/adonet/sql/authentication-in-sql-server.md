---
title: 在 SQL Server 中進行驗證
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 1723552a48ebfa41e8d6a0f963154fc3b864119d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957485"
---
# <a name="authentication-in-sql-server"></a>在 SQL Server 中進行驗證
SQL Server 支援兩種驗證模式：Windows 驗證模式和混合模式。  
  
- Windows 驗證是預設設定，也經常稱為整合式安全性，因為這個 SQL Server 安全性模型會與 Windows 緊密整合。 特定的 Windows 使用者和群組帳戶會受信任而可登入 SQL Server。 已經過驗證的 Windows 使用者不必再提供額外認證資料。  
  
- 混合模式支援 Windows 和 SQL Server 提供的驗證。 使用者名稱和密碼組會在 SQL Server 內進行維護。  
  
> [!IMPORTANT]
> 建議盡量使用「Windows 驗證」。 Windows 驗證會使用一系列的加密訊息在 SQL Server 中驗證使用者。 使用 SQL Server 登入時, 系統會在網路上傳遞 SQL Server 登入名稱和加密的密碼, 使其較不安全。  
  
 使用 Windows 驗證的好處是因為使用者已登入 Windows，所以不必再另行登入 SQL Server。 下列`SqlConnection.ConnectionString`指定 Windows 驗證, 而不需要使用者提供使用者名稱或密碼。  
  
```  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> 登入不同於資料庫使用者。 您必須藉由個別作業，將登入或 Windows 群組對應到資料庫使用者或角色。 接著再將存取資料庫物件的權限授與使用者或角色。  
  
## <a name="authentication-scenarios"></a>驗證案例  
 在下列情況中，Windows 驗證通常是最佳選擇：  
  
- 有網域控制站存在。  
  
- 應用程式和資料庫位於相同的電腦。  
  
- 您使用的是 SQL Server Express 或 LocalDB 的實例。  
  
 SQL Server 登入通常用於以下狀況：  
  
- 如果您擁有工作群組。  
  
- 使用者是自不同的非受信任網域進行連接。  
  
- 網際網路應用程式, 例如 ASP.NET。  
  
> [!NOTE]
> 指定 Windows 驗證並不會停用 SQL Server 登入。 請使用 ALTER LOGIN DISABLE Transact-SQL 陳述式來停用具有高權限的 SQL Server 登入。  
  
## <a name="login-types"></a>登入類型  
 SQL Server 支援三種登入類型:  
  
- 本機 Windows 使用者帳戶或受信任的網域帳戶。 SQL Server 會仰賴 Windows 來驗證 Windows 使用者帳戶。  
  
- Windows 群組。 如果授與存取權給 Windows 群組，則也會授權給全部該群組成員的 Windows 使用者登入。  
  
- SQL Server 登入。 SQL Server 會將使用者名稱和密碼雜湊儲存在 master 資料庫，並使用內部驗證方法確認登入作業。  
  
> [!NOTE]
> SQL Server 提供從憑證建立的登入, 或僅用於程式碼簽署的非對稱金鑰。 而不會用來連接至 SQL Server。  
  
## <a name="mixed-mode-authentication"></a>混合模式驗證  
 如果您必須使用混合模式驗證，則必須建立儲存在 SQL Server 中的 SQL Server 登入。 然後在執行階段時還需要提供 SQL Server 使用者名稱和密碼。  
  
> [!IMPORTANT]
> SQL Server 會使用名為 `sa` (「系統管理員」的縮寫) 的 SQL Server 登入來進行安裝。 請指派強式密碼給 `sa` 登入，且不要在應用程式中使用 `sa` 登入。 `sa` 登入對應的是 `sysadmin` 固定伺服器角色，對於整個伺服器具有不可變更之管理權限。 如果攻擊者取得系統管理員的存取權，就可以大肆破壞而毫不受限。 Windows `BUILTIN\Administrators` 群組 (本機系統管理員群組) 的所有成員，都會預設為 `sysadmin` 角色的成員，但可以從該角色移除。  
  
 SQL Server 在或更新版本上[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)]執行時, 會為 SQL Server 登入提供 Windows 密碼原則機制。 密碼複雜性原則是為了阻止暴力攻擊而設計，方法是盡可能地增加密碼數目。 SQL Server 可以將中[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)]所使用的相同複雜性和到期原則套用至 SQL Server 內使用的密碼。  
  
> [!IMPORTANT]
> 串連來自使用者輸入的連接字串，可能會使您易遭受連接字串插入式攻擊。 請使用 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 在執行階段建立語法有效的連接字串。 如需詳細資訊，請參閱[連接字串建置器](../../../../../docs/framework/data/adonet/connection-string-builders.md)。  
  
## <a name="external-resources"></a>外部資源  
 如需詳細資訊，請參閱下列資源。  
  
|Resource|說明|  
|--------------|-----------------|  
|[原理](/sql/relational-databases/security/authentication-access/principals-database-engine)|描述 SQL Server 中的登入和其他安全性主體。|  
  
## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [連接至資料來源](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [連接字串](../../../../../docs/framework/data/adonet/connection-strings.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
