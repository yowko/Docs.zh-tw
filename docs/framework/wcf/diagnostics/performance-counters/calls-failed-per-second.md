---
title: 每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: d3eafc4b31f0e62093a972b7c9f2325a3648d21b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285456"
---
# <a name="calls-failed-per-second"></a>每秒失敗的呼叫數

計數器名稱：每秒失敗的呼叫數  
  
## <a name="description"></a>描述  

 此作業中包含每秒未處理例外狀況的呼叫數。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 此計數器會在此作業中每次有未處理的例外狀況時遞增。  
  
## <a name="see-also"></a>另請參閱

- [指定與處理合約和服務中的錯誤](../../specifying-and-handling-faults-in-contracts-and-services.md)
