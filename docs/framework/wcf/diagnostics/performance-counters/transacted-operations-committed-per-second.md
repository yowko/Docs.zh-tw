---
title: 每秒認可的交易作業數
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 047640e9b5cc22f2d443832fb7bd5afd47aef5be
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550634"
---
# <a name="transacted-operations-committed-per-second"></a>每秒認可的交易作業數
計數器名稱：每秒認可的交易作業數。  
  
## <a name="description"></a>描述  
 此服務每秒所認可的異動作業數。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
