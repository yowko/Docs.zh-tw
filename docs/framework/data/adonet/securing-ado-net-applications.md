---
title: 設定 ADO.NET 應用程式的安全性
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 32d3de15242aaf9cfacd9371289a5a0a675f884b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149379"
---
# <a name="securing-adonet-applications"></a>設定 ADO.NET 應用程式的安全性
撰寫安全的 ADO.NET 應用程式並不只是為了避免常見的編碼錯誤，例如未驗證使用者輸入。 用於存取資料的應用程式有許多潛在的錯誤，攻擊者可以利用這些錯誤來擷取、管理或毀損機密資料。 因此，了解安全性的所有面向就相當重要，從應用程式設計階段期間的威脅模組處理，到最終的部署以及進行中的作業，都包括在內。  
  
 .NET Framework 提供許多有用的類別 (Class)、服務和工具，能用於保護及管理資料庫應用程式。 Common Language Runtime (CLR) 提供型別安全的環境，讓您在其中執行程式碼，方法是使用程式碼存取安全性 (CAS)，進一步限制 Managed 程式碼的使用權限。 遵循安全資料存取編碼實務，可限制潛在的攻擊者所可能造成的損害。  
  
 撰寫安全的程式碼，並不能防衛在使用 Unmanged 資源 (例如資料庫) 時自身造成的安全性漏洞。 大部分的伺服器資料庫 (例如 SQL Server) 都擁有自己的安全性系統，如果實作正確即可提升安全性。 不過，即使是具有嚴密安全性系統的資料來源，如果設定不正確，也可能在攻擊中受損。  
  
## <a name="in-this-section"></a>本節內容  
 [安全性概觀](../../../../docs/framework/data/adonet/security-overview.md)  
 針對設計安全的 ADO. NET 應用程式提供建議。  
  
 [安全存取資料](../../../../docs/framework/data/adonet/secure-data-access.md)  
 說明如何使用安全資料來源的資料。  
  
 [保護用戶端應用程式的安全](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 說明用戶端應用程式的安全性考量。  
  
 [程式碼存取安全性和 ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)  
 說明 CAS 如何協助保護 ADO.NET 程式碼， 也將討論如何使用部分信任。  
  
 [隱私權和資料安全性](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 說明 ADO. NET 應用程式的加密選項。  
  
## <a name="related-sections"></a>相關章節  
 [SQL Server 安全性](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 從開發人員的觀點說明 SQL Server 安全性功能。  
  
 [安全性考量](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 描述 Entity Framework 應用程式的安全性。  
  
 [安全性](../../../../docs/standard/security/index.md)  
 包含說明 .NET 中所有安全性面向之主題的連結。  
  
 [安全性工具](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 保護及管理安全性原則的 .NET Framework 工具。  
  
 [建立安全應用程式的資源](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 提供建立安全應用程式的主題連結。  
  
 [安全性參考書目](/visualstudio/ide/security-bibliography)  
 提供可線上使用及列印版本的外部資源連結。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET Managed 提供者和DataSet開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
