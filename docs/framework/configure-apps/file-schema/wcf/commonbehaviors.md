---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350318"
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="ec6f3-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="ec6f3-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="ec6f3-103">`commonBehaviors` 區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="ec6f3-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="ec6f3-104">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="ec6f3-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="ec6f3-105">每個集合會定義分別由所有 WCF 端點和電腦上的服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="ec6f3-105">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="ec6f3-106">在 `endpointBehaviors` 中定義的行為只會套用至用戶端，在 `serviceBehaviors` 中定義的行為只會套用至服務。</span><span class="sxs-lookup"><span data-stu-id="ec6f3-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="ec6f3-107">如果 `commonBehaviors` 和 `behaviors` 區段中都有定義某個行為，則會優先使用 `behaviors` 區段中的行為。</span><span class="sxs-lookup"><span data-stu-id="ec6f3-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
