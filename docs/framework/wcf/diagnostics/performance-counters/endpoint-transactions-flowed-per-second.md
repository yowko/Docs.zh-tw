---
title: 端點：每秒流動的異動數
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: b814d7ca9e286426289c611b3a6bf5a52c1b2335
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256426"
---
# <a name="endpoint-transactions-flowed-per-second"></a>端點：每秒流動的異動數

計數器名稱：每秒流動的交易數。  
  
## <a name="description"></a>描述  

 每秒流動至此端點處作業的交易數。 每當傳送給端點的訊息中有交易識別碼存在時，此計數器就會遞增。  
  
 此計數器是效能計數器類型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
