---
title: "端點效能計數器 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d44d576-bd4e-453b-8b76-a818ce90b806
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 端點效能計數器
端點效能計數器會擷取顯示端點如何接受訊息的資料。使用效能監視器檢視時，可以在 `ServiceModelEndpoint 4.0.0.0` 效能物件下找到它們。執行個體是使用下列模式來命名：  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 此資料與針對個別作業而收集的資料類似，但只彙總了端點之間的資料。  
  
> [!CAUTION]
>  效能計數器執行個體的名稱具有長度限制。當 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 計數器執行個體名稱超出最大長度時，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會以雜湊值取代此執行個體名稱的一部分。  
  
## 請參閱  
 [效能計數器](../../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)