---
title: 網路中斷性變更
description: 列出 .NET Core 網路功能的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: fdbd3f3bdcae5048b4f01e4d827f8a0e876c5c15
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050507"
---
# <a name="networking-breaking-changes"></a>網路中斷性變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | - |
| [NegotiateStream 和 SslStream 允許連續的開始作業](#negotiatestream-and-sslstream-allow-successive-begin-operations) | 5.0 |
| [LocalEndPoint 會在呼叫 SendToAsync 之後更新](#socketlocalendpoint-is-updated-after-calling-sendtoasync) | 5.0 |
| [WinHttpHandler 已從 .NET 執行時間移除](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [MulticastOption。群組不接受 null 值](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [Cookie 路徑處理現在符合 RFC 6265](#cookie-path-handling-now-conforms-to-rfc-6265) | 5.0 |
| [HttpRequestMessage 的預設值已變更為1。1](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient >cancelasync 不一定會立即取消](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [negotiatestream-sslstream-dont-fail-on-successive-begin-calls](../../../includes/core-changes/networking/5.0/negotiatestream-sslstream-dont-fail-on-successive-begin-calls.md)]

***

[!INCLUDE [localendpoint-updated-on-sendtoasync](../../../includes/core-changes/networking/5.0/localendpoint-updated-on-sendtoasync.md)]

***

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
