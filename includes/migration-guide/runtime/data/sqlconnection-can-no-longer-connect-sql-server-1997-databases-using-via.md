---
ms.openlocfilehash: e65ba0edb132f5cded244a69d58e43ffea76a039
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606324"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a>SqlConnection 無法再使用 VIA 配接器連線至 SQL Server 1997 或資料庫

#### <a name="details"></a>詳細資料

不再支援透過 [) 通訊協定使用虛擬介面配接器 (](/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) SQL Server 資料庫的連接。 用來連線至 SQL Server 資料庫的通訊協定會顯示在接字串中。 VIA 連線將包含 via:&lt;伺服器名稱&gt;。 如果此應用程式透過通訊協定（而非 VIA (tcp：或 np) ：）連接到 SQL，則不會發生任何重大變更。 此外，不再支援 SQL Server 7 (1997) 的連接。

#### <a name="suggestion"></a>建議

VIA 通訊協定已淘汰，因此應該使用替代的通訊協定來連線至 SQL 資料庫。 最常用的通訊協定是 TCP/IP。 如需透過 TCP/IP 進行連線的詳細資訊，請參閱[啟用資料庫執行個體的 TCP/IP 通訊協定](/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90))。 如果只能從內部網路中存取資料庫，若網路太慢，則共用管道通訊協定可以提供更好的效能。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
