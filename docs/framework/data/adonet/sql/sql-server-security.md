---
title: SQL Server 安全性
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: eb9eb073eb2227ce98d4adb93b8f4b60575cf1b7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-security"></a>SQL Server 安全性
SQL Server 具有許多功能，可支援安全資料庫應用程式的建立。  
  
 資料竊取或破壞等一般的安全性考量，則適用於所有的 SQL Server 版本。 資料完整性也應視為安全性問題。 如果資料未受保護，可以對其進行臨機操作 (Ad Hoc)，或用能夠用錯誤的值不小心或惡意地加以修改或全部刪除，資料就可能變得毫無價值。 此外，也經常會有必須遵循的法律需求，例如機密資訊的正確儲存方式等。 依照特定管轄區適用的法律而定，某些類型的個人資料可能完全不得儲存。  
  
 如同每個 Windows 版本，每個 SQL Server 版本都具有不同的安全性功能，而越新的版本功能越強。 單靠安全性功能並不足以確保資料庫應用程式的安全，瞭解這點是很重要的。 每個資料庫應用程式的需求、執行環境、部署模型、實體位置和使用者族群都有其獨特性。 某些具有本機範圍的應用程式可能只需要最低的安全性，而其他的本機應用程式或透過 Internet 部署的應用程式卻可能需要嚴謹的安全性措施及持續不斷的監控和評估。  
  
 您應該在設計階段考量 SQL Server 資料庫應用程式的安全性需求，而不是事後才加以考量。 提早在開發週期中評估威脅，可增加在偵測到安全性漏洞時減少可能損害的機會。  
  
 即使一開始的應用程式設計安全無虞，隨著系統的演進，新的威脅也可能會出現。 藉由在資料庫周圍築起多道防線，您可以將安全性破壞所造成的損傷減至最少。 您的第一道防線是絕不授與比絕對必要多的權限，藉此而減少可能受到攻擊的表面區域。  
  
 本節中的主題簡要說明與開發人員相關的 SQL Server 安全性功能，並提供連結至《SQL Server 線上叢書》中的相關主題以及提供更深入探討的其他資源。  
  
## <a name="in-this-section"></a>本節內容  
 [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 說明 SQL Server 的架構和安全性功能。  
  
 [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 包含討論 ADO.NET 和 SQL Server 應用程式之各種應用程式安全性案例的主題。  
  
 [SQL Server Express 安全性](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 說明 SQL Server express 的安全性考量。  
  
## <a name="related-sections"></a>相關章節  
[SQL Server Database Engine 和 Azure SQL Database 的資訊安全中心](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
描述 SQL Server 和 Azure SQL Database 的安全性考量。

[SQL Server 安裝的安全性考量](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
描述安裝 SQL Server 之前應考量的安全性疑慮。

## <a name="see-also"></a>另請參閱  
 [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
