---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393976"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="c568c-101">標識：SignInAsync 為未身份驗證的標識引發異常</span><span class="sxs-lookup"><span data-stu-id="c568c-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="c568c-102">預設情況下，`SignInAsync`為 主體/標識（其中`IsAuthenticated`為`false`）引發異常。</span><span class="sxs-lookup"><span data-stu-id="c568c-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c568c-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="c568c-103">Version introduced</span></span>

<span data-ttu-id="c568c-104">3.0</span><span class="sxs-lookup"><span data-stu-id="c568c-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c568c-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="c568c-105">Old behavior</span></span>

<span data-ttu-id="c568c-106">`SignInAsync`接受任何主體/身份，包括`IsAuthenticated`中`false`的身份。</span><span class="sxs-lookup"><span data-stu-id="c568c-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c568c-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="c568c-107">New behavior</span></span>

<span data-ttu-id="c568c-108">預設情況下，`SignInAsync`為 主體/標識（其中`IsAuthenticated`為`false`）引發異常。</span><span class="sxs-lookup"><span data-stu-id="c568c-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="c568c-109">有一個新的標誌來禁止此行為，但預設行為已更改。</span><span class="sxs-lookup"><span data-stu-id="c568c-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c568c-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="c568c-110">Reason for change</span></span>

<span data-ttu-id="c568c-111">舊行為存在問題，因為預設情況下，這些主體被`[Authorize]` / `RequireAuthenticatedUser()`拒絕。</span><span class="sxs-lookup"><span data-stu-id="c568c-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c568c-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c568c-112">Recommended action</span></span>

<span data-ttu-id="c568c-113">在ASP.NET酷睿 3.0 預覽 6`RequireAuthenticatedSignIn`中`AuthenticationOptions`，預設情況下有`true`一個標誌。</span><span class="sxs-lookup"><span data-stu-id="c568c-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="c568c-114">將此標誌設置為`false`還原舊行為。</span><span class="sxs-lookup"><span data-stu-id="c568c-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="c568c-115">類別</span><span class="sxs-lookup"><span data-stu-id="c568c-115">Category</span></span>

<span data-ttu-id="c568c-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c568c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c568c-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c568c-117">Affected APIs</span></span>

<span data-ttu-id="c568c-118">None</span><span class="sxs-lookup"><span data-stu-id="c568c-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
