---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393992"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="01a94-101">裝載：已從 Windows 裝載套件組合中移除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="01a94-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="01a94-102">從 ASP.NET Core 3.0 開始，Windows 裝載套件組合將不會包含 AspNetCoreModule （ANCM） V1。</span><span class="sxs-lookup"><span data-stu-id="01a94-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="01a94-103">ANCM V2 與 ANCM OutOfProcess 回溯相容，建議用於 ASP.NET Core 3.0 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01a94-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="01a94-104">如需討論，請參閱[aspnet/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095)。</span><span class="sxs-lookup"><span data-stu-id="01a94-104">For discussion, see [aspnet/AspNetCore#7095](https://github.com/aspnet/AspNetCore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01a94-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="01a94-105">Version introduced</span></span>

<span data-ttu-id="01a94-106">3.0</span><span class="sxs-lookup"><span data-stu-id="01a94-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="01a94-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="01a94-107">Old behavior</span></span>

<span data-ttu-id="01a94-108">ANCM V1 包含在 Windows 裝載套件組合中。</span><span class="sxs-lookup"><span data-stu-id="01a94-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="01a94-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="01a94-109">New behavior</span></span>

<span data-ttu-id="01a94-110">ANCM V1 並未包含在 Windows 裝載套件組合中。</span><span class="sxs-lookup"><span data-stu-id="01a94-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="01a94-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="01a94-111">Reason for change</span></span>

<span data-ttu-id="01a94-112">ANCM V2 與 ANCM OutOfProcess 回溯相容，建議用於 ASP.NET Core 3.0 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01a94-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01a94-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="01a94-113">Recommended action</span></span>

<span data-ttu-id="01a94-114">使用 ANCM V2 搭配 ASP.NET Core 3.0 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01a94-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="01a94-115">如果需要 ANCM V1，可以使用 ASP.NET Core 2.1 或 2.2 Windows 裝載套件組合來安裝。</span><span class="sxs-lookup"><span data-stu-id="01a94-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="01a94-116">這種變更會中斷 ASP.NET Core 3.0 應用程式：</span><span class="sxs-lookup"><span data-stu-id="01a94-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="01a94-117">已使用 ANCM V1 與 `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` 明確加入宣告。</span><span class="sxs-lookup"><span data-stu-id="01a94-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="01a94-118">具有 `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` 的自訂*web.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="01a94-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="01a94-119">分類</span><span class="sxs-lookup"><span data-stu-id="01a94-119">Category</span></span>

<span data-ttu-id="01a94-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="01a94-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01a94-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="01a94-121">Affected APIs</span></span>

<span data-ttu-id="01a94-122">無</span><span class="sxs-lookup"><span data-stu-id="01a94-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
