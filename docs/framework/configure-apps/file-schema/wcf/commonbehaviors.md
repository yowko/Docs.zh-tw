---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704358"
---
# \<commonBehaviors>
<span data-ttu-id="13441-101">`commonBehaviors` 區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="13441-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="13441-102">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="13441-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="13441-103">每個集合會分別定義機器上所有 WCF 端點和服務所使用的行為專案。</span><span class="sxs-lookup"><span data-stu-id="13441-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="13441-104">在 `endpointBehaviors` 中定義的行為只會套用至用戶端，在 `serviceBehaviors` 中定義的行為只會套用至服務。</span><span class="sxs-lookup"><span data-stu-id="13441-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="13441-105">如果 `commonBehaviors` 和 `behaviors` 區段中都有定義某個行為，則會優先使用 `behaviors` 區段中的行為。</span><span class="sxs-lookup"><span data-stu-id="13441-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
