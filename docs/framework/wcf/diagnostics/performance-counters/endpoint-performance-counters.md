---
title: 端點效能計數器
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: 2352bc82998c8e87e72f331104446bac4fcb9fda
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040575"
---
# <a name="endpoint-performance-counters"></a>端點效能計數器
端點效能計數器會擷取顯示端點如何接受訊息的資料。 使用效能監視器檢視時，可以在 `ServiceModelEndpoint 4.0.0.0` 效能物件下找到它們。 執行個體是使用下列模式來命名：  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 此資料與針對個別作業而收集的資料類似，但只彙總了端點之間的資料。  
  
> [!CAUTION]
> 效能計數器執行個體的名稱具有長度限制。 當 Windows Communication Foundation (WCF) 計數器實例名稱超過最大長度時, WCF 會以雜湊值取代實例名稱的一部分。  
  
## <a name="see-also"></a>另請參閱

- [效能計數器](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
