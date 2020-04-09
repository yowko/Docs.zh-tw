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

- <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType>配置使用<xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>還是較舊的 HTTP 協定<xref:System.Net.Http.WinHttpHandler>堆疊(`CurlHandler`在 Windows 和 ,在 Linux 上在[libcurl](https://curl.haxx.se/libcurl/)之上實現的內部類別)。

  > [!NOTE]
  > 您可能使用的是進階網路 API,而不是直接實例<xref:System.Net.Http.HttpClientHandler>化類別 。 此設定還影響進階網路 API(包括<xref:System.Net.Http.HttpClient>和[HTTPClientFactory)](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118))使用哪些 HTTP 協定堆疊。

- 預設值:<xref:System.Net.Http.SocketsHttpHandler>`true`使用 ( 。

- 您可以通過調<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>用 方法以程式設計方式設定此設定。

| | 設定名稱 | 值 |
| - | - | - |
| **執行時設定.json** | `System.Net.Http.UseSocketsHttpHandler` | `true`- 使用<xref:System.Net.Http.SocketsHttpHandler><br/>`false`- 允許在<xref:System.Net.Http.WinHttpHandler>Windows 上使用, 或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/) |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`- 使用<xref:System.Net.Http.SocketsHttpHandler><br/>`0`- 允許在<xref:System.Net.Http.WinHttpHandler>Windows 上使用, 或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/) |

> [!NOTE]
> 從 .NET`System.Net.Http.UseSocketsHttpHandler`5 中開始,該設置不再可用。
