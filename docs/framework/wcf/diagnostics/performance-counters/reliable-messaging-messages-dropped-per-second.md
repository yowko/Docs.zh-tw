---
title: 每秒捨棄的可信賴傳訊訊息數
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 946e0408b8b6602bba7824b45e4d6cb91cdaa4eb
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163952"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>每秒捨棄的可信賴傳訊訊息數
計數器名稱：每秒捨棄的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  
 在此服務中已捨棄的每秒可信賴傳訊訊息總數。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
