---
title: 網路設定設定
description: 瞭解設定 .NET Core 應用程式網路功能的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802768"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="ce104-103">網路功能的執行時間設定選項</span><span class="sxs-lookup"><span data-stu-id="ce104-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="ce104-104">HTTP/2 通訊協定</span><span class="sxs-lookup"><span data-stu-id="ce104-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="ce104-105">設定是否啟用 HTTP/2 通訊協定的支援。</span><span class="sxs-lookup"><span data-stu-id="ce104-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="ce104-106">預設：停用（`false`）。</span><span class="sxs-lookup"><span data-stu-id="ce104-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="ce104-107">在 .NET Core 3.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="ce104-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="ce104-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ce104-108">Setting name</span></span> | <span data-ttu-id="ce104-109">值</span><span class="sxs-lookup"><span data-stu-id="ce104-109">Values</span></span> |
| - | - |
| <span data-ttu-id="ce104-110">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ce104-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="ce104-111">`false`-已停用</span><span class="sxs-lookup"><span data-stu-id="ce104-111">`false` - disabled</span></span><br/><span data-ttu-id="ce104-112">已啟用 `true`</span><span class="sxs-lookup"><span data-stu-id="ce104-112">`true` - enabled</span></span> |
| <span data-ttu-id="ce104-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ce104-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="ce104-114">`0`-已停用</span><span class="sxs-lookup"><span data-stu-id="ce104-114">`0` - disabled</span></span><br/><span data-ttu-id="ce104-115">已啟用 `1`</span><span class="sxs-lookup"><span data-stu-id="ce104-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="ce104-116">通訊端 HTTP 處理常式</span><span class="sxs-lookup"><span data-stu-id="ce104-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="ce104-117">設定高階網路 Api （例如 <xref:System.Net.Http.HttpClient>）是否使用 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 或以[libcurl](https://curl.haxx.se/libcurl/)為基礎的 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 執行。</span><span class="sxs-lookup"><span data-stu-id="ce104-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="ce104-118">預設值：使用 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> （`true`）。</span><span class="sxs-lookup"><span data-stu-id="ce104-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="ce104-119">您可以藉由呼叫 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法，以程式設計方式設定這項設定。</span><span class="sxs-lookup"><span data-stu-id="ce104-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="ce104-120">設定名稱</span><span class="sxs-lookup"><span data-stu-id="ce104-120">Setting name</span></span> | <span data-ttu-id="ce104-121">值</span><span class="sxs-lookup"><span data-stu-id="ce104-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ce104-122">**.runtimeconfig.json json**</span><span class="sxs-lookup"><span data-stu-id="ce104-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="ce104-123">`true`-允許使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="ce104-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="ce104-124">`false`-允許使用 <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="ce104-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="ce104-125">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="ce104-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="ce104-126">`1`-允許使用 <xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="ce104-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="ce104-127">`0`-允許使用 <xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="ce104-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
