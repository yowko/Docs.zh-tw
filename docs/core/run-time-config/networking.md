---
title: 網路設定設定
description: 瞭解為 .NET Core 應用配置網路的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: f5ea47f0444a911dc2347a66817cabf585fd8e70
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635417"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="0c42c-103">網路執行時設定選項</span><span class="sxs-lookup"><span data-stu-id="0c42c-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="0c42c-104">HTTP/2 協定</span><span class="sxs-lookup"><span data-stu-id="0c42c-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="0c42c-105">配置是否啟用了對 HTTP/2 協定的支援。</span><span class="sxs-lookup"><span data-stu-id="0c42c-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="0c42c-106">預設值:`false`已關閉 ( 。</span><span class="sxs-lookup"><span data-stu-id="0c42c-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="0c42c-107">在 .NET 核心 3.0 中介紹。</span><span class="sxs-lookup"><span data-stu-id="0c42c-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="0c42c-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="0c42c-108">Setting name</span></span> | <span data-ttu-id="0c42c-109">值</span><span class="sxs-lookup"><span data-stu-id="0c42c-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0c42c-110">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="0c42c-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="0c42c-111">`false`- 停用</span><span class="sxs-lookup"><span data-stu-id="0c42c-111">`false` - disabled</span></span><br/><span data-ttu-id="0c42c-112">`true`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="0c42c-112">`true` - enabled</span></span> |
| <span data-ttu-id="0c42c-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="0c42c-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="0c42c-114">`0`- 停用</span><span class="sxs-lookup"><span data-stu-id="0c42c-114">`0` - disabled</span></span><br/><span data-ttu-id="0c42c-115">`1`- 已開啟</span><span class="sxs-lookup"><span data-stu-id="0c42c-115">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="0c42c-116">使用 SocketTTHttpHandler</span><span class="sxs-lookup"><span data-stu-id="0c42c-116">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="0c42c-117">設定進<xref:System.Net.Http.HttpClient>階網路 API(如<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>、使用<xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>還是基於[libcurl](https://curl.haxx.se/libcurl/)的實現)。</span><span class="sxs-lookup"><span data-stu-id="0c42c-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="0c42c-118">預設值:<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>`true`使用 ( 。</span><span class="sxs-lookup"><span data-stu-id="0c42c-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="0c42c-119">您可以通過調<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>用 方法以程式設計方式設定此設定。</span><span class="sxs-lookup"><span data-stu-id="0c42c-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="0c42c-120">設定名稱</span><span class="sxs-lookup"><span data-stu-id="0c42c-120">Setting name</span></span> | <span data-ttu-id="0c42c-121">值</span><span class="sxs-lookup"><span data-stu-id="0c42c-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0c42c-122">**執行時設定.json**</span><span class="sxs-lookup"><span data-stu-id="0c42c-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="0c42c-123">`true`- 使用<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="0c42c-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="0c42c-124">`false`- 使用<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="0c42c-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="0c42c-125">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="0c42c-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="0c42c-126">`1`- 使用<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="0c42c-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="0c42c-127">`0`- 使用<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="0c42c-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |

> [!NOTE]
> <span data-ttu-id="0c42c-128">從 .NET`System.Net.Http.UseSocketsHttpHandler`5 中開始,該設置不再可用。</span><span class="sxs-lookup"><span data-stu-id="0c42c-128">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>
