---
ms.openlocfilehash: e36dac19beb6251debef100656670a6623344eea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237823"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>嘗試建立 TCP/IP 連線至解析為 `localhost` 的 SQL Server 資料庫會失敗

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6 和 4.6.1 中，嘗試建立 TCP/IP 連線至解析為 <code>localhost</code> 的 SQL Server 資料庫會失敗，錯誤為：「建立連線至 SQL Server 時，發生網路相關或執行個體特定的錯誤。 找不到或無法存取伺服器。 檢查執行個體名稱是否正確以及 SQL Server 執行個體是否設定為允許遠端連接。 (提供者：SQL 網路介面，錯誤：26 - 搜尋指定的伺服器/執行個體時發生錯誤)」|
|建議|在 .NET Framework 4.6.2 中已解決此問題，並還原舊版行為。 若要連線至解析為 <code>localhost</code> 的 SQL Server 資料庫，請升級至 .NET Framework 4.6.2。|
|影響範圍|Minor|
|版本|4.6|
|類型|執行階段|
