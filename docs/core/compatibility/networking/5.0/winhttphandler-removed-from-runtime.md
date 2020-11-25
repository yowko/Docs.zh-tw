---
title: 重大變更： WinHttpHandler 已從 .NET 執行時間移除
description: 瞭解 .NET 5.0 中從 .NET 執行時間移除 WinHttpHandler 的重大變更。
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760618"
---
# <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="ae1bd-103">WinHttpHandler 已從 .NET 執行時間移除</span><span class="sxs-lookup"><span data-stu-id="ae1bd-103">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="ae1bd-104">`WinHttpHandler`類別已從 *System.Net.Http.dll* 元件中移除。</span><span class="sxs-lookup"><span data-stu-id="ae1bd-104">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="ae1bd-105">它現在僅適用于頻外 (OOB) [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。</span><span class="sxs-lookup"><span data-stu-id="ae1bd-105">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ae1bd-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ae1bd-106">Version introduced</span></span>

<span data-ttu-id="ae1bd-107">5.0</span><span class="sxs-lookup"><span data-stu-id="ae1bd-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="ae1bd-108">變更描述</span><span class="sxs-lookup"><span data-stu-id="ae1bd-108">Change description</span></span>

<span data-ttu-id="ae1bd-109">在先前的 .NET 版本中， <xref:System.Net.Http.WinHttpHandler> 類別可作為核心 .net 程式庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="ae1bd-109">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="ae1bd-110">從 .NET 5.0 開始， <xref:System.Net.Http.WinHttpHandler> 類別僅可作為個別安裝的 [NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。</span><span class="sxs-lookup"><span data-stu-id="ae1bd-110">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ae1bd-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ae1bd-111">Recommended action</span></span>

<span data-ttu-id="ae1bd-112">安裝 [WinHttpHandler NuGet 套件](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。</span><span class="sxs-lookup"><span data-stu-id="ae1bd-112">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="ae1bd-113">或者，如果您不需要 WinHTTP 特定功能，請改用 <xref:System.Net.Http.SocketsHttpHandler> 。</span><span class="sxs-lookup"><span data-stu-id="ae1bd-113">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ae1bd-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ae1bd-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
