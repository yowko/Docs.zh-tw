---
title: 每秒不確定的交易作業數
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 59186b1fc113bb87264a8b946cfee2719ff50b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550595"
---
# <a name="transacted-operations-in-doubt-per-second"></a>每秒不確定的交易作業數
計數器名稱：每秒不確定的交易作業數。  
  
## <a name="description"></a>描述  
 每秒鐘此服務中結果不確定的交易作業數。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
