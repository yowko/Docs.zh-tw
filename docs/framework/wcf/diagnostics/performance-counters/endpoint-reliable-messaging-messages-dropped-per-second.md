---
title: 端點：每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737577"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a>端點：每秒捨棄的可信賴傳訊訊息數
計數器名稱：每秒捨棄的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  
 在此端點上每秒已捨棄的可信賴傳訊訊息數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649)，使用下列公式來計算其值。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
