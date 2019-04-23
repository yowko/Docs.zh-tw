---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234894"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="03e47-101">路徑冒號檢查更嚴格</span><span class="sxs-lookup"><span data-stu-id="03e47-101">Path colon checks are stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="03e47-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="03e47-102">Details</span></span>|<span data-ttu-id="03e47-103">在 .NET Framework 4.6.2 中，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。</span><span class="sxs-lookup"><span data-stu-id="03e47-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="03e47-104">對於適當磁碟機分隔符號 (冒號) 語法的檢查更為正確，副作用則是會封鎖一些選取路徑 API 中的某些 URI 路徑，而在過去都會容許它們。</span><span class="sxs-lookup"><span data-stu-id="03e47-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>|
|<span data-ttu-id="03e47-105">建議</span><span class="sxs-lookup"><span data-stu-id="03e47-105">Suggestion</span></span>|<span data-ttu-id="03e47-106">如果傳遞 URI 給受影響的 API，請先將字串修改為合法的路徑。</span><span class="sxs-lookup"><span data-stu-id="03e47-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="03e47-107">以手動方式從 URL 移除配置 (例如從 URL 移除 <code>file://</code>)</span><span class="sxs-lookup"><span data-stu-id="03e47-107">Remove the scheme from URLs manually (e.g. remove <code>file://</code> from URLs)</span></span></li><li><span data-ttu-id="03e47-108">將 URI 傳遞給 <xref:System.Uri> 類別，並且使用</span><span class="sxs-lookup"><span data-stu-id="03e47-108">Pass the URI to the <xref:System.Uri> class and use</span></span> <xref:System.Uri.LocalPath></li></ul><span data-ttu-id="03e47-109">或者，將 <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext 參數設為 true，以選擇退出新的路徑正規化。</span><span class="sxs-lookup"><span data-stu-id="03e47-109">Alternatively, you can opt out of the new path normalization by setting the <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext switch to true.</span></span>|
|<span data-ttu-id="03e47-110">範圍</span><span class="sxs-lookup"><span data-stu-id="03e47-110">Scope</span></span>|<span data-ttu-id="03e47-111">Edge</span><span class="sxs-lookup"><span data-stu-id="03e47-111">Edge</span></span>|
|<span data-ttu-id="03e47-112">版本</span><span class="sxs-lookup"><span data-stu-id="03e47-112">Version</span></span>|<span data-ttu-id="03e47-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="03e47-113">4.6.2</span></span>|
|<span data-ttu-id="03e47-114">類型</span><span class="sxs-lookup"><span data-stu-id="03e47-114">Type</span></span>|<span data-ttu-id="03e47-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="03e47-115">Retargeting</span></span>|
|<span data-ttu-id="03e47-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="03e47-116">Affected APIs</span></span>|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
