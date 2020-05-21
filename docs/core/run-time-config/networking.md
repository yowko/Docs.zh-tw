---
title: 網路設定設定
description: 瞭解設定 .NET Core 應用程式網路功能的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6b5e03b127f95911b712b66c0be8a4f5a2929fc2
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761937"
---
# <a name="run-time-configuration-options-for-networking"></a>網路功能的執行時間設定選項

## <a name="http2-protocol"></a>HTTP/2 通訊協定

- 設定是否啟用 HTTP/2 通訊協定的支援。

- 如果您省略此設定，則會停用 HTTP/2 通訊協定的支援。 這相當於將值設定為 `false` 。

- 在 .NET Core 3.0 中引進。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false`-已停用<br/>`true`-已啟用 |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0`-已停用<br/>`1`-已啟用 |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- 設定是否 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 使用 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 或較舊的 HTTP 通訊協定堆疊（ <xref:System.Net.Http.WinHttpHandler> 在 Windows 上，以及在 `CurlHandler` Linux 上以[libcurl](https://curl.haxx.se/libcurl/)為基礎執行的內部類別）。

  > [!NOTE]
  > 您可能使用高階網路 Api，而不是直接具現化 <xref:System.Net.Http.HttpClientHandler> 類別。 這項設定也會影響高階網路 Api （包括和 HttpClientFactory）所使用的 HTTP 通訊協定堆疊 <xref:System.Net.Http.HttpClient> 。 [HttpClientFactory](https://docs.microsoft.com/previous-versions/aspnet/hh995280(v%3dvs.118))

- 如果您省略此設定，會 <xref:System.Net.Http.HttpClientHandler> 使用 <xref:System.Net.Http.SocketsHttpHandler> 。 這相當於將值設定為 `true` 。

- 您可以藉由呼叫方法，以程式設計方式設定這項設定 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 。

| | 設定名稱 | 值 |
| - | - | - |
| **.runtimeconfig.json json** | `System.Net.Http.UseSocketsHttpHandler` | `true`-允許使用<xref:System.Net.Http.SocketsHttpHandler><br/>`false`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 或 Linux 上的[libcurl](https://curl.haxx.se/libcurl/)上使用 |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1`-允許使用<xref:System.Net.Http.SocketsHttpHandler><br/>`0`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 或 Linux 上的[libcurl](https://curl.haxx.se/libcurl/)上使用 |

> [!NOTE]
> 從 .NET 5 開始， `System.Net.Http.UseSocketsHttpHandler` 設定就無法再使用。
