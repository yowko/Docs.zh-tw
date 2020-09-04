---
title: 網路中斷性變更
description: 列出 .NET Core 網路功能的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: fa5807c882c3bc6f66e8a27361ccc14254e90b3e
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465506"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="59cae-103">網路中斷性變更</span><span class="sxs-lookup"><span data-stu-id="59cae-103">Networking breaking changes</span></span>

<span data-ttu-id="59cae-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="59cae-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="59cae-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="59cae-105">Breaking change</span></span> | <span data-ttu-id="59cae-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="59cae-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="59cae-107">WinHttpHandler 已從 .NET 執行時間移除</span><span class="sxs-lookup"><span data-stu-id="59cae-107">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="59cae-108">5.0</span><span class="sxs-lookup"><span data-stu-id="59cae-108">5.0</span></span> |
| [<span data-ttu-id="59cae-109">MulticastOption。群組不接受 null 值</span><span class="sxs-lookup"><span data-stu-id="59cae-109">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="59cae-110">5.0</span><span class="sxs-lookup"><span data-stu-id="59cae-110">5.0</span></span> |
| [<span data-ttu-id="59cae-111">Cookie 路徑處理現在符合 RFC 6265</span><span class="sxs-lookup"><span data-stu-id="59cae-111">Cookie Path handling now conforms to RFC 6265</span></span>](#cookie-path-handling-now-conforms-to-rfc-6265) | <span data-ttu-id="59cae-112">5.0</span><span class="sxs-lookup"><span data-stu-id="59cae-112">5.0</span></span> |
| [<span data-ttu-id="59cae-113">HttpRequestMessage 的預設值已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="59cae-113">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="59cae-114">3.0</span><span class="sxs-lookup"><span data-stu-id="59cae-114">3.0</span></span> |
| [<span data-ttu-id="59cae-115">WebClient >cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="59cae-115">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="59cae-116">2.0</span><span class="sxs-lookup"><span data-stu-id="59cae-116">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="59cae-117">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="59cae-117">.NET 5.0</span></span>

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

[!INCLUDE [cookie-path-conforms-to-rfc6265](../../../includes/core-changes/networking/5.0/cookie-path-conforms-to-rfc6265.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="59cae-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="59cae-118">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="59cae-119">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="59cae-119">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
