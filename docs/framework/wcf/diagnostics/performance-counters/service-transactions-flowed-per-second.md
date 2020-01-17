---
title: 服務：每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: e8fbc314321a46fd3539998bd3dd22770086ca37
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164004"
---
# <a name="service-transactions-flowed-per-second"></a>服務：每秒流動的異動數
計數器名稱：每秒流動的交易數。  
  
## <a name="description"></a>描述  
 每秒流動至此服務中作業的交易數。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
