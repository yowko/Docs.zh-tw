---
title: 端點：每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 25e504221097505e622a3ba60f0c7e85ec455f36
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163614"
---
# <a name="endpoint-calls-failed-per-second"></a>端點：每秒失敗的呼叫數
計數器名稱：每秒失敗的呼叫數。  
  
## <a name="description"></a>描述  
 具有未處理的例外狀況以及由這個端點在一秒內收到的呼叫數目。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 每當這個端點有未處理的例外狀況時，這個計數器就會遞增。  
  
## <a name="see-also"></a>請參閱

- [指定及處理合約與服務中的錯誤](../../specifying-and-handling-faults-in-contracts-and-services.md)
