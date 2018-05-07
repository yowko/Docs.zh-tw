---
title: 每秒發生錯誤的可信賴傳訊工作階段數
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: fafc63d692d2a6892330b0be5fe534ace5d7f0ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a>每秒發生錯誤的可信賴傳訊工作階段數
計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  
 在此服務每秒發生的可信賴傳訊工作階段錯誤數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
