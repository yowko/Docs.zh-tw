---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704358"
---
# <a name="commonbehaviors"></a><span data-ttu-id="8fed8-101">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="8fed8-101">\<commonBehaviors></span></span>
<span data-ttu-id="8fed8-102">`commonBehaviors` 區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="8fed8-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="8fed8-103">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="8fed8-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="8fed8-104">每個集合會定義分別由所有 WCF 端點和電腦上的服務的行為項目。</span><span class="sxs-lookup"><span data-stu-id="8fed8-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="8fed8-105">在 `endpointBehaviors` 中定義的行為只會套用至用戶端，在 `serviceBehaviors` 中定義的行為只會套用至服務。</span><span class="sxs-lookup"><span data-stu-id="8fed8-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="8fed8-106">如果 `commonBehaviors` 和 `behaviors` 區段中都有定義某個行為，則會優先使用 `behaviors` 區段中的行為。</span><span class="sxs-lookup"><span data-stu-id="8fed8-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
