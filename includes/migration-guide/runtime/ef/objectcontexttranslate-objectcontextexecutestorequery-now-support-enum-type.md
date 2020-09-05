---
ms.openlocfilehash: 81992e57d7e92b4df92ce68870c0272d6cd5b220
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497554"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="a3476-101">ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 現在支援列舉類型</span><span class="sxs-lookup"><span data-stu-id="a3476-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="a3476-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a3476-102">Details</span></span>

<span data-ttu-id="a3476-103">在 .NET Framework 4.0 中，<code>ObjectContext.Translate</code> 和 <code>ObjectContext.ExecuteStoreQuery</code> 方法的泛型參數 <code>T</code> 不可為列舉。</span><span class="sxs-lookup"><span data-stu-id="a3476-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="a3476-104">現在支援這種情況。</span><span class="sxs-lookup"><span data-stu-id="a3476-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a3476-105">建議</span><span class="sxs-lookup"><span data-stu-id="a3476-105">Suggestion</span></span>

<span data-ttu-id="a3476-106">如果在 .NET Framework 4.0 中對列舉類型呼叫 Translate 或 ExecuteStoreQuery，則會傳回 '0'。</span><span class="sxs-lookup"><span data-stu-id="a3476-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="a3476-107">如果這不是您要的行為，請以常數 0 (或相當於此值的列舉) 取代呼叫。</span><span class="sxs-lookup"><span data-stu-id="a3476-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="a3476-108">名稱</span><span class="sxs-lookup"><span data-stu-id="a3476-108">Name</span></span>    | <span data-ttu-id="a3476-109">值</span><span class="sxs-lookup"><span data-stu-id="a3476-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a3476-110">範圍</span><span class="sxs-lookup"><span data-stu-id="a3476-110">Scope</span></span>   |<span data-ttu-id="a3476-111">Edge</span><span class="sxs-lookup"><span data-stu-id="a3476-111">Edge</span></span>|
|<span data-ttu-id="a3476-112">版本</span><span class="sxs-lookup"><span data-stu-id="a3476-112">Version</span></span>|<span data-ttu-id="a3476-113">4.5</span><span class="sxs-lookup"><span data-stu-id="a3476-113">4.5</span></span>|
|<span data-ttu-id="a3476-114">類型</span><span class="sxs-lookup"><span data-stu-id="a3476-114">Type</span></span>|<span data-ttu-id="a3476-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="a3476-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="a3476-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a3476-116">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType>
- <xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

<!--

#### Affected APIs

- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader)``
- ``M:System.Data.Objects.ObjectContext.Translate``1(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.Object[])``
- ``M:System.Data.Objects.ObjectContext.ExecuteStoreQuery``1(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])``

-->
