---
title: 每秒認可的交易作業數
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: b81146516413c4afa9baf9a533797f0867a1b20d
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163848"
---
# <a name="transacted-operations-committed-per-second"></a>每秒認可的交易作業數
計數器名稱：每秒認可的交易作業數。  
  
## <a name="description"></a>描述  
 此服務每秒所認可的異動作業數。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
