---
title: 安全性交涉與逾時
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 4ccc7e5539b1a772be6f9edb5a4cb4d94a8d1c1b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275979"
---
# <a name="security-negotiation-and-timeouts"></a>安全性交涉與逾時

當用戶端和服務進行驗證時，Windows Communication Foundation (WCF) 支援一種模式，在此模式下會將服務認證作為驗證的一部分進行協商。 在這類案例中，用戶端和伺服器之間可能會進行 multi-leg 交換，以便將服務認證傳播至用戶端。 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 屬性會控制完成 multi-leg 交換所需要的時間。 不過，只有在交換所花費的實際時間超過單一要求-回應的時間時，這個逾時情況才適用。 如果在單一來回行程中完成交涉，逾時就不適用。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [作法：設定最大時鐘誤差](how-to-set-a-max-clock-skew.md)
