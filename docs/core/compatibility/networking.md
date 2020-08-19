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
# <a name="networking-breaking-changes"></a><span data-ttu-id="10a04-103">網路中斷性變更</span><span class="sxs-lookup"><span data-stu-id="10a04-103">Networking breaking changes</span></span>

<span data-ttu-id="10a04-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="10a04-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="10a04-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="10a04-105">Breaking change</span></span> | <span data-ttu-id="10a04-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="10a04-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="10a04-107">WinHttpHandler 已從 .NET 執行時間移除</span><span class="sxs-lookup"><span data-stu-id="10a04-107">WinHttpHandler removed from .NET runtime</span></span>](#winhttphandler-removed-from-net-runtime) | <span data-ttu-id="10a04-108">5.0</span><span class="sxs-lookup"><span data-stu-id="10a04-108">5.0</span></span> |
| [<span data-ttu-id="10a04-109">MulticastOption。群組不接受 null 值</span><span class="sxs-lookup"><span data-stu-id="10a04-109">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="10a04-110">5.0</span><span class="sxs-lookup"><span data-stu-id="10a04-110">5.0</span></span> |
| [<span data-ttu-id="10a04-111">HttpRequestMessage 的預設值已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="10a04-111">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="10a04-112">3.0</span><span class="sxs-lookup"><span data-stu-id="10a04-112">3.0</span></span> |
| [<span data-ttu-id="10a04-113">WebClient >cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="10a04-113">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="10a04-114">2.0</span><span class="sxs-lookup"><span data-stu-id="10a04-114">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="10a04-115">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="10a04-115">.NET 5.0</span></span>

[!INCLUDE [winhttphandler-removed-from-runtime](../../../includes/core-changes/networking/5.0/winhttphandler-removed-from-runtime.md)]

***

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="10a04-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="10a04-116">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="10a04-117">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="10a04-117">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
