---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032348"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="3eddf-101">裝載：已從 Windows 裝載套件組合移除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="3eddf-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="3eddf-102">從 ASP.NET Core 3.0 開始，Windows 裝載套件組合將不會包含 AspNetCoreModule (ANCM) V1。</span><span class="sxs-lookup"><span data-stu-id="3eddf-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="3eddf-103">ANCM V2 可回溯相容于 ANCM OutOfProcess，並建議搭配 ASP.NET Core 3.0 應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="3eddf-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="3eddf-104">如需討論，請參閱 [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095)。</span><span class="sxs-lookup"><span data-stu-id="3eddf-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3eddf-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3eddf-105">Version introduced</span></span>

<span data-ttu-id="3eddf-106">3.0</span><span class="sxs-lookup"><span data-stu-id="3eddf-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3eddf-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="3eddf-107">Old behavior</span></span>

<span data-ttu-id="3eddf-108">ANCM V1 包含在 Windows 裝載套件組合中。</span><span class="sxs-lookup"><span data-stu-id="3eddf-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3eddf-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="3eddf-109">New behavior</span></span>

<span data-ttu-id="3eddf-110">ANCM V1 未包含在 Windows 裝載套件組合中。</span><span class="sxs-lookup"><span data-stu-id="3eddf-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3eddf-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="3eddf-111">Reason for change</span></span>

<span data-ttu-id="3eddf-112">ANCM V2 可回溯相容于 ANCM OutOfProcess，並建議搭配 ASP.NET Core 3.0 應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="3eddf-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3eddf-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3eddf-113">Recommended action</span></span>

<span data-ttu-id="3eddf-114">使用 ANCM V2 搭配 ASP.NET Core 3.0 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3eddf-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="3eddf-115">如果需要 ANCM V1，可以使用 ASP.NET Core 2.1 或 2.2 Windows 裝載套件組合來安裝。</span><span class="sxs-lookup"><span data-stu-id="3eddf-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="3eddf-116">這種變更將會中斷下列 ASP.NET Core 3.0 應用程式：</span><span class="sxs-lookup"><span data-stu-id="3eddf-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="3eddf-117">明確選擇使用 ANCM V1 搭配 `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` 。</span><span class="sxs-lookup"><span data-stu-id="3eddf-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="3eddf-118">使用自訂的 *web.config* 檔案 `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` 。</span><span class="sxs-lookup"><span data-stu-id="3eddf-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="3eddf-119">類別</span><span class="sxs-lookup"><span data-stu-id="3eddf-119">Category</span></span>

<span data-ttu-id="3eddf-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3eddf-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3eddf-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3eddf-121">Affected APIs</span></span>

<span data-ttu-id="3eddf-122">None</span><span class="sxs-lookup"><span data-stu-id="3eddf-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
