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
`commonBehaviors` 區段只能定義在 machine.config 檔中。 它會定義兩個名為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。  每個集合會分別定義機器上所有 WCF 端點和服務所使用的行為專案。 在 `endpointBehaviors` 中定義的行為只會套用至用戶端，在 `serviceBehaviors` 中定義的行為只會套用至服務。 如果 `commonBehaviors` 和 `behaviors` 區段中都有定義某個行為，則會優先使用 `behaviors` 區段中的行為。
