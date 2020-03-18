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
# <a name="run-time-configuration-options-for-networking"></a>網路運行時配置選項

## <a name="http2-protocol"></a>HTTP/2 協定

- 配置是否啟用了對 HTTP/2 協定的支援。
- 預設值： 已`false`禁用 （ 。
- 在 .NET 核心 3.0 仲介紹。

| | 設定名稱 | 值 |
| - | - |
| **運行時配置.json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`- 禁用<br/>`true`- 已啟用 |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`- 禁用<br/>`1`- 已啟用 |

## <a name="sockets-http-handler"></a>通訊端 HTTP 處理常式

- 配置高級<xref:System.Net.Http.HttpClient>網路 API（如、使用<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>還是基於<xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>[libcurl](https://curl.haxx.se/libcurl/)的實現）。
- 預設值：<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>使用`true`（ 。
- 您可以通過調用<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>方法以程式設計方式配置此設置。

| | 設定名稱 | 值 |
| - | - | - |
| **運行時配置.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- 能夠使用<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- 能夠使用<xref:System.Net.Http.HttpClientHandler> |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- 能夠使用<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- 能夠使用<xref:System.Net.Http.HttpClientHandler> |
