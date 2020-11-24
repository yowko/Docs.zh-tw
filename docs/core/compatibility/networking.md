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
# <a name="networking-breaking-changes-in-net-core-20-and-30"></a><span data-ttu-id="a8ccf-103">.NET Core 2.0 和3.0 中的網路中斷性變更</span><span class="sxs-lookup"><span data-stu-id="a8ccf-103">Networking breaking changes in .NET Core 2.0 and 3.0</span></span>

<span data-ttu-id="a8ccf-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="a8ccf-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="a8ccf-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="a8ccf-105">Breaking change</span></span> | <span data-ttu-id="a8ccf-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a8ccf-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="a8ccf-107">HttpRequestMessage 的預設值已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="a8ccf-107">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="a8ccf-108">3.0</span><span class="sxs-lookup"><span data-stu-id="a8ccf-108">3.0</span></span> |
| [<span data-ttu-id="a8ccf-109">WebClient >cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="a8ccf-109">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="a8ccf-110">2.0</span><span class="sxs-lookup"><span data-stu-id="a8ccf-110">2.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="a8ccf-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a8ccf-111">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="a8ccf-112">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a8ccf-112">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
