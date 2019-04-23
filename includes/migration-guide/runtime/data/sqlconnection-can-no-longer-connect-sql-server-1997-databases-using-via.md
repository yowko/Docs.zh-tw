---
ms.openlocfilehash: fcaee245e98dfe71beb4042a2664a14b64cf2398
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803501"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection 無法再使用 VIA 配接器連線至 SQL Server 1997 或資料庫

|   |   |
|---|---|
|詳細資料|不再支援使用[虛擬介面配接器 (VIA) 通訊協定](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229%28v=sql.105%29)至 SQL Server 資料庫。 用來連線至 SQL Server 資料庫的通訊協定會顯示在接字串中。 VIA 連線將包含 via:&lt;伺服器名稱&gt;。 如果此應用程式透過 VIA 以外的通訊協定 (例如 tcp: 或 np:) 連線至 SQL，則不會發生任何重大變更。此外，不再支援連線至 SQL Server 7 (1997)。|
|建議|VIA 通訊協定已淘汰，因此應該使用替代的通訊協定來連線至 SQL 資料庫。 最常用的通訊協定是 TCP/IP。 如需透過 TCP/IP 進行連線的詳細資訊，請參閱[啟用資料庫執行個體的 TCP/IP 通訊協定](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90))。 如果只能從內部網路中存取資料庫，若網路太慢，則共用管道通訊協定可以提供更好的效能。|
|範圍|Edge|
|版本|4.5|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)?displayProperty=nameWithType></li></ul>|
