---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621065"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a><span data-ttu-id="18ac5-101">允許在與 UNC 共用相似的 URI 中使用 Unicode</span><span class="sxs-lookup"><span data-stu-id="18ac5-101">Allow Unicode in URIs that resemble UNC shares</span></span>

#### <a name="details"></a><span data-ttu-id="18ac5-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="18ac5-102">Details</span></span>

<span data-ttu-id="18ac5-103">在 <xref:System.Uri?displayProperty=fullName> 中，若您建構的檔案 URI 同時包含 UNC 共用名稱和 Unicode 字元時，不會再導致 URI 出現無效的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="18ac5-103">In <xref:System.Uri?displayProperty=fullName>, constructing a file URI containing both a UNC share name and Unicode characters will no longer result in a URI with invalid internal state.</span></span> <span data-ttu-id="18ac5-104">這項行為只有在下列所有條件都符合時才會變更：</span><span class="sxs-lookup"><span data-stu-id="18ac5-104">The behavior will change only when all of the following are true:</span></span><ul><li><span data-ttu-id="18ac5-105">URI 具有 <code>file:</code> 配置，且後接 4 條以上的斜線。</span><span class="sxs-lookup"><span data-stu-id="18ac5-105">The URI has the scheme <code>file:</code> and is followed by four or more slashes.</span></span></li><li><span data-ttu-id="18ac5-106">主機名稱開頭為底線或其他非保留符號。</span><span class="sxs-lookup"><span data-stu-id="18ac5-106">The host name begins with an underscore or other non-reserved symbol.</span></span></li><li><span data-ttu-id="18ac5-107">URI 包含 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="18ac5-107">The URI contains Unicode characters.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="18ac5-108">建議</span><span class="sxs-lookup"><span data-stu-id="18ac5-108">Suggestion</span></span>

<span data-ttu-id="18ac5-109">如果應用程式使用的 URI 始終包含 Unicode，可想而知，該應用程式會使用這項行為來禁止參考 UNC 共用。</span><span class="sxs-lookup"><span data-stu-id="18ac5-109">Applications working with URIs consistently containing Unicode could have conceivably used this behavior to disallow references to UNC shares.</span></span> <span data-ttu-id="18ac5-110">因此，這類應用程式應該改用 <xref:System.Uri.IsUnc>。</span><span class="sxs-lookup"><span data-stu-id="18ac5-110">Those applications should use <xref:System.Uri.IsUnc> instead.</span></span>

| <span data-ttu-id="18ac5-111">名稱</span><span class="sxs-lookup"><span data-stu-id="18ac5-111">Name</span></span>    | <span data-ttu-id="18ac5-112">值</span><span class="sxs-lookup"><span data-stu-id="18ac5-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="18ac5-113">影響範圍</span><span class="sxs-lookup"><span data-stu-id="18ac5-113">Scope</span></span>   |<span data-ttu-id="18ac5-114">Edge</span><span class="sxs-lookup"><span data-stu-id="18ac5-114">Edge</span></span>|
|<span data-ttu-id="18ac5-115">版本</span><span class="sxs-lookup"><span data-stu-id="18ac5-115">Version</span></span>|<span data-ttu-id="18ac5-116">4.7.2</span><span class="sxs-lookup"><span data-stu-id="18ac5-116">4.7.2</span></span>|
|<span data-ttu-id="18ac5-117">類型</span><span class="sxs-lookup"><span data-stu-id="18ac5-117">Type</span></span>|<span data-ttu-id="18ac5-118">執行階段</span><span class="sxs-lookup"><span data-stu-id="18ac5-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="18ac5-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="18ac5-119">Affected APIs</span></span>

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
