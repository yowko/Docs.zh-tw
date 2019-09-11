---
title: 服務效能計數器
ms.date: 03/30/2017
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
ms.openlocfilehash: 4ce0efbeb0a1d6f2409bb976102b8ec8821d5cdc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848992"
---
# <a name="service-performance-counters"></a>服務效能計數器
服務效能計數器會測量整體的服務行為，而且可用於診斷整個服務的效能。 以效能監視器 (Perfmon.exe) 檢視時，可以在 `ServiceModelService 4.0.0.0` 效能物件下找到它們。 執行個體會使用以下模式來命名：  
  
`ServiceName@ServiceBaseAddress`
  
> [!CAUTION]
> 效能計數器執行個體的名稱具有長度限制。 當 Windows Communication Foundation （WCF）計數器實例名稱超過最大長度時，WCF 會以雜湊值取代實例名稱的一部分。  
  
## <a name="see-also"></a>另請參閱

- [效能計數器](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
