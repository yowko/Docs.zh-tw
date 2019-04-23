---
ms.openlocfilehash: 1d2d6133683360b97569e49402e7c8c4d182b65d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803476"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a><span data-ttu-id="f1ee5-101">ObjectContext.Translate 和 ObjectContext.ExecuteStoreQuery 現在支援列舉類型</span><span class="sxs-lookup"><span data-stu-id="f1ee5-101">ObjectContext.Translate and ObjectContext.ExecuteStoreQuery now support enum type</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f1ee5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f1ee5-102">Details</span></span>|<span data-ttu-id="f1ee5-103">在 .NET Framework 4.0 中，<code>ObjectContext.Translate</code> 和 <code>ObjectContext.ExecuteStoreQuery</code> 方法的泛型參數 <code>T</code> 不可為列舉。</span><span class="sxs-lookup"><span data-stu-id="f1ee5-103">In .NET Framework 4.0, the generic parameter <code>T</code> of <code>ObjectContext.Translate</code> and <code>ObjectContext.ExecuteStoreQuery</code> methods could not be an enum.</span></span> <span data-ttu-id="f1ee5-104">現在支援這種情況。</span><span class="sxs-lookup"><span data-stu-id="f1ee5-104">That scenario is now supported.</span></span>|
|<span data-ttu-id="f1ee5-105">建議</span><span class="sxs-lookup"><span data-stu-id="f1ee5-105">Suggestion</span></span>|<span data-ttu-id="f1ee5-106">如果在 .NET Framework 4.0 中對列舉類型呼叫 Translate 或 ExecuteStoreQuery，則會傳回 '0'。</span><span class="sxs-lookup"><span data-stu-id="f1ee5-106">If Translate or ExecuteStoreQuery was called on an enum type in .NET Framework 4.0, '0' was returned.</span></span> <span data-ttu-id="f1ee5-107">如果這不是您要的行為，請以常數 0 (或相當於此值的列舉) 取代呼叫。</span><span class="sxs-lookup"><span data-stu-id="f1ee5-107">If that behavior was desirable, the calls should be replaced with a constant 0 (or the enum equivalent of it).</span></span>|
|<span data-ttu-id="f1ee5-108">範圍</span><span class="sxs-lookup"><span data-stu-id="f1ee5-108">Scope</span></span>|<span data-ttu-id="f1ee5-109">Edge</span><span class="sxs-lookup"><span data-stu-id="f1ee5-109">Edge</span></span>|
|<span data-ttu-id="f1ee5-110">版本</span><span class="sxs-lookup"><span data-stu-id="f1ee5-110">Version</span></span>|<span data-ttu-id="f1ee5-111">4.5</span><span class="sxs-lookup"><span data-stu-id="f1ee5-111">4.5</span></span>|
|<span data-ttu-id="f1ee5-112">類型</span><span class="sxs-lookup"><span data-stu-id="f1ee5-112">Type</span></span>|<span data-ttu-id="f1ee5-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="f1ee5-113">Runtime</span></span>|
|<span data-ttu-id="f1ee5-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="f1ee5-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
