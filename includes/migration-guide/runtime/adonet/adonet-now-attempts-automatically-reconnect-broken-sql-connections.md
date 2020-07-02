---
ms.openlocfilehash: 23ba6064a283b47312a66f3636c2834a7d58106e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619946"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="485dd-101">ADO.NET 現在會嘗試自動重新連接中斷的 SQL 連線</span><span class="sxs-lookup"><span data-stu-id="485dd-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="485dd-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="485dd-102">Details</span></span>

<span data-ttu-id="485dd-103">從 .NET Framework 4.5.1 中開始，.NET Framework 將嘗試自動重新連接中斷的 SQL 連線。</span><span class="sxs-lookup"><span data-stu-id="485dd-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="485dd-104">雖然這通常會讓應用程式更可靠，但是會有邊緣案例，應用程式必須知道連線已中斷，讓它可以在重新連接時採取某些動作。</span><span class="sxs-lookup"><span data-stu-id="485dd-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="485dd-105">建議</span><span class="sxs-lookup"><span data-stu-id="485dd-105">Suggestion</span></span>

<span data-ttu-id="485dd-106">如果基於相容性考量，您不想要這項功能，可以將連接字串的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> 屬性 (或 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) 設為 0 來加以停用。</span><span class="sxs-lookup"><span data-stu-id="485dd-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="485dd-107">名稱</span><span class="sxs-lookup"><span data-stu-id="485dd-107">Name</span></span>    | <span data-ttu-id="485dd-108">值</span><span class="sxs-lookup"><span data-stu-id="485dd-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="485dd-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="485dd-109">Scope</span></span>   |<span data-ttu-id="485dd-110">Edge</span><span class="sxs-lookup"><span data-stu-id="485dd-110">Edge</span></span>|
|<span data-ttu-id="485dd-111">版本</span><span class="sxs-lookup"><span data-stu-id="485dd-111">Version</span></span>|<span data-ttu-id="485dd-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="485dd-112">4.5.1</span></span>|
|<span data-ttu-id="485dd-113">類型</span><span class="sxs-lookup"><span data-stu-id="485dd-113">Type</span></span>|<span data-ttu-id="485dd-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="485dd-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="485dd-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="485dd-115">Affected APIs</span></span>

-<xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor></li><li><xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor></li><li><xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)></li></ul>|
