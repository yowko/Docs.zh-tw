---
title: 端點：每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: b8c0f91b2de5d023232756159a50236574308954
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290838"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a>端點：每秒捨棄的可信賴傳訊訊息數

計數器名稱：每秒捨棄的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  

 在此端點上每秒已捨棄的可信賴傳訊訊息數。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
