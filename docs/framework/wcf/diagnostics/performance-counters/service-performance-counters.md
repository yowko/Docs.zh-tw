---
title: 服務效能計數器
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: bdc68fd2b629c538c097dab4e1cf3f89b7f3a091
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810183"
---
# <a name="service-performance-counters"></a>服務效能計數器
服務效能計數器會測量整體的服務行為，而且可用於診斷整個服務的效能。 以效能監視器 (Perfmon.exe) 檢視時，可以在 `ServiceModelService 4.0.0.0` 效能物件下找到它們。 執行個體會使用以下模式來命名：  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  效能計數器執行個體的名稱具有長度限制。 當 Windows Communication Foundation (WCF) 計數器執行個體名稱超出最大長度時，WCF 會取代的雜湊值的執行個體名稱的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [效能計數器](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
