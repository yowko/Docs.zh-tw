---
title: 網路設定設定
description: 瞭解設定 .NET Core 應用程式網路功能的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: d43b68206cc82f4a41df02bd5998702b4f5d0590
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538129"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="8d260-103">網路功能的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="8d260-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="8d260-104">HTTP/2 通訊協定</span><span class="sxs-lookup"><span data-stu-id="8d260-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="8d260-105">設定是否啟用 HTTP/2 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="8d260-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="8d260-106">如果您省略此設定，則會停用 HTTP/2 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="8d260-106">If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="8d260-107">這相當於將值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="8d260-107">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="8d260-108">在 .NET Core 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="8d260-108">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="8d260-109">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8d260-109">Setting name</span></span> | <span data-ttu-id="8d260-110">值</span><span class="sxs-lookup"><span data-stu-id="8d260-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="8d260-111">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="8d260-111">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="8d260-112">`false` -已停用</span><span class="sxs-lookup"><span data-stu-id="8d260-112">`false` - disabled</span></span><br/><span data-ttu-id="8d260-113">`true` -已啟用</span><span class="sxs-lookup"><span data-stu-id="8d260-113">`true` - enabled</span></span> |
| <span data-ttu-id="8d260-114">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8d260-114">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="8d260-115">`0` -已停用</span><span class="sxs-lookup"><span data-stu-id="8d260-115">`0` - disabled</span></span><br/><span data-ttu-id="8d260-116">`1` -已啟用</span><span class="sxs-lookup"><span data-stu-id="8d260-116">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="8d260-117">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="8d260-117">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="8d260-118">設定是否 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 在 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Windows 上 (使用或較舊的 HTTP 通訊協定堆疊 <xref:System.Net.Http.WinHttpHandler> ，以及在 `CurlHandler` Linux) 上以 [libcurl](https://curl.haxx.se/libcurl/)上執行的內部類別。</span><span class="sxs-lookup"><span data-stu-id="8d260-118">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="8d260-119">您可以使用高階網路 Api，而不是直接具現化 <xref:System.Net.Http.HttpClientHandler> 類別。</span><span class="sxs-lookup"><span data-stu-id="8d260-119">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="8d260-120">這項設定也會影響高階網路 Api （包括和 HttpClientFactory）所使用的 HTTP 通訊協定堆疊 <xref:System.Net.Http.HttpClient> 。 [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118))</span><span class="sxs-lookup"><span data-stu-id="8d260-120">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="8d260-121">如果您省略此設定，則會 <xref:System.Net.Http.HttpClientHandler> 使用 <xref:System.Net.Http.SocketsHttpHandler> 。</span><span class="sxs-lookup"><span data-stu-id="8d260-121">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="8d260-122">這相當於將值設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="8d260-122">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="8d260-123">您可以藉由呼叫方法，以程式設計方式來設定此設定 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="8d260-123">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="8d260-124">設定名稱</span><span class="sxs-lookup"><span data-stu-id="8d260-124">Setting name</span></span> | <span data-ttu-id="8d260-125">值</span><span class="sxs-lookup"><span data-stu-id="8d260-125">Values</span></span> |
| - | - | - |
| <span data-ttu-id="8d260-126">**runtimeconfig.js開啟**</span><span class="sxs-lookup"><span data-stu-id="8d260-126">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="8d260-127">`true` -可讓您使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="8d260-127">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="8d260-128">`false`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 上使用或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="8d260-128">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="8d260-129">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="8d260-129">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="8d260-130">`1` -可讓您使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="8d260-130">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="8d260-131">`0`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 上使用或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="8d260-131">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="8d260-132">從 .NET 5 開始， `System.Net.Http.UseSocketsHttpHandler` 就無法再使用此設定。</span><span class="sxs-lookup"><span data-stu-id="8d260-132">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
