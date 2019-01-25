---
title: 端點效能計數器
ms.date: 03/30/2017
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
ms.openlocfilehash: de750b3e5ee61b6bfc5b387fb7de84b74171d8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501957"
---
# <a name="endpoint-performance-counters"></a>端點效能計數器
端點效能計數器會擷取顯示端點如何接受訊息的資料。 使用效能監視器檢視時，可以在 `ServiceModelEndpoint 4.0.0.0` 效能物件下找到它們。 執行個體是使用下列模式來命名：  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 此資料與針對個別作業而收集的資料類似，但只彙總了端點之間的資料。  
  
> [!CAUTION]
>  效能計數器執行個體的名稱具有長度限制。 當 Windows Communication Foundation (WCF) 計數器執行個體名稱超過最大長度時，WCF 會以雜湊值取代一部分的執行個體名稱。  
  
## <a name="see-also"></a>另請參閱
- [效能計數器](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
