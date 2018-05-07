---
title: 服務：每秒的呼叫數
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: c23456f49eb867d5b6f66b4386a83615d95e07da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="service-calls-per-second"></a>服務：每秒的呼叫數
計數器名稱：每秒呼叫數。  
  
## <a name="description"></a>描述  
 對這個服務的每秒呼叫數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)，其中分子 (N) 表示最新樣本間隔期間的已執行作業數，分母 (D) 表示最新樣本間隔期間的已耗用時間，而 F 是刻度的頻率。
