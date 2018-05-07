---
title: 服務：每秒未授權的安全性呼叫數
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d1fa297536cbac174e77b2d19b53b642a577f949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="service-security-calls-not-authorized-per-second"></a>服務：每秒未授權的安全性呼叫數
計數器名稱：每秒未授權的安全性呼叫數  
  
## <a name="description"></a>描述  
 來自有效使用者且適當保護的每秒傳入訊息數，但使用者未獲授權以執行特定工作。  
  
 當 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法傳回 `false` 時，此計數器就會遞增。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
