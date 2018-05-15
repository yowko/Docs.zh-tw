---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: aaf89f73b6de250aaa572b8fef31e5a1ebd5482b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="7c786-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="7c786-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="7c786-103">`commonBehaviors` 區段只能定義在 machine.config 檔中。</span><span class="sxs-lookup"><span data-stu-id="7c786-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="7c786-104">它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="7c786-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="7c786-105">每個集合會分別定義由所有 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 端點和電腦上服務所使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="7c786-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="7c786-106">在 `endpointBehaviors` 中定義的行為只會套用至用戶端，在 `serviceBehaviors` 中定義的行為只會套用至服務。</span><span class="sxs-lookup"><span data-stu-id="7c786-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="7c786-107">如果 `commonBehaviors` 和 `behaviors` 區段中都有定義某個行為，則會優先使用 `behaviors` 區段中的行為。</span><span class="sxs-lookup"><span data-stu-id="7c786-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
