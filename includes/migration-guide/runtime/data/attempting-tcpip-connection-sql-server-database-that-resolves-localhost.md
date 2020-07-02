---
ms.openlocfilehash: 87cb2570d3d47a2acb85b5557141c0fef885516a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621776"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>嘗試建立 TCP/IP 連線至解析為 `localhost` 的 SQL Server 資料庫會失敗

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6 和 4.6.1 中，嘗試建立 TCP/IP 連線至解析為 <code>localhost</code> 的 SQL Server 資料庫會失敗，錯誤為：「建立連線至 SQL Server 時，發生網路相關或執行個體特定的錯誤。 找不到或無法存取伺服器。 檢查執行個體名稱是否正確以及 SQL Server 執行個體是否設定為允許遠端連接。 (提供者：SQL 網路介面，錯誤：26 - 搜尋指定的伺服器/執行個體時發生錯誤)」

#### <a name="suggestion"></a>建議

在 .NET Framework 4.6.2 中已解決此問題，並還原舊版行為。 若要連線至解析為 <code>localhost</code> 的 SQL Server 資料庫，請升級至 .NET Framework 4.6.2。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.6|
|類型|執行階段|
