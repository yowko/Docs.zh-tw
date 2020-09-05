---
ms.openlocfilehash: 8c593fa6490451c6236f0d4390f09d4e9e4f0cbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497314"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="23fef-101">ObjectContext.CreateDatabase 和 DbProviderServices.CreateDatabase 方法處理例外狀況的方式不同</span><span class="sxs-lookup"><span data-stu-id="23fef-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

#### <a name="details"></a><span data-ttu-id="23fef-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="23fef-102">Details</span></span>

<span data-ttu-id="23fef-103">從 .NET Framework 4.5 開始，如果資料庫建立失敗，<code>CreateDatabase</code> 方法會嘗試卸除空白資料庫。</span><span class="sxs-lookup"><span data-stu-id="23fef-103">Beginning in .NET Framework 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="23fef-104">如果該作業成功，則會傳播原始 <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> (而不是在 .NET Framework 4.0 中一律擲回的 <xref:System.InvalidOperationException?displayProperty=fullName>)</span><span class="sxs-lookup"><span data-stu-id="23fef-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=fullName> that was always thrown in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="23fef-105">建議</span><span class="sxs-lookup"><span data-stu-id="23fef-105">Suggestion</span></span>

<span data-ttu-id="23fef-106">如果在執行 <xref:System.Data.Objects.ObjectContext.CreateDatabase> 或 <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> 時攔截 <xref:System.InvalidOperationException?displayProperty=fullName>，現在也應該要攔截 SQLException。</span><span class="sxs-lookup"><span data-stu-id="23fef-106">When catching an <xref:System.InvalidOperationException?displayProperty=fullName> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>

| <span data-ttu-id="23fef-107">名稱</span><span class="sxs-lookup"><span data-stu-id="23fef-107">Name</span></span>    | <span data-ttu-id="23fef-108">值</span><span class="sxs-lookup"><span data-stu-id="23fef-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="23fef-109">範圍</span><span class="sxs-lookup"><span data-stu-id="23fef-109">Scope</span></span>   |<span data-ttu-id="23fef-110">Minor</span><span class="sxs-lookup"><span data-stu-id="23fef-110">Minor</span></span>|
|<span data-ttu-id="23fef-111">版本</span><span class="sxs-lookup"><span data-stu-id="23fef-111">Version</span></span>|<span data-ttu-id="23fef-112">4.5</span><span class="sxs-lookup"><span data-stu-id="23fef-112">4.5</span></span>|
|<span data-ttu-id="23fef-113">類型</span><span class="sxs-lookup"><span data-stu-id="23fef-113">Type</span></span>|<span data-ttu-id="23fef-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="23fef-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="23fef-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="23fef-115">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>
- <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`
- `M:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)`

-->
