---
title: SQL Server 安全性概觀
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: adc1ce661d49c468de09552ea36a2cd58d6343f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780946"
---
# <a name="overview-of-sql-server-security"></a>SQL Server 安全性概觀
具有重疊安全性層的深入防禦策略是抵禦安全性威脅的最佳方式。 SQL Server 提供了一種安全性架構，其設計目的是為了允許資料庫管理員和開發人員建立安全的資料庫應用程式並抵禦威脅。 每個 SQL Server 版本都會透過引進新的特性和功能來改善舊版 SQL Server。 不過，安全性無法一體適用。 每個應用程式的安全性需求都是唯一的。 開發人員必須瞭解哪些特性和功能的組合最適合用來抵禦已知威脅，以及預期未來可能會發生的威脅。  
  
 SQL Server 執行個體包含階層式實體 (Entity) 集合，從伺服器開始。 每個伺服器都包含多個資料庫，而每個資料庫都包含安全性實體物件的集合。 每個 SQL Server 安全性實體都有相關聯的*許可權*，可授與*主體*，也就是授與 SQL Server 存取權的個人、群組或進程。 SQL Server 安全性架構會透過*驗證*和*授權*來管理安全實體的存取權。  
  
- 驗證是指登入 SQL Server 的程序，其中主體會透過提交伺服器評估的認證來要求存取。 驗證會建立正在進行驗證之使用者或處理序的識別。  
  
- 授權是指決定主體可存取哪些安全性實體資源，以及允許針對這些資源進行哪些作業的程序。  
  
 本節中的主題涵蓋了 SQL Server 安全性基本概念，並提供《SQL Server 線上叢書》相關版本中完整文件的連結。  
  
## <a name="in-this-section"></a>本節內容  
 [在 SQL Server 中進行驗證](authentication-in-sql-server.md)  
 說明 SQL Server 中的登入和驗證，並提供其他資源的連結。  
  
 [SQL Server 中的伺服器和資料庫角色](server-and-database-roles-in-sql-server.md)  
 說明固定伺服器和資料庫角色、自訂資料庫角色和內建帳戶，並提供其他資源的連結。  
  
 [SQL Server 中的擁有權和使用者結構描述分離](ownership-and-user-schema-separation-in-sql-server.md)  
 說明物件擁有權和使用者結構描述分隔，並提供其他資源的連結。  
  
 [SQL Server 中的授權和權限](authorization-and-permissions-in-sql-server.md)  
 說明如何使用最小權限的原則來授與權限，並提供其他資源的連結。  
  
 [在 SQL Server 中加密資料](data-encryption-in-sql-server.md)  
 說明 SQL Server 中的資料加密選項，並提供其他資源的連結。  
  
 [SQL Server 中的 CLR 整合安全性](clr-integration-security-in-sql-server.md)  
 提供 CLR 整合安全性資源的連結。  
  
## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../securing-ado-net-applications.md)
- [SQL Server 安全性](sql-server-security.md)
- [SQL Server 中的應用程式安全性案例](application-security-scenarios-in-sql-server.md)
- [ADO.NET 概觀](../ado-net-overview.md)
