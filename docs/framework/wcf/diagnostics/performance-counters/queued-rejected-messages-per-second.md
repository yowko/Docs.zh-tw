---
title: 每秒佇列拒絕的訊息數
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 805b4f5d1e7882f38cfcc76ad63451d735389d5f
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163965"
---
# <a name="queued-rejected-messages-per-second"></a>每秒佇列拒絕的訊息數
計數器名稱：每秒拒絕的佇列訊息。  
  
## <a name="description"></a>描述  
 此服務的佇列傳輸每秒拒絕的訊息數。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
