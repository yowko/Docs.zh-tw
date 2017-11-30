---
title: "服務：每秒失敗的呼叫數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2072a686d5d424f90ac2f32cf5fc11564b07542c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-failed-per-second"></a>服務：每秒失敗的呼叫數
計數器名稱：每秒失敗的呼叫數。  
  
## <a name="description"></a>描述  
 未處理之例外狀況的呼叫數，以及此服務在一秒之內所收到的呼叫數。  
  
 這個計數器的效能計數器型別是[PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)，其值使用以下公式計算。  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。  
  
 在 Managed 程式碼中，發生錯誤狀況時會擲回例外狀況。  
  
 每當此服務有未處理的例外狀況時，此計數器就會遞增。  
  
## <a name="see-also"></a>另請參閱  
 [指定及處理合約與服務中的錯誤](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
