---
title: 每秒佇列的有害訊息數
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="queued-poison-messages-per-second"></a>每秒佇列的有害訊息數
計數器名稱：每秒佇列的有害訊息數。  
  
## <a name="description"></a>描述  
 此服務佇列傳輸標示為有害的每秒訊息數量。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
