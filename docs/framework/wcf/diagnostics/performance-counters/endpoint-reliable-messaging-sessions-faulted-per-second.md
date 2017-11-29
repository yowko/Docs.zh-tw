---
title: "端點：每秒發生錯誤的可信賴傳訊工作階段數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f4a8614420a11b31bf3b19fb03e13210f4590a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>端點：每秒發生錯誤的可信賴傳訊工作階段數
計數器名稱：每秒發生錯誤的可信賴傳訊工作階段數。  
  
## <a name="description"></a>描述  
 在此端點每秒發生的可信賴傳訊工作階段錯誤數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
