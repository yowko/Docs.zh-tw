---
title: 每秒的呼叫數
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: 766e481478cf98c43a898bf28fcd7af3896b2327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271339"
---
# <a name="calls-per-second"></a>每秒的呼叫數

計數器名稱：每秒的呼叫數  
  
## <a name="description"></a>描述  

 對這個作業的每秒呼叫數。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
