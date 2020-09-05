---
ms.openlocfilehash: 8dc947f584d3433f0638a72f4db86ac2680c8dbf
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496555"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="4d36d-101">SqlConnection 無法再使用 VIA 配接器連線至 SQL Server 1997 或資料庫</span><span class="sxs-lookup"><span data-stu-id="4d36d-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="4d36d-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4d36d-102">Details</span></span>

<span data-ttu-id="4d36d-103">不再支援透過 [) 通訊協定使用虛擬介面配接器 (](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) SQL Server 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="4d36d-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="4d36d-104">用來連線至 SQL Server 資料庫的通訊協定會顯示在接字串中。</span><span class="sxs-lookup"><span data-stu-id="4d36d-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="4d36d-105">VIA 連線將包含 via:&lt;伺服器名稱&gt;。</span><span class="sxs-lookup"><span data-stu-id="4d36d-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="4d36d-106">如果此應用程式透過通訊協定（而非 VIA (tcp：或 np) ：）連接到 SQL，則不會發生任何重大變更。</span><span class="sxs-lookup"><span data-stu-id="4d36d-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="4d36d-107">此外，不再支援 SQL Server 7 (1997) 的連接。</span><span class="sxs-lookup"><span data-stu-id="4d36d-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4d36d-108">建議</span><span class="sxs-lookup"><span data-stu-id="4d36d-108">Suggestion</span></span>

<span data-ttu-id="4d36d-109">VIA 通訊協定已淘汰，因此應該使用替代的通訊協定來連線至 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d36d-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="4d36d-110">最常用的通訊協定是 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="4d36d-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="4d36d-111">如需透過 TCP/IP 進行連線的詳細資訊，請參閱[啟用資料庫執行個體的 TCP/IP 通訊協定](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="4d36d-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="4d36d-112">如果只能從內部網路中存取資料庫，若網路太慢，則共用管道通訊協定可以提供更好的效能。</span><span class="sxs-lookup"><span data-stu-id="4d36d-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="4d36d-113">名稱</span><span class="sxs-lookup"><span data-stu-id="4d36d-113">Name</span></span>    | <span data-ttu-id="4d36d-114">值</span><span class="sxs-lookup"><span data-stu-id="4d36d-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4d36d-115">範圍</span><span class="sxs-lookup"><span data-stu-id="4d36d-115">Scope</span></span>   |<span data-ttu-id="4d36d-116">Edge</span><span class="sxs-lookup"><span data-stu-id="4d36d-116">Edge</span></span>|
|<span data-ttu-id="4d36d-117">版本</span><span class="sxs-lookup"><span data-stu-id="4d36d-117">Version</span></span>|<span data-ttu-id="4d36d-118">4.5</span><span class="sxs-lookup"><span data-stu-id="4d36d-118">4.5</span></span>|
|<span data-ttu-id="4d36d-119">類型</span><span class="sxs-lookup"><span data-stu-id="4d36d-119">Type</span></span>|<span data-ttu-id="4d36d-120">執行階段</span><span class="sxs-lookup"><span data-stu-id="4d36d-120">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4d36d-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4d36d-121">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)>
- <xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String)`
- `M:System.Data.SqlClient.SqlConnection.#ctor(System.String,System.Data.SqlClient.SqlCredential)`

-->
