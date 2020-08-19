---
title: 網路中斷性變更
description: 列出 .NET Core 網路功能的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: 5d27f9663a2c1b79610ab002a03beeafa8b2818e
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557956"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="b1a70-103">網路中斷性變更</span><span class="sxs-lookup"><span data-stu-id="b1a70-103">Networking breaking changes</span></span>

<span data-ttu-id="b1a70-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="b1a70-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b1a70-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="b1a70-105">Breaking change</span></span> | <span data-ttu-id="b1a70-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b1a70-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="b1a70-107">MulticastOption。群組不接受 null 值</span><span class="sxs-lookup"><span data-stu-id="b1a70-107">MulticastOption.Group doesn't accept a null value</span></span>](#multicastoptiongroup-doesnt-accept-a-null-value) | <span data-ttu-id="b1a70-108">5.0</span><span class="sxs-lookup"><span data-stu-id="b1a70-108">5.0</span></span> |
| [<span data-ttu-id="b1a70-109">HttpRequestMessage 的預設值已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="b1a70-109">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="b1a70-110">3.0</span><span class="sxs-lookup"><span data-stu-id="b1a70-110">3.0</span></span> |
| [<span data-ttu-id="b1a70-111">WebClient >cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="b1a70-111">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="b1a70-112">2.0</span><span class="sxs-lookup"><span data-stu-id="b1a70-112">2.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="b1a70-113">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="b1a70-113">.NET 5.0</span></span>

[!INCLUDE [multicastoption-group-doesnt-accept-null](../../../includes/core-changes/networking/5.0/multicastoption-group-doesnt-accept-null.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="b1a70-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1a70-114">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="b1a70-115">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b1a70-115">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
