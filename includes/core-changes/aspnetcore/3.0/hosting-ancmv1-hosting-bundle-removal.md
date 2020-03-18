---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901580"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="c158d-101">託管：從 Windows 託管捆綁包中刪除的 AspNetCore 模組 V1</span><span class="sxs-lookup"><span data-stu-id="c158d-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="c158d-102">從 ASP.NET 酷睿 3.0 開始，Windows 託管捆綁包將不包含 AspNetCore 模組 （ANCM） V1。</span><span class="sxs-lookup"><span data-stu-id="c158d-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="c158d-103">ANCM V2 向後相容 ANCM 出進程，建議與 ASP.NET 酷睿 3.0 應用一起使用。</span><span class="sxs-lookup"><span data-stu-id="c158d-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="c158d-104">有關討論，請參閱[dotnet/aspnetcore_7095](https://github.com/dotnet/aspnetcore/issues/7095)。</span><span class="sxs-lookup"><span data-stu-id="c158d-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c158d-105">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="c158d-105">Version introduced</span></span>

<span data-ttu-id="c158d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="c158d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c158d-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="c158d-107">Old behavior</span></span>

<span data-ttu-id="c158d-108">ANCM V1 包含在 Windows 託管捆綁包中。</span><span class="sxs-lookup"><span data-stu-id="c158d-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c158d-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="c158d-109">New behavior</span></span>

<span data-ttu-id="c158d-110">ANCM V1 不包括在 Windows 託管捆綁包中。</span><span class="sxs-lookup"><span data-stu-id="c158d-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c158d-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="c158d-111">Reason for change</span></span>

<span data-ttu-id="c158d-112">ANCM V2 向後相容 ANCM 出進程，建議與 ASP.NET 酷睿 3.0 應用一起使用。</span><span class="sxs-lookup"><span data-stu-id="c158d-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c158d-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c158d-113">Recommended action</span></span>

<span data-ttu-id="c158d-114">將 ANCM V2 與 ASP.NET核心 3.0 應用一起使用。</span><span class="sxs-lookup"><span data-stu-id="c158d-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="c158d-115">如果需要 ANCM V1，可以使用ASP.NET酷睿 2.1 或 2.2 Windows 託管捆綁包進行安裝。</span><span class="sxs-lookup"><span data-stu-id="c158d-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="c158d-116">此更改將破壞 ASP.NET Core 3.0 應用：</span><span class="sxs-lookup"><span data-stu-id="c158d-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="c158d-117">明確選擇將 ANCM V1`<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`與 。</span><span class="sxs-lookup"><span data-stu-id="c158d-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="c158d-118">使用 具有 自訂*Web.config*檔`<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`。</span><span class="sxs-lookup"><span data-stu-id="c158d-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="c158d-119">類別</span><span class="sxs-lookup"><span data-stu-id="c158d-119">Category</span></span>

<span data-ttu-id="c158d-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c158d-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c158d-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c158d-121">Affected APIs</span></span>

<span data-ttu-id="c158d-122">None</span><span class="sxs-lookup"><span data-stu-id="c158d-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
