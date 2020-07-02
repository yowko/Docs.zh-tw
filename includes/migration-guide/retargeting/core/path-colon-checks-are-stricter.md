---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614349"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="e1cb2-101">路徑冒號檢查更嚴格</span><span class="sxs-lookup"><span data-stu-id="e1cb2-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="e1cb2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1cb2-102">Details</span></span>

<span data-ttu-id="e1cb2-103">在 .NET Framework 4.6.2 中，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。</span><span class="sxs-lookup"><span data-stu-id="e1cb2-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="e1cb2-104">對於適當磁碟機分隔符號 (冒號) 語法的檢查更為正確，副作用則是會封鎖一些選取路徑 API 中的某些 URI 路徑，而在過去都會容許它們。</span><span class="sxs-lookup"><span data-stu-id="e1cb2-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e1cb2-105">建議</span><span class="sxs-lookup"><span data-stu-id="e1cb2-105">Suggestion</span></span>

<span data-ttu-id="e1cb2-106">如果傳遞 URI 給受影響的 API，請先將字串修改為合法的路徑。</span><span class="sxs-lookup"><span data-stu-id="e1cb2-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="e1cb2-107">以手動方式從 URL 移除配置 (例如從 URL 移除 `file://`)</span><span class="sxs-lookup"><span data-stu-id="e1cb2-107">Remove the scheme from URLs manually (e.g. remove `file://` from URLs)</span></span>

- <span data-ttu-id="e1cb2-108">將 URI 傳遞給 <xref:System.Uri> 類別，並且使用 <xref:System.Uri.LocalPath></span><span class="sxs-lookup"><span data-stu-id="e1cb2-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span>

<span data-ttu-id="e1cb2-109">或者，將 `Switch.System.IO.UseLegacyPathHandling` AppContext 參數設為 true，以選擇退出新的路徑正規化。</span><span class="sxs-lookup"><span data-stu-id="e1cb2-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to true.</span></span>

| <span data-ttu-id="e1cb2-110">名稱</span><span class="sxs-lookup"><span data-stu-id="e1cb2-110">Name</span></span>    | <span data-ttu-id="e1cb2-111">值</span><span class="sxs-lookup"><span data-stu-id="e1cb2-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e1cb2-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e1cb2-112">Scope</span></span>   | <span data-ttu-id="e1cb2-113">Edge</span><span class="sxs-lookup"><span data-stu-id="e1cb2-113">Edge</span></span>        |
| <span data-ttu-id="e1cb2-114">版本</span><span class="sxs-lookup"><span data-stu-id="e1cb2-114">Version</span></span> | <span data-ttu-id="e1cb2-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e1cb2-115">4.6.2</span></span>       |
| <span data-ttu-id="e1cb2-116">類型</span><span class="sxs-lookup"><span data-stu-id="e1cb2-116">Type</span></span>    | <span data-ttu-id="e1cb2-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="e1cb2-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="e1cb2-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e1cb2-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
