---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620030"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="d3e32-101">ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 現在支援列舉類型</span><span class="sxs-lookup"><span data-stu-id="d3e32-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

#### <a name="details"></a><span data-ttu-id="d3e32-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d3e32-102">Details</span></span>

<span data-ttu-id="d3e32-103">在 .NET Framework 4.0 中，<code>ObjectContext.Translate</code> 和 <code>ObjectContext.ExecuteStoreQuery</code> 方法的泛型參數 <code>T</code> 不可為列舉。</span><span class="sxs-lookup"><span data-stu-id="d3e32-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="d3e32-104">現在支援這種情況。</span><span class="sxs-lookup"><span data-stu-id="d3e32-104">That scenario is now supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d3e32-105">建議</span><span class="sxs-lookup"><span data-stu-id="d3e32-105">Suggestion</span></span>

<span data-ttu-id="d3e32-106">如果在 .NET Framework 4.0 中對列舉類型呼叫 Translate 或 ExecuteStoreQuery，則會傳回 '0'。</span><span class="sxs-lookup"><span data-stu-id="d3e32-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="d3e32-107">如果這不是您要的行為，請以常數 0 (或相當於此值的列舉) 取代呼叫。</span><span class="sxs-lookup"><span data-stu-id="d3e32-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>

| <span data-ttu-id="d3e32-108">名稱</span><span class="sxs-lookup"><span data-stu-id="d3e32-108">Name</span></span>    | <span data-ttu-id="d3e32-109">值</span><span class="sxs-lookup"><span data-stu-id="d3e32-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d3e32-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="d3e32-110">Scope</span></span>   |<span data-ttu-id="d3e32-111">Edge</span><span class="sxs-lookup"><span data-stu-id="d3e32-111">Edge</span></span>|
|<span data-ttu-id="d3e32-112">版本</span><span class="sxs-lookup"><span data-stu-id="d3e32-112">Version</span></span>|<span data-ttu-id="d3e32-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d3e32-113">4.5</span></span>|
|<span data-ttu-id="d3e32-114">類型</span><span class="sxs-lookup"><span data-stu-id="d3e32-114">Type</span></span>|<span data-ttu-id="d3e32-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="d3e32-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d3e32-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d3e32-116">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
