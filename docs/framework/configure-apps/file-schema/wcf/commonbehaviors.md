---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 55f70157b6759c5e1cb45da20eed928fa1d4a183
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176054"
---
# \<commonBehaviors>

<span data-ttu-id="cc23c-101">`commonBehaviors` 區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="cc23c-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="cc23c-102">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="cc23c-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="cc23c-103">每個集合會分別定義電腦上所有 WCF 端點和服務所使用的行為元素。</span><span class="sxs-lookup"><span data-stu-id="cc23c-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="cc23c-104">在 `endpointBehaviors` 中定義的行為只會套用至用戶端，在 `serviceBehaviors` 中定義的行為只會套用至服務。</span><span class="sxs-lookup"><span data-stu-id="cc23c-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="cc23c-105">如果 `commonBehaviors` 和 `behaviors` 區段中都有定義某個行為，則會優先使用 `behaviors` 區段中的行為。</span><span class="sxs-lookup"><span data-stu-id="cc23c-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
