---
title: 服務：每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: 1151117c8537d4a8eaa4de60d14e314b55ce82d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474840"
---
# <a name="service-transactions-flowed-per-second"></a>服務：每秒流動的異動數
計數器名稱：每秒流動的異動數。  
  
## <a name="description"></a>描述  
 每秒流動至此服務中作業的異動數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
