---
title: "爭用 ETW 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "爭用事件 [.NET Framework]"
  - "ETW, 爭用事件 (CLR)"
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 爭用 ETW 事件
每當發生 <xref:System.Threading.Monitor?displayProperty=fullName> 鎖定的爭用或執行階段所使用之原生鎖定的爭用時，就會引發爭用事件。  當某個執行緒正在等候鎖定，而另一個執行緒處理此鎖定時，就會發生爭用。  
  
 下表會說明引發事件的關鍵字，以及事件的層級：\(如需詳細資訊，請參閱 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)\)。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`ContentionKeyword` \(0x4000\)|告知性 \(4\)|  
  
 下表顯示事件資訊。  
  
|事件|事件識別碼|引發時機|  
|--------|-----------|----------|  
|`ContentionStart_V1`|81|爭用開始。  此事件不會包括執行緒等候以取得鎖定之前的空轉時間量。只有當執行緒等候以取得鎖定時，才會引發此事件。|  
|`ContentionStop`|81|爭用資料結束。|  
  
 下表顯示事件資料。  
  
|欄位名稱|資料型別|說明|  
|----------|----------|--------|  
|旗標|win:UInt8|0 代表 Managed，而 1 代表原生。|  
|ClrInstanceID|win:UInt16|CLR 執行個體的唯一 ID。|  
  
## 請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)