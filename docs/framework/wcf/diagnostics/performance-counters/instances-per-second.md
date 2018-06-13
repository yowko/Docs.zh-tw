---
title: 每秒的執行個體數
ms.date: 03/30/2017
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
ms.openlocfilehash: c955d2cd0d87c89f412892e7088285f2db27ff42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471864"
---
# <a name="instances-per-second"></a>每秒的執行個體數
計數器名稱：每秒建立的執行個體。  
  
## <a name="description"></a>描述  
 每秒建立的服務執行個體總數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
