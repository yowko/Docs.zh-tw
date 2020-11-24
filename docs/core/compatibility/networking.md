---
title: 網路中斷性變更
description: 列出 .NET Core 2.0 和3.0 中網路功能的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: 761c6481888bcb8e91f7b4212355aca067632495
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689208"
---
# <a name="networking-breaking-changes-in-net-core-20-and-30"></a>.NET Core 2.0 和3.0 中的網路中斷性變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | - |
| [HttpRequestMessage 的預設值已變更為1。1](#default-value-of-httprequestmessageversion-changed-to-11) | 3.0 |
| [WebClient >cancelasync 不一定會立即取消](#webclientcancelasync-doesnt-always-cancel-immediately) | 2.0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
