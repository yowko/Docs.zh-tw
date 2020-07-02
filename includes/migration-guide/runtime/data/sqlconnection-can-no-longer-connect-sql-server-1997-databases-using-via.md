---
ms.openlocfilehash: 241184d61d718fedfea396260e739d2dbc05c305
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620001"
---
### <a name="sqlconnection-can-no-longer-connect-to-sql-server-1997-or-databases-using-the-via-adapter"></a><span data-ttu-id="c479a-101">SqlConnection 無法再使用 VIA 配接器連線至 SQL Server 1997 或資料庫</span><span class="sxs-lookup"><span data-stu-id="c479a-101">SqlConnection can no longer connect to SQL Server 1997 or databases using the VIA adapter</span></span>

#### <a name="details"></a><span data-ttu-id="c479a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c479a-102">Details</span></span>

<span data-ttu-id="c479a-103">不再支援使用[虛擬介面卡（VIA）通訊協定](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105))連接到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c479a-103">Connections to SQL Server databases using the [Virtual Interface Adapter (VIA) protocol](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms191229(v=sql.105)) are no longer supported.</span></span> <span data-ttu-id="c479a-104">用來連線至 SQL Server 資料庫的通訊協定會顯示在接字串中。</span><span class="sxs-lookup"><span data-stu-id="c479a-104">The protocol used to connect to a SQL Server database is visible in the connection string.</span></span> <span data-ttu-id="c479a-105">VIA 連線將包含 via:&lt;伺服器名稱&gt;。</span><span class="sxs-lookup"><span data-stu-id="c479a-105">A VIA connection will contain via:&lt;servername&gt;.</span></span> <span data-ttu-id="c479a-106">如果此應用程式透過以外的通訊協定（例如 tcp：或 np：）連接到 SQL，則不會遇到中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="c479a-106">If this app is connecting to SQL via a protocol other than VIA (tcp: or np: for example), then no breaking change will be encountered.</span></span> <span data-ttu-id="c479a-107">此外，不再支援與 SQL Server 7 （1997）的連接。</span><span class="sxs-lookup"><span data-stu-id="c479a-107">Also, connections to SQL Server 7 (1997) are no longer supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c479a-108">建議</span><span class="sxs-lookup"><span data-stu-id="c479a-108">Suggestion</span></span>

<span data-ttu-id="c479a-109">VIA 通訊協定已淘汰，因此應該使用替代的通訊協定來連線至 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c479a-109">The VIA protocol is deprecated, so an alternative protocol should be used to connect to SQL databases.</span></span> <span data-ttu-id="c479a-110">最常用的通訊協定是 TCP/IP。</span><span class="sxs-lookup"><span data-stu-id="c479a-110">The most common protocol used is TCP/IP.</span></span> <span data-ttu-id="c479a-111">如需透過 TCP/IP 進行連線的詳細資訊，請參閱[啟用資料庫執行個體的 TCP/IP 通訊協定](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="c479a-111">For more information about connecting through TCP/IP, see [Enable the TCP/IP protocol for a database instance](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb909712(v=vs.90)).</span></span> <span data-ttu-id="c479a-112">如果只能從內部網路中存取資料庫，若網路太慢，則共用管道通訊協定可以提供更好的效能。</span><span class="sxs-lookup"><span data-stu-id="c479a-112">If the database is only accessed from within an intranet, the shared pipes protocol may provide better performance if the network is slow.</span></span>

| <span data-ttu-id="c479a-113">名稱</span><span class="sxs-lookup"><span data-stu-id="c479a-113">Name</span></span>    | <span data-ttu-id="c479a-114">值</span><span class="sxs-lookup"><span data-stu-id="c479a-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c479a-115">影響範圍</span><span class="sxs-lookup"><span data-stu-id="c479a-115">Scope</span></span>   |<span data-ttu-id="c479a-116">Edge</span><span class="sxs-lookup"><span data-stu-id="c479a-116">Edge</span></span>|
|<span data-ttu-id="c479a-117">版本</span><span class="sxs-lookup"><span data-stu-id="c479a-117">Version</span></span>|<span data-ttu-id="c479a-118">4.5</span><span class="sxs-lookup"><span data-stu-id="c479a-118">4.5</span></span>|
|<span data-ttu-id="c479a-119">類型</span><span class="sxs-lookup"><span data-stu-id="c479a-119">Type</span></span>|<span data-ttu-id="c479a-120">執行階段</span><span class="sxs-lookup"><span data-stu-id="c479a-120">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c479a-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c479a-121">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String)></li><li><xref:System.Data.SqlClient.SqlConnection.%23ctor(System.String,System.Data.SqlClient.SqlCredential)></li></ul>|
