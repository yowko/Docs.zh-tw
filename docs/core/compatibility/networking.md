---
title: 網路中斷性變更
description: 列出 .NET Core 中網路功能的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: 07e0b2e062ce244cd6312bbe08bcc63db4c74347
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859635"
---
# <a name="networking-breaking-changes"></a><span data-ttu-id="e558c-103">網路中斷性變更</span><span class="sxs-lookup"><span data-stu-id="e558c-103">Networking breaking changes</span></span>

<span data-ttu-id="e558c-104">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="e558c-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e558c-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="e558c-105">Breaking change</span></span> | <span data-ttu-id="e558c-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e558c-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="e558c-107">HttpRequestMessage 的預設值。版本已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="e558c-107">Default value of HttpRequestMessage.Version changed to 1.1</span></span>](#default-value-of-httprequestmessageversion-changed-to-11) | <span data-ttu-id="e558c-108">3.0</span><span class="sxs-lookup"><span data-stu-id="e558c-108">3.0</span></span> |
| [<span data-ttu-id="e558c-109">WebClient 地說 cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="e558c-109">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately) | <span data-ttu-id="e558c-110">2.0</span><span class="sxs-lookup"><span data-stu-id="e558c-110">2.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="e558c-111">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e558c-111">.NET Core 3.0</span></span>

[!INCLUDE[Default value of HttpRequestMessage.Version changed to 1.1](~/includes/core-changes/networking/3.0/httprequestmessage-version-change.md)]

***

## <a name="net-core-20"></a><span data-ttu-id="e558c-112">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e558c-112">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***
