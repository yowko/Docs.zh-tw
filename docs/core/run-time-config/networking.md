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
# <a name="run-time-configuration-options-for-networking"></a>網路執行時設定選項

## <a name="http2-protocol"></a>HTTP/2 協定

- 配置是否啟用了對 HTTP/2 協定的支援。
- 預設值:`false`已關閉 ( 。
- 在 .NET 核心 3.0 中介紹。

| | 設定名稱 | 值 |
| - | - | - |
| **執行時設定.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- 停用<br/>`true`- 已開啟 |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- 停用<br/>`1`- 已開啟 |

## <a name="usesocketshttphandler"></a>使用 SocketTTHttpHandler

- 設定進<xref:System.Net.Http.HttpClient>階網路 API(如<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>、使用<xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>還是基於[libcurl](https://curl.haxx.se/libcurl/)的實現)。
- 預設值:<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>`true`使用 ( 。
- 您可以通過調<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>用 方法以程式設計方式設定此設定。

| | 設定名稱 | 值 |
| - | - | - |
| **執行時設定.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- 使用<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- 使用<xref:System.Net.Http.HttpClientHandler> |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- 使用<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- 使用<xref:System.Net.Http.HttpClientHandler> |

> [!NOTE]
> 從 .NET`System.Net.Http.UseSocketsHttpHandler`5 中開始,該設置不再可用。
