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
# <a name="networking-breaking-changes"></a><span data-ttu-id="f94ea-103">網路中斷性變更</span><span class="sxs-lookup"><span data-stu-id="f94ea-103">Networking breaking changes</span></span>

<span data-ttu-id="f94ea-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="f94ea-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="f94ea-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="f94ea-105">Breaking change</span></span> | <span data-ttu-id="f94ea-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="f94ea-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="f94ea-107">NegotiateStream 和 SslStream 允許連續的開始作業</span><span class="sxs-lookup"><span data-stu-id="f94ea-107">NegotiateStream and SslStream allow successive Begin operations</span></span>](#negotiatestream-and-sslstream-allow-successive-begin-operations) | <span data-ttu-id="f94ea-108">5.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-108">5.0</span></span> |
| [<span data-ttu-id="f94ea-109">LocalEndPoint 會在呼叫 SendToAsync 之後更新</span><span class="sxs-lookup"><span data-stu-id="f94ea-109">Socket.LocalEndPoint is updated after calling SendToAsync</span></span>](#socketlocalendpoint-is-updated-after-calling-sendtoasync) | <span data-ttu-id="f94ea-110">5.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-110">5.0</span></span> |
| [<span data-ttu-id="f94ea-111">WinHttpHandler 已從 .NET 執行時間移除</span><span class="sxs-lookup"><span data-stu-id="f94ea-111">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="f94ea-112">5.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-112">5.0</span></span> |
| [<span data-ttu-id="f94ea-113">MulticastOption。群組不接受 null 值</span><span class="sxs-lookup"><span data-stu-id="f94ea-113">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="f94ea-114">5.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-114">5.0</span></span> |
| [<span data-ttu-id="f94ea-115">Cookie 路徑處理現在符合 RFC 6265</span><span class="sxs-lookup"><span data-stu-id="f94ea-115">Cookie Path handling now conforms to RFC 6265</span></span>](#cookie-path-handling-now-conforms-to-rfc-6265) | <span data-ttu-id="f94ea-116">5.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-116">5.0</span></span> |
| [<span data-ttu-id="f94ea-117">HttpRequestMessage 的預設值已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="f94ea-117">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="f94ea-118">3.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-118">3.0</span></span> |
| [<span data-ttu-id="f94ea-119">WebClient >cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="f94ea-119">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="f94ea-120">2.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-120">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="f94ea-121">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="f94ea-121">.NET 5.0</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="f94ea-122">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-122">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="f94ea-123">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f94ea-123">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
