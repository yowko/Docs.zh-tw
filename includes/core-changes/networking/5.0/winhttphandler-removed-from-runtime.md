---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608471"
---
### <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="492cd-101">WinHttpHandler 已從 .NET 執行時間移除</span><span class="sxs-lookup"><span data-stu-id="492cd-101">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="492cd-102">`WinHttpHandler`類別已從*System.Net.Http.dll*元件中移除。</span><span class="sxs-lookup"><span data-stu-id="492cd-102">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="492cd-103">它現在僅適用于頻外 (OOB) [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。</span><span class="sxs-lookup"><span data-stu-id="492cd-103">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="492cd-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="492cd-104">Version introduced</span></span>

<span data-ttu-id="492cd-105">5.0</span><span class="sxs-lookup"><span data-stu-id="492cd-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="492cd-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="492cd-106">Change description</span></span>

<span data-ttu-id="492cd-107">在先前的 .NET 版本中， <xref:System.Net.Http.WinHttpHandler> 類別可作為核心 .net 程式庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="492cd-107">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="492cd-108">從 .NET 5.0 開始， <xref:System.Net.Http.WinHttpHandler> 類別僅可作為個別安裝的 [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。</span><span class="sxs-lookup"><span data-stu-id="492cd-108">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="492cd-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="492cd-109">Recommended action</span></span>

<span data-ttu-id="492cd-110">安裝 [WinHttpHandler NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。</span><span class="sxs-lookup"><span data-stu-id="492cd-110">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="492cd-111">或者，如果您不需要 WinHTTP 特定功能，請改用 <xref:System.Net.Http.SocketsHttpHandler> 。</span><span class="sxs-lookup"><span data-stu-id="492cd-111">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

#### <a name="category"></a><span data-ttu-id="492cd-112">類別</span><span class="sxs-lookup"><span data-stu-id="492cd-112">Category</span></span>

<span data-ttu-id="492cd-113">網路功能</span><span class="sxs-lookup"><span data-stu-id="492cd-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="492cd-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="492cd-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
