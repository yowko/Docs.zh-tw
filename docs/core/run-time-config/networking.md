---
title: 網路設定設定
description: 瞭解設定 .NET Core 應用程式網路功能的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bda608e83bb1b093d7d9b860de9607f6734720aa
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188298"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="61c68-103">網路功能的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="61c68-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="61c68-104">HTTP/2 通訊協定</span><span class="sxs-lookup"><span data-stu-id="61c68-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="61c68-105">設定是否啟用 HTTP/2 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="61c68-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="61c68-106">在 .NET Core 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="61c68-106">Introduced in .NET Core 3.0.</span></span>

- <span data-ttu-id="61c68-107">僅限 .NET Core 3.0：如果您省略此設定，則會停用 HTTP/2 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="61c68-107">.NET Core 3.0 only: If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="61c68-108">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="61c68-108">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="61c68-109">.NET Core 3.1 和 .NET 5 +：如果您省略此設定，則會啟用 HTTP/2 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="61c68-109">.NET Core 3.1 and .NET 5+: If you omit this setting, support for the HTTP/2 protocol is enabled.</span></span> <span data-ttu-id="61c68-110">這相當於將值設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="61c68-110">This is equivalent to setting the value to `true`.</span></span>

| | <span data-ttu-id="61c68-111">設定名稱</span><span class="sxs-lookup"><span data-stu-id="61c68-111">Setting name</span></span> | <span data-ttu-id="61c68-112">值</span><span class="sxs-lookup"><span data-stu-id="61c68-112">Values</span></span> |
| - | - | - |
| <span data-ttu-id="61c68-113">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="61c68-113">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="61c68-114">`false` -已停用</span><span class="sxs-lookup"><span data-stu-id="61c68-114">`false` - disabled</span></span><br/><span data-ttu-id="61c68-115">`true` -已啟用</span><span class="sxs-lookup"><span data-stu-id="61c68-115">`true` - enabled</span></span> |
| <span data-ttu-id="61c68-116">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="61c68-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="61c68-117">`0` -已停用</span><span class="sxs-lookup"><span data-stu-id="61c68-117">`0` - disabled</span></span><br/><span data-ttu-id="61c68-118">`1` -已啟用</span><span class="sxs-lookup"><span data-stu-id="61c68-118">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="61c68-119">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="61c68-119">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="61c68-120">設定是否 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 在 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Windows 上 (使用或較舊的 HTTP 通訊協定堆疊 <xref:System.Net.Http.WinHttpHandler> ，以及在 `CurlHandler` Linux) 上以 [libcurl](https://curl.haxx.se/libcurl/)上執行的內部類別。</span><span class="sxs-lookup"><span data-stu-id="61c68-120">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="61c68-121">您可以使用高階網路 Api，而不是直接具現化 <xref:System.Net.Http.HttpClientHandler> 類別。</span><span class="sxs-lookup"><span data-stu-id="61c68-121">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="61c68-122">這項設定也會影響高階網路 Api （包括和 HttpClientFactory）所使用的 HTTP 通訊協定堆疊 <xref:System.Net.Http.HttpClient> 。 [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118))</span><span class="sxs-lookup"><span data-stu-id="61c68-122">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="61c68-123">如果您省略此設定，則會 <xref:System.Net.Http.HttpClientHandler> 使用 <xref:System.Net.Http.SocketsHttpHandler> 。</span><span class="sxs-lookup"><span data-stu-id="61c68-123">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="61c68-124">這相當於將值設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="61c68-124">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="61c68-125">您可以藉由呼叫方法，以程式設計方式來設定此設定 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="61c68-125">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="61c68-126">設定名稱</span><span class="sxs-lookup"><span data-stu-id="61c68-126">Setting name</span></span> | <span data-ttu-id="61c68-127">值</span><span class="sxs-lookup"><span data-stu-id="61c68-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="61c68-128">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="61c68-128">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="61c68-129">`true` -可讓您使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="61c68-129">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="61c68-130">`false`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 上使用或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="61c68-130">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="61c68-131">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="61c68-131">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="61c68-132">`1` -可讓您使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="61c68-132">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="61c68-133">`0`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 上使用或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="61c68-133">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="61c68-134">從 .NET 5 開始， `System.Net.Http.UseSocketsHttpHandler` 就無法再使用此設定。</span><span class="sxs-lookup"><span data-stu-id="61c68-134">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>

## <a name="latin1-headers-net-core-31-only"></a><span data-ttu-id="61c68-135">採用 latin1-general 標頭 ( 僅限 .NET Core 3.1) </span><span class="sxs-lookup"><span data-stu-id="61c68-135">Latin1 headers (.NET Core 3.1 only)</span></span>

- <span data-ttu-id="61c68-136">此參數可放寬 HTTP 標頭驗證， <xref:System.Net.Http.SocketsHttpHandler> 以便在標頭中傳送 ISO-8859-1 (拉丁字母) 編碼的字元。</span><span class="sxs-lookup"><span data-stu-id="61c68-136">This switch allows relaxing the HTTP header validation, enabling <xref:System.Net.Http.SocketsHttpHandler> to send ISO-8859-1 (Latin-1) encoded characters in headers.</span></span>

- <span data-ttu-id="61c68-137">如果您省略這個設定，嘗試傳送非 ASCII 字元將會導致 <xref:System.Net.Http.HttpRequestException> 。</span><span class="sxs-lookup"><span data-stu-id="61c68-137">If you omit this setting, an attempt to send a non-ASCII character will result in <xref:System.Net.Http.HttpRequestException>.</span></span> <span data-ttu-id="61c68-138">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="61c68-138">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="61c68-139">設定名稱</span><span class="sxs-lookup"><span data-stu-id="61c68-139">Setting name</span></span> | <span data-ttu-id="61c68-140">值</span><span class="sxs-lookup"><span data-stu-id="61c68-140">Values</span></span> |
| - | - | - |
| <span data-ttu-id="61c68-141">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="61c68-141">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | <span data-ttu-id="61c68-142">`false` -已停用</span><span class="sxs-lookup"><span data-stu-id="61c68-142">`false` - disabled</span></span><br/><span data-ttu-id="61c68-143">`true` -已啟用</span><span class="sxs-lookup"><span data-stu-id="61c68-143">`true` - enabled</span></span> |
| <span data-ttu-id="61c68-144">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="61c68-144">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | <span data-ttu-id="61c68-145">`0` -已停用</span><span class="sxs-lookup"><span data-stu-id="61c68-145">`0` - disabled</span></span><br/><span data-ttu-id="61c68-146">`1` -已啟用</span><span class="sxs-lookup"><span data-stu-id="61c68-146">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="61c68-147">此選項僅適用于 .NET Core 3.1 （自版本3.1.9），不適用於舊版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="61c68-147">This option is only available in .NET Core 3.1 since version 3.1.9, and not in previous or later versions.</span></span> <span data-ttu-id="61c68-148">在 .NET 5 中，我們建議使用 <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> 。</span><span class="sxs-lookup"><span data-stu-id="61c68-148">In .NET 5 we recommend using <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector>.</span></span>
