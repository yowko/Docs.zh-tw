---
title: 作業效能計數器
ms.date: 03/30/2017
ms.assetid: 333a51e0-f56e-4e1a-b359-5c91ff390568
ms.openlocfilehash: d4f5755129fecb62e6a4da98a2bf642c5e20f9c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916197"
---
# <a name="operation-performance-counters"></a>作業效能計數器
當使用效能監視器 (Perfmon.exe) 檢視時，您可以在 `ServiceModelOperation 4.0.0.0` 效能物件中找到作業效能計數器。 每個作業都有個別的執行個體。 也就是，如果指定的合約有 10 個作業，就會有 10 個作業計數器執行個體與該合約產生關聯。 物件執行個體會使用以下模式來命名：  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 這個計數器能夠讓您測量呼叫的使用狀況，以及作業的執行效能。  
  
> [!CAUTION]
>  效能計數器執行個體的名稱具有長度限制。 當 Windows Communication Foundation (WCF) 計數器執行個體名稱超過最大長度時，WCF 會以雜湊值取代一部分的執行個體名稱。  
  
## <a name="see-also"></a>另請參閱

- [效能計數器](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
