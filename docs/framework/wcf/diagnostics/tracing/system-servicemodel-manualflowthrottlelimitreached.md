---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: fb69c3c737a0e77b05e08ab8d8282069feb069bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761516"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a>System.ServiceModel.ManualFlowThrottleLimitReached
System.ServiceModel.ManualFlowThrottleLimitReached  
  
## <a name="description"></a>描述  
 系統已到達針對 ManualFlowControlLimit 節流閥所設定的限制。 您可以視需要修改 ServiceHost 或 InstanceContext 上的 ManualFlowControlLimit 屬性，變更節流閥值。  
  
 當手動流量控制限制一開始降低到 0 時，就會發出此追蹤。 以後再變更為 0 時將不會被追蹤。 執行個體內容上的流量控制限制只會針對每個內容追蹤一次。  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
