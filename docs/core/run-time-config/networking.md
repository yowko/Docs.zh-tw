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
# <a name="run-time-configuration-options-for-networking"></a>網路功能的執行時間設定選項

## <a name="http2-protocol"></a>HTTP/2 通訊協定

- 設定是否啟用 HTTP/2 通訊協定的支援。
- 預設：停用（`false`）。
- 在 .NET Core 3.0 中引進。

| | 設定名稱 | 值 |
| - | - |
| **.runtimeconfig.json json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-已停用<br/>已啟用 `true` |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-已停用<br/>已啟用 `1` |

## <a name="sockets-http-handler"></a>通訊端 HTTP 處理常式

- 設定高階網路 Api （例如 <xref:System.Net.Http.HttpClient>）是否使用 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 或以[libcurl](https://curl.haxx.se/libcurl/)為基礎的 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 執行。
- 預設值：使用 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> （`true`）。
- 您可以藉由呼叫 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法，以程式設計方式設定這項設定。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Net.Http.UseSocketsHttpHandler` | `true`-允許使用 <xref:System.Net.Http.SocketsHttpHandler><br/>`false`-允許使用 <xref:System.Net.Http.HttpClientHandler> |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`-允許使用 <xref:System.Net.Http.SocketsHttpHandler><br/>`0`-允許使用 <xref:System.Net.Http.HttpClientHandler> |
