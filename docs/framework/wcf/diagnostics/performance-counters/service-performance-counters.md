---
title: "服務效能計數器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4210f549-31f2-4ea7-99bd-69eaffb98ddf
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2bc29ace454c6c41d3ad6ec11f98a9e6fb3e7d0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="service-performance-counters"></a>服務效能計數器
服務效能計數器會測量整體的服務行為，而且可用於診斷整個服務的效能。 以效能監視器 (Perfmon.exe) 檢視時，可以在 `ServiceModelService 4.0.0.0` 效能物件下找到它們。 執行個體會使用以下模式來命名：  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
> [!CAUTION]
>  效能計數器執行個體的名稱具有長度限制。 當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 計數器執行個體名稱超出最大長度時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會以雜湊值取代此執行個體名稱的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [效能計數器](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
