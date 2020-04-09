---
title: 網路設定設定
description: 瞭解為 .NET Core 應用配置網路的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 8d02087ad7260cc78c096090bf3b06a716d34678
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989099"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="6c94e-103">網路執行時設定選項</span><span class="sxs-lookup"><span data-stu-id="6c94e-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="6c94e-104">HTTP/2 協定</span><span class="sxs-lookup"><span data-stu-id="6c94e-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="6c94e-105">配置是否啟用了對 HTTP/2 協定的支援。</span><span class="sxs-lookup"><span data-stu-id="6c94e-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="6c94e-106">預設值:`false`已關閉 ( 。</span><span class="sxs-lookup"><span data-stu-id="6c94e-106">Default: Disabled (`false`).</span></span>

- <span data-ttu-id="6c94e-107">在 .NET 核心 3.0 中介紹。</span><span class="sxs-lookup"><span data-stu-id="6c94e-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="6c94e-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="6c94e-108">Setting name</span></span> | <span data-ttu-id="6c94e-109">值</span><span class="sxs-lookup"><span data-stu-id="6c94e-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6c94e-110">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="6c94e-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="6c94e-111">`false`- 停用</span><span class="sxs-lookup"><span data-stu-id="6c94e-111">`false` - disabled</span></span><br/><span data-ttu-id="6c94e-112">`true`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="6c94e-112">`true` - enabled</span></span> |
| <span data-ttu-id="6c94e-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="6c94e-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="6c94e-114">`0`- 停用</span><span class="sxs-lookup"><span data-stu-id="6c94e-114">`0` - disabled</span></span><br/><span data-ttu-id="6c94e-115">`1`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="6c94e-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="6c94e-116">使用 SocketTTHttpHandler</span><span class="sxs-lookup"><span data-stu-id="6c94e-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="6c94e-117"><xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>配置使用<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>還是較舊的 HTTP 協定<xref:System.Net.Http.WinHttpHandler>堆疊(`CurlHandler`在 Windows 和 ,在 Linux 上在[libcurl](https://curl.haxx.se/libcurl/)之上實現的內部類別)。</span><span class="sxs-lookup"><span data-stu-id="6c94e-117">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="6c94e-118">您可能使用的是進階網路 API,而不是直接實例<xref:System.Net.Http.HttpClientHandler>化類別 。</span><span class="sxs-lookup"><span data-stu-id="6c94e-118">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="6c94e-119">此設定還影響進階網路 API(包括<xref:System.Net.Http.HttpClient>和[HTTPClientFactory)](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118))使用哪些 HTTP 協定堆疊。</span><span class="sxs-lookup"><span data-stu-id="6c94e-119">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118)).</span></span>

- <span data-ttu-id="6c94e-120">預設值:<xref:System.Net.Http.SocketsHttpHandler>`true`使用 ( 。</span><span class="sxs-lookup"><span data-stu-id="6c94e-120">Default: Use <xref:System.Net.Http.SocketsHttpHandler> (`true`).</span></span>

- <span data-ttu-id="6c94e-121">您可以通過調<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>用 方法以程式設計方式設定此設定。</span><span class="sxs-lookup"><span data-stu-id="6c94e-121">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="6c94e-122">設定名稱</span><span class="sxs-lookup"><span data-stu-id="6c94e-122">Setting name</span></span> | <span data-ttu-id="6c94e-123">值</span><span class="sxs-lookup"><span data-stu-id="6c94e-123">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6c94e-124">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="6c94e-124">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="6c94e-125">`true`- 使用<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="6c94e-125">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="6c94e-126">`false`- 允許在<xref:System.Net.Http.WinHttpHandler>Windows 上使用, 或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="6c94e-126">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="6c94e-127">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="6c94e-127">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="6c94e-128">`1`- 使用<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="6c94e-128">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="6c94e-129">`0`- 允許在<xref:System.Net.Http.WinHttpHandler>Windows 上使用, 或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/)</span><span class="sxs-lookup"><span data-stu-id="6c94e-129">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="6c94e-130">從 .NET`System.Net.Http.UseSocketsHttpHandler`5 中開始,該設置不再可用。</span><span class="sxs-lookup"><span data-stu-id="6c94e-130">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
