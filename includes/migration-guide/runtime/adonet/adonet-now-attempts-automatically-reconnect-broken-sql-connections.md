---
ms.openlocfilehash: 7f7e718d543a4abdf2b8a87e52d8c0e2ba28203f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497751"
---
### <a name="adonet-now-attempts-to-automatically-reconnect-broken-sql-connections"></a><span data-ttu-id="877c9-101">ADO.NET 現在會嘗試自動重新連接中斷的 SQL 連線</span><span class="sxs-lookup"><span data-stu-id="877c9-101">ADO.NET now attempts to automatically reconnect broken SQL connections</span></span>

#### <a name="details"></a><span data-ttu-id="877c9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="877c9-102">Details</span></span>

<span data-ttu-id="877c9-103">從 .NET Framework 4.5.1 中開始，.NET Framework 將嘗試自動重新連接中斷的 SQL 連線。</span><span class="sxs-lookup"><span data-stu-id="877c9-103">Beginning in the .NET Framework 4.5.1, the .NET Framework will attempt to automatically reconnect broken SQL connections.</span></span> <span data-ttu-id="877c9-104">雖然這通常會讓應用程式更可靠，但是會有邊緣案例，應用程式必須知道連線已中斷，讓它可以在重新連接時採取某些動作。</span><span class="sxs-lookup"><span data-stu-id="877c9-104">Although this will typically make apps more reliable, there are edge cases in which an app needs to know that the connection was lost so that it can take some action upon reconnection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="877c9-105">建議</span><span class="sxs-lookup"><span data-stu-id="877c9-105">Suggestion</span></span>

<span data-ttu-id="877c9-106">如果基於相容性考量，您不想要這項功能，可以將連接字串的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> 屬性 (或 <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) 設為 0 來加以停用。</span><span class="sxs-lookup"><span data-stu-id="877c9-106">If this feature is undesirable due to compatibility concerns, it can be disabled by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectRetryCount?displayProperty=fullName> property of a connection string (or <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName>) to 0.</span></span>

| <span data-ttu-id="877c9-107">名稱</span><span class="sxs-lookup"><span data-stu-id="877c9-107">Name</span></span>    | <span data-ttu-id="877c9-108">值</span><span class="sxs-lookup"><span data-stu-id="877c9-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="877c9-109">範圍</span><span class="sxs-lookup"><span data-stu-id="877c9-109">Scope</span></span>   |<span data-ttu-id="877c9-110">Edge</span><span class="sxs-lookup"><span data-stu-id="877c9-110">Edge</span></span>|
|<span data-ttu-id="877c9-111">版本</span><span class="sxs-lookup"><span data-stu-id="877c9-111">Version</span></span>|<span data-ttu-id="877c9-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="877c9-112">4.5.1</span></span>|
|<span data-ttu-id="877c9-113">類型</span><span class="sxs-lookup"><span data-stu-id="877c9-113">Type</span></span>|<span data-ttu-id="877c9-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="877c9-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="877c9-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="877c9-115">Affected APIs</span></span>

- <xref:System.Data.IDbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Configuration.ConnectionStringSettings.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.Common.DbConnectionStringBuilder.ConnectionString?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor>
- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.%23ctor(System.String)>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor>
- <xref:System.Data.Common.DbConnectionStringBuilder.%23ctor(System.Boolean)>

<!--

#### Affected APIs

- `P:System.Data.IDbConnection.ConnectionString`
- `P:System.Data.SqlClient.SqlConnection.ConnectionString`
- `P:System.Configuration.ConnectionStringSettings.ConnectionString`
- `P:System.Data.Common.DbConnection.ConnectionString`
- `P:System.Data.Common.DbConnectionStringBuilder.ConnectionString`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor`
- `M:System.Data.SqlClient.SqlConnectionStringBuilder.#ctor(System.String)`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor`
- `M:System.Data.Common.DbConnectionStringBuilder.#ctor(System.Boolean)`

-->
