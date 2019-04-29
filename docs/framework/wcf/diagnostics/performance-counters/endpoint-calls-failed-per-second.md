---
title: 端點：每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 52419f45adde768d19d6b46642d52ad0a1844197
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797341"
---
# <a name="endpoint-calls-failed-per-second"></a>端點：每秒失敗的呼叫數
計數器名稱：每秒失敗的呼叫數。  
  
## <a name="description"></a>描述  
 具有未處理的例外狀況以及由這個端點在一秒內收到的呼叫數目。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 每當這個端點有未處理的例外狀況時，這個計數器就會遞增。  
  
## <a name="see-also"></a>另請參閱

- [指定及處理合約與服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
