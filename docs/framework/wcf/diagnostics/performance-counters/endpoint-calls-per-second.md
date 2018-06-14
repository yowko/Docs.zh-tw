---
title: 端點：每秒的呼叫數
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: 186d59d2f0255f0f964130659a2053fc8f440dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474502"
---
# <a name="endpoint-calls-per-second"></a>端點：每秒的呼叫數
計數器名稱：每秒呼叫數。  
  
## <a name="description"></a>描述  
 對這個端點的每秒呼叫數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
