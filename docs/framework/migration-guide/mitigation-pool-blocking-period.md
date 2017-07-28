---
title: "風險降低︰集區封鎖期"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: caaaafaff44f2a679b16fe3f1aae59bcf717388e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-pool-blocking-period"></a>風險降低︰集區封鎖期
已移除 Azure SQL Database 連線的連線集區封鎖期。  
  
## <a name="additional-description"></a>其他描述  
 在 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 和舊版中，如果應用程式在連線到資料庫時發生暫時性連線失敗，由於連線集區會快取此錯誤並在 5 秒鐘到 1 分鐘後重新擲回，因此無法很快就重試連線。如需詳細資訊，請參閱 [SQL Server 連線共用 (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。 此行為會對 Azure SQL Database 連線造成問題，連線通常會因暫時性錯誤而失敗，而且一般會在幾秒內復原。 連線集區封鎖功能表示應用程式有很長的一段時間無法連線到資料庫，即使資料庫可供使用也一樣。 此行為特別會對連線到 Azure SQL Database 且需要在幾秒內轉譯的 Web 應用程式造成問題。  
  
 從 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 開始，針對已知 Azure SQL Database (*.database.windows.net、\*.database.chinacloudapi.cn、\*.database.usgovcloudapi.net、\*.database.cloudapi.de) 的連線開啟要求，不會快取連線開啟錯誤。 至於所有其他連線嘗試，則會繼續強制執行連線集區封鎖期。  
  
## <a name="impact"></a>影響  
 這項變更允許立即重試 Azure SQL Database 的連線開啟嘗試，因而提升啟用雲端功能的應用程式效能。  
  
## <a name="mitigation"></a>緩和  
 如果這項變更會對應用程式造成負面影響，可以藉由設定新的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> 屬性，來設定連線集區封鎖期。  屬性的值是 <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=fullName> 列舉的成員，可以採用三個值的其中一個值︰  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 將 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> 屬性設為 `PoolBlockingPeriod.AlwaysBlock` 可以還原舊有行為。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)

