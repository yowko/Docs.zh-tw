---
title: 端點：每秒發生錯誤的可信賴傳訊工作階段數
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 26fd8236af6516716f7cf9c7c06f669473bdfc3a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163185"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>端點：每秒發生錯誤的可信賴傳訊工作階段數
計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  
 在此端點每秒發生的可信賴傳訊工作階段錯誤數。  
  
 此計數器是效能計數器類型[PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值是使用下列公式來計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
