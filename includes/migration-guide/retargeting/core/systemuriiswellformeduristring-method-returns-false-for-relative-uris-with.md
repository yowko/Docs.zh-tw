---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617141"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a><span data-ttu-id="336d2-101">System.Uri.IsWellFormedUriString 方法針對第一個區段中有冒號字元的相對 URI 會傳回 false</span><span class="sxs-lookup"><span data-stu-id="336d2-101">System.Uri.IsWellFormedUriString method returns false for relative URIs with a colon char in first segment</span></span>

#### <a name="details"></a><span data-ttu-id="336d2-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="336d2-102">Details</span></span>

<span data-ttu-id="336d2-103">從 .NET Framework 4.5 開始，<xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> 會將第一個區段中具有 `:` 的相對 URI 視為格式不正確。</span><span class="sxs-lookup"><span data-stu-id="336d2-103">Beginning with the .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> will treat relative URIs with a `:` in their first segment as not well formed.</span></span> <span data-ttu-id="336d2-104">這是 .NET Framework 4.0 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> 行為的變更，以符合 RFC3986。</span><span class="sxs-lookup"><span data-stu-id="336d2-104">This is a change from <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> behavior in the .NET Framework 4.0 that was made to conform to RFC3986.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="336d2-105">建議</span><span class="sxs-lookup"><span data-stu-id="336d2-105">Suggestion</span></span>

<span data-ttu-id="336d2-106">這項變更 (就像許多其他的 URI 變更一樣) 只會影響以 .NET Framework 4.5 (或更新版本) 為目標的應用程式。</span><span class="sxs-lookup"><span data-stu-id="336d2-106">This change (like many other URI changes) will only affect applications targeting the .NET Framework 4.5 (or later).</span></span> <span data-ttu-id="336d2-107">若要繼續使用舊的行為，請將應用程式設為以 .NET Framework 4.0 為目標。</span><span class="sxs-lookup"><span data-stu-id="336d2-107">To keep using the old behavior, target the app against the .NET Framework 4.0.</span></span> <span data-ttu-id="336d2-108">或者，在呼叫 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> 前掃描 URI，尋找 `:` 字元，如果您偏好舊的行為，則請移除字元以進行驗證。</span><span class="sxs-lookup"><span data-stu-id="336d2-108">Alternatively, scan URI's prior to calling <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> looking for `:` characters that you may want to remove for validation purposes, if the old behavior is desirable.</span></span>

| <span data-ttu-id="336d2-109">名稱</span><span class="sxs-lookup"><span data-stu-id="336d2-109">Name</span></span>    | <span data-ttu-id="336d2-110">值</span><span class="sxs-lookup"><span data-stu-id="336d2-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="336d2-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="336d2-111">Scope</span></span>   | <span data-ttu-id="336d2-112">Minor</span><span class="sxs-lookup"><span data-stu-id="336d2-112">Minor</span></span>       |
| <span data-ttu-id="336d2-113">版本</span><span class="sxs-lookup"><span data-stu-id="336d2-113">Version</span></span> | <span data-ttu-id="336d2-114">4.5</span><span class="sxs-lookup"><span data-stu-id="336d2-114">4.5</span></span>         |
| <span data-ttu-id="336d2-115">類型</span><span class="sxs-lookup"><span data-stu-id="336d2-115">Type</span></span>    | <span data-ttu-id="336d2-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="336d2-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="336d2-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="336d2-117">Affected APIs</span></span>

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
