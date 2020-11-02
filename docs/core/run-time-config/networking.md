---
title: 網路設定設定
description: 瞭解設定 .NET Core 應用程式網路功能的執行時間設定。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bda608e83bb1b093d7d9b860de9607f6734720aa
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188298"
---
# <a name="run-time-configuration-options-for-networking"></a>網路功能的執行時間設定選項

## <a name="http2-protocol"></a>HTTP/2 通訊協定

- 設定是否啟用 HTTP/2 通訊協定的支援。

- 在 .NET Core 3.0 中引進。

- 僅限 .NET Core 3.0：如果您省略此設定，則會停用 HTTP/2 通訊協定的支援。 這相當於將值設定為 `false` 。

- .NET Core 3.1 和 .NET 5 +：如果您省略此設定，則會啟用 HTTP/2 通訊協定的支援。 這相當於將值設定為 `true` 。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `System.Net.Http.SocketsHttpHandler.Http2Support` | `false` -已停用<br/>`true` -已啟用 |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | `0` -已停用<br/>`1` -已啟用 |

## <a name="usesocketshttphandler"></a>UseSocketsHttpHandler

- 設定是否 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> 在 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> Windows 上 (使用或較舊的 HTTP 通訊協定堆疊 <xref:System.Net.Http.WinHttpHandler> ，以及在 `CurlHandler` Linux) 上以 [libcurl](https://curl.haxx.se/libcurl/)上執行的內部類別。

  > [!NOTE]
  > 您可以使用高階網路 Api，而不是直接具現化 <xref:System.Net.Http.HttpClientHandler> 類別。 這項設定也會影響高階網路 Api （包括和 HttpClientFactory）所使用的 HTTP 通訊協定堆疊 <xref:System.Net.Http.HttpClient> 。 [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118))

- 如果您省略此設定，則會 <xref:System.Net.Http.HttpClientHandler> 使用 <xref:System.Net.Http.SocketsHttpHandler> 。 這相當於將值設定為 `true` 。

- 您可以藉由呼叫方法，以程式設計方式來設定此設定 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `System.Net.Http.UseSocketsHttpHandler` | `true` -可讓您使用 <xref:System.Net.Http.SocketsHttpHandler><br/>`false`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 上使用或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/) |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | `1` -可讓您使用 <xref:System.Net.Http.SocketsHttpHandler><br/>`0`-可讓您在 <xref:System.Net.Http.WinHttpHandler> Windows 上使用或在 Linux 上使用[libcurl](https://curl.haxx.se/libcurl/) |

> [!NOTE]
> 從 .NET 5 開始， `System.Net.Http.UseSocketsHttpHandler` 就無法再使用此設定。

## <a name="latin1-headers-net-core-31-only"></a>採用 latin1-general 標頭 ( 僅限 .NET Core 3.1) 

- 此參數可放寬 HTTP 標頭驗證， <xref:System.Net.Http.SocketsHttpHandler> 以便在標頭中傳送 ISO-8859-1 (拉丁字母) 編碼的字元。

- 如果您省略這個設定，嘗試傳送非 ASCII 字元將會導致 <xref:System.Net.Http.HttpRequestException> 。 這相當於將值設定為 `false` 。

| | 設定名稱 | 值 |
| - | - | - |
| **runtimeconfig.js開啟** | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | `false` -已停用<br/>`true` -已啟用 |
| **環境變數** | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | `0` -已停用<br/>`1` -已啟用 |

> [!NOTE]
> 此選項僅適用于 .NET Core 3.1 （自版本3.1.9），不適用於舊版或更新版本。 在 .NET 5 中，我們建議使用 <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> 。
