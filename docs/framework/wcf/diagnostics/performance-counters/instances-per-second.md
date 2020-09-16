---
title: 每秒的執行個體數
ms.date: 03/30/2017
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
ms.openlocfilehash: 9b78707f3815fd370d3398f1a7b422ee4bf2d369
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541222"
---
# <a name="instances-per-second"></a>每秒的執行個體數
計數器名稱：每秒建立的執行個體。  
  
## <a name="description"></a>描述  
 每秒建立的服務執行個體總數。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
