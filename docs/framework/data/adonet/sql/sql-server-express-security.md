---
title: SQL Server Express 安全性
ms.date: 03/30/2017
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.openlocfilehash: f4291de89b397f60aedd35b89d6aa3130d348be5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61876781"
---
# <a name="sql-server-express-security"></a>SQL Server Express 安全性
Microsoft SQL Server Express Edition (SQL Server Express) 是以 Microsoft SQL Server 為基礎，可支援大部分資料庫引擎的功能。 其設計方式是在預設情況下關閉非必要的功能和網路連接。 這樣做可減少受到惡意使用者攻擊的表面區域。  
  
 SQL Server Express 通常會安裝成具名執行個體。 此執行個體的預設名稱為 `SQLExpress`。 具名執行個體是由電腦的網路名稱以及您在安裝期間指定的執行個體名稱所識別。  
  
## <a name="network-access"></a>網路存取  
 基於安全性考量，SQL Server Express 中的網路通訊協定預設是停用的。 這樣做可防止外部使用者的攻擊，避免危害裝載 SQL Server Express 執行個體的電腦。 您必須明確啟用網路連接並啟動 SQL Server Browser 服務，才能從另一部電腦連接至 SQL Server Express 執行個體。  
  
 一旦網路連接啟用之後，SQL Server Express 執行個體與其他 SQL Server 版本便具有相同的安全性需求。  
  
## <a name="user-instances"></a>使用者執行個體  
 使用者執行個體是 SQL Server Express Database Engine 的獨立執行個體，由 SQL Server Express 父執行個體所產生。 使用者執行個體的主要目標是允許在最小權限使用者帳戶底下執行 Windows 的使用者，針對其本機電腦上的 SQL Server Express 執行個體擁有系統管理員 (`sysadmin`) 權限。 使用者執行個體不適用於在其電腦上具有系統管理員身分的使用者。  
  
 使用者執行個體是從代表使用者的 SQL Server 或 SQL Server Express 主要執行個體產生。 它會在使用者的 Windows 安全性內容底下當做使用者處理序執行，而非當做服務執行。 此時，系統不允許 SQL Server 登入，僅支援 Windows 登入。 這樣做可防止使用者執行個體上執行的軟體進行該使用者無權執行的整個系統範圍變更。 此外，使用者執行個體也稱為子或用戶端執行個體，而且有時候會使用 RANU 縮寫 (「以一般使用者的身分執行」) 表示。  
  
 每個使用者執行個體都與其父執行個體以及在相同電腦上執行的其他使用者執行個體隔離。 安裝在使用者執行個體上的資料庫只會以單一使用者模式開啟，因此多位使用者無法連接至這些資料庫。 使用者執行個體的複寫、分散式查詢和遠端連接都是停用的。 當使用者連接至使用者執行個體時，他們對於 SQL Server Express 父執行個體並沒有任何特殊權限。  
  
## <a name="external-resources"></a>外部資源  
 如需 SQL Server Express 的詳細資訊，請參閱下列資源。  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition 線上叢書](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|SQL Server 2005 Express Edition 的完整文件。|  
|[非系統管理員的使用者執行個體](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100))中 SQL Server 線上叢書|說明如何建立和部署使用者執行個體。|  
|[SQL Server Express 使用者執行個體](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)|說明 ADO.NET 應用程式中的使用者執行個體功能。 提供有關如何啟用使用者執行個體、使用 <xref:System.Data.SqlClient.SqlConnection> 來連接至使用者執行個體、使用者執行個體存留期 (Lifetime) 和使用者執行個體案例的資訊。|  
  
## <a name="see-also"></a>另請參閱

- [SQL Server 安全性](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [SQL Server Express 使用者執行個體](../../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
