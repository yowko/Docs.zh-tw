---
title: 每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ff9320b0990a0543bbb1da553d040ff5a4b4fed9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797419"
---
# <a name="calls-failed-per-second"></a>每秒失敗的呼叫數
計數器名稱：每秒失敗的呼叫數  
  
## <a name="description"></a>描述  
 此作業中包含每秒未處理例外狀況的呼叫數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 每當此作業含有未處理的例外狀況時，此計數器就會遞增。  
  
## <a name="see-also"></a>另請參閱

- [指定及處理合約與服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
