---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760716"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="b13b0-101">允許在與 UNC 共用相似的 URI 中使用 Unicode</span><span class="sxs-lookup"><span data-stu-id="b13b0-101">Allow Unicode in URIs that resemble UNC shares</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b13b0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b13b0-102">Details</span></span>|<span data-ttu-id="b13b0-103">在 <xref:System.Uri?displayProperty=fullName> 中，若您建構的檔案 URI 同時包含 UNC 共用名稱和 Unicode 字元時，不會再導致 URI 出現無效的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="b13b0-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="b13b0-104">這項行為只有在下列所有條件都符合時才會變更：</span><span class="sxs-lookup"><span data-stu-id="b13b0-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="b13b0-105">URI 具有 <code>file:</code> 配置，且後接 4 條以上的斜線。</span><span class="sxs-lookup"><span data-stu-id="b13b0-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="b13b0-106">主機名稱開頭為底線或其他非保留符號。</span><span class="sxs-lookup"><span data-stu-id="b13b0-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="b13b0-107">URI 包含 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="b13b0-107">The URI contains Unicode characters.</span></span></li></ul>|
|<span data-ttu-id="b13b0-108">建議</span><span class="sxs-lookup"><span data-stu-id="b13b0-108">Suggestion</span></span>|<span data-ttu-id="b13b0-109">如果應用程式使用的 URI 始終包含 Unicode，可想而知，該應用程式會使用這項行為來禁止參考 UNC 共用。</span><span class="sxs-lookup"><span data-stu-id="b13b0-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="b13b0-110">因此，這類應用程式應該改用 <xref:System.Uri.IsUnc>。</span><span class="sxs-lookup"><span data-stu-id="b13b0-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>|
|<span data-ttu-id="b13b0-111">範圍</span><span class="sxs-lookup"><span data-stu-id="b13b0-111">Scope</span></span>|<span data-ttu-id="b13b0-112">Edge</span><span class="sxs-lookup"><span data-stu-id="b13b0-112">Edge</span></span>|
|<span data-ttu-id="b13b0-113">版本</span><span class="sxs-lookup"><span data-stu-id="b13b0-113">Version</span></span>|<span data-ttu-id="b13b0-114">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b13b0-114">4.7.2</span></span>|
|<span data-ttu-id="b13b0-115">類型</span><span class="sxs-lookup"><span data-stu-id="b13b0-115">Type</span></span>|<span data-ttu-id="b13b0-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="b13b0-116">Runtime</span></span>|
|<span data-ttu-id="b13b0-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b13b0-117">Affected APIs</span></span>|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

