---
title: 每秒失敗的呼叫數
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321114"
---
# <a name="calls-failed-per-second"></a>每秒失敗的呼叫數
計數器名稱：每秒失敗的呼叫數  
  
## <a name="description"></a>描述  
 此作業中包含每秒未處理例外狀況的呼叫數。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 每次此作業中有未處理的例外狀況時，此計數器就會遞增。  
  
## <a name="see-also"></a>請參閱

- [指定及處理合約與服務中的錯誤](../../specifying-and-handling-faults-in-contracts-and-services.md)
