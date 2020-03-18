---
title: 網路設定設置
description: 瞭解為 .NET Core 應用配置網路的運行時設置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 622c4afbd36d3d9004edbd9219145fa9e5d326ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802768"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="60054-103">網路運行時配置選項</span><span class="sxs-lookup"><span data-stu-id="60054-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="60054-104">HTTP/2 協定</span><span class="sxs-lookup"><span data-stu-id="60054-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="60054-105">配置是否啟用了對 HTTP/2 協定的支援。</span><span class="sxs-lookup"><span data-stu-id="60054-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>
- <span data-ttu-id="60054-106">預設值： 已`false`禁用 （ 。</span><span class="sxs-lookup"><span data-stu-id="60054-106">Default: Disabled (`false`).</span></span>
- <span data-ttu-id="60054-107">在 .NET 核心 3.0 仲介紹。</span><span class="sxs-lookup"><span data-stu-id="60054-107">Introduced in .NET Core 3.0.</span></span>

| | <span data-ttu-id="60054-108">設定名稱</span><span class="sxs-lookup"><span data-stu-id="60054-108">Setting name</span></span> | <span data-ttu-id="60054-109">值</span><span class="sxs-lookup"><span data-stu-id="60054-109">Values</span></span> |
| - | - |
| <span data-ttu-id="60054-110">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="60054-110">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="60054-111">`false`- 禁用</span><span class="sxs-lookup"><span data-stu-id="60054-111">`false` - disabled</span></span><br/><span data-ttu-id="60054-112">`true`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="60054-112">`true` - enabled</span></span> |
| <span data-ttu-id="60054-113">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="60054-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="60054-114">`0`- 禁用</span><span class="sxs-lookup"><span data-stu-id="60054-114">`0` - disabled</span></span><br/><span data-ttu-id="60054-115">`1`- 已啟用</span><span class="sxs-lookup"><span data-stu-id="60054-115">`1` - enabled</span></span> |

## <a name="sockets-http-handler"></a><span data-ttu-id="60054-116">通訊端 HTTP 處理常式</span><span class="sxs-lookup"><span data-stu-id="60054-116">Sockets HTTP handler</span></span>

- <span data-ttu-id="60054-117">配置高級<xref:System.Net.Http.HttpClient>網路 API（如、使用<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>還是基於<xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>[libcurl](https://curl.haxx.se/libcurl/)的實現）。</span><span class="sxs-lookup"><span data-stu-id="60054-117">Configures whether high-level networking APIs, such as <xref:System.Net.Http.HttpClient>, use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or the implementation of <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> that's based on [libcurl](https://curl.haxx.se/libcurl/).</span></span>
- <span data-ttu-id="60054-118">預設值：<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>使用`true`（ 。</span><span class="sxs-lookup"><span data-stu-id="60054-118">Default: Use <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> (`true`).</span></span>
- <span data-ttu-id="60054-119">您可以通過調用<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>方法以程式設計方式配置此設置。</span><span class="sxs-lookup"><span data-stu-id="60054-119">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="60054-120">設定名稱</span><span class="sxs-lookup"><span data-stu-id="60054-120">Setting name</span></span> | <span data-ttu-id="60054-121">值</span><span class="sxs-lookup"><span data-stu-id="60054-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="60054-122">**運行時配置.json**</span><span class="sxs-lookup"><span data-stu-id="60054-122">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="60054-123">`true`- 能夠使用<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="60054-123">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="60054-124">`false`- 能夠使用<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="60054-124">`false` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
| <span data-ttu-id="60054-125">**環境變數**</span><span class="sxs-lookup"><span data-stu-id="60054-125">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="60054-126">`1`- 能夠使用<xref:System.Net.Http.SocketsHttpHandler></span><span class="sxs-lookup"><span data-stu-id="60054-126">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="60054-127">`0`- 能夠使用<xref:System.Net.Http.HttpClientHandler></span><span class="sxs-lookup"><span data-stu-id="60054-127">`0` - enables the use of <xref:System.Net.Http.HttpClientHandler></span></span> |
