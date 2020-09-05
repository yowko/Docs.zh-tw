---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497877"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="8524a-101">路徑冒號檢查更嚴格</span><span class="sxs-lookup"><span data-stu-id="8524a-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="8524a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8524a-102">Details</span></span>

<span data-ttu-id="8524a-103">在 .NET Framework 4.6.2 中，為了支援先前所不支援的路徑 (就長度和格式兩方面) 而有數項變更。</span><span class="sxs-lookup"><span data-stu-id="8524a-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="8524a-104">檢查是否有適當的磁片磁碟機分隔符號 (冒號) 語法是否更正確，它的副作用是在一些先前容許的特定路徑 Api 中封鎖某些 URI 路徑。</span><span class="sxs-lookup"><span data-stu-id="8524a-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they were previously tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8524a-105">建議</span><span class="sxs-lookup"><span data-stu-id="8524a-105">Suggestion</span></span>

<span data-ttu-id="8524a-106">如果傳遞 URI 給受影響的 API，請先將字串修改為合法的路徑。</span><span class="sxs-lookup"><span data-stu-id="8524a-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span>

- <span data-ttu-id="8524a-107">以手動方式從 Url 移除配置 (例如， `file://` 從 url 移除) 。</span><span class="sxs-lookup"><span data-stu-id="8524a-107">Remove the scheme from URLs manually (for example, remove `file://` from URLs).</span></span>

- <span data-ttu-id="8524a-108">將 URI 傳遞給 <xref:System.Uri> 類別，並使用 <xref:System.Uri.LocalPath> 。</span><span class="sxs-lookup"><span data-stu-id="8524a-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath>.</span></span>

<span data-ttu-id="8524a-109">或者，您可以藉由將 AppCoNtext 參數設定為，退出宣告新的路徑正規化 `Switch.System.IO.UseLegacyPathHandling` `true` 。</span><span class="sxs-lookup"><span data-stu-id="8524a-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to `true`.</span></span>

| <span data-ttu-id="8524a-110">名稱</span><span class="sxs-lookup"><span data-stu-id="8524a-110">Name</span></span>    | <span data-ttu-id="8524a-111">值</span><span class="sxs-lookup"><span data-stu-id="8524a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8524a-112">範圍</span><span class="sxs-lookup"><span data-stu-id="8524a-112">Scope</span></span>   | <span data-ttu-id="8524a-113">Edge</span><span class="sxs-lookup"><span data-stu-id="8524a-113">Edge</span></span>        |
| <span data-ttu-id="8524a-114">版本</span><span class="sxs-lookup"><span data-stu-id="8524a-114">Version</span></span> | <span data-ttu-id="8524a-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8524a-115">4.6.2</span></span>       |
| <span data-ttu-id="8524a-116">類型</span><span class="sxs-lookup"><span data-stu-id="8524a-116">Type</span></span>    | <span data-ttu-id="8524a-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8524a-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8524a-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8524a-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
