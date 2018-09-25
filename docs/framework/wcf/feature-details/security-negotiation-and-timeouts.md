---
title: 安全性交涉與逾時
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
ms.openlocfilehash: 6b6c9c6ed44eb3ebefb21f2fbff1e73171262ed7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088304"
---
# <a name="security-negotiation-and-timeouts"></a>安全性交涉與逾時
當用戶端和服務驗證時，Windows Communication Foundation (WCF) 支援驗證過程中交涉服務認證的其中一個模式。 在這類案例中，用戶端和伺服器之間可能會進行 multi-leg 交換，以便將服務認證傳播至用戶端。 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 屬性會控制完成 multi-leg 交換所需要的時間。 不過，只有在交換所花費的實際時間超過單一要求-回應的時間時，這個逾時情況才適用。 如果在單一來回行程中完成交涉，逾時就不適用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [如何：設定最大時鐘誤差](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
