---
title: 網路中斷性變更
description: 列出 .NET Core 網路功能的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: 568d26bde43ccd6e19fbe2d947f576ef5f99450a
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608462"
---
# <a name="networking-breaking-changes"></a>網路中斷性變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | - |
| [WinHttpHandler 已從 .NET 執行時間移除](#winhttphandler-removed-from-net-runtime) | 5.0 |
| [MulticastOption。群組不接受 null 值](#multicastoptiongroup-doesnt-accept-a-null-value) | 5.0 |
| [HttpRequestMessage 的預設值已變更為1。1](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient >cancelasync 不一定會立即取消](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
