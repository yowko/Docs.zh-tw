---
title: "可執行的執行個體偵測週期 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 可執行的執行個體偵測週期
SQL 工作流程執行個體存放區會執行內部工作，該工作會定期喚醒及偵測持續性資料庫中可執行或可啟動的執行個體。SQL 工作流程執行個體存放區的**可執行的執行個體偵測週期**屬性會指定一段時間，在這段時間之後，SQL 工作流程執行個體存放區會執行偵測工作，以偵測在上一次偵測週期之後，持續性資料庫中任何可執行或可啟動的工作流程執行個體。  
  
 為這個屬性設定較短的間隔，可縮短與工作流程執行個體相關之計時器逾時和發出事件訊號及後續載入執行個體之間的時間。不過，這麼做也會增加主機的處理負載，在極少出現永久性計時器和\/或主機故障的案例中，可能不是適當的做法。屬性的型別是 TimeSpan，屬性值的格式則為：hh:mm:ss。這個屬性的最小值是 00:00:01。屬性的預設值為 00:00:05。  
  
 如需偵測及啟動可執行及可啟動工作流程執行個體的詳細資訊，請參閱[執行個體啟用](../../../docs/framework/windows-workflow-foundation//instance-activation.md)。