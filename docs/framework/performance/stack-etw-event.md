---
title: "堆疊 ETW 事件 | Microsoft Docs"
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
  - "ETW, 堆疊事件 (CLR)"
  - "堆疊事件 [.NET Framework]"
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# 堆疊 ETW 事件
堆疊事件應該搭配其他事件使用，以便在引發事件之後產生堆疊追蹤。  啟用執行階段提供者時，就會記錄這個事件。  這是發生頻率非常高的事件，因為每當引發另一個執行階段事件時，就會引發此事件。  因此，我們建議您謹慎使用這個事件。  
  
 下表顯示關鍵字和層級。\(如需詳細資訊，請參閱 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)\)。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`StackKeyword` \(0x40000000\)|永遠記錄\(0\)|  
  
 下表顯示事件資訊。  
  
|事件|事件識別碼|引發時機|  
|--------|-----------|----------|  
|`CLRStackWalk`|82|搭配其他事件，以便在事件之後產生堆疊追蹤。|  
  
 下表顯示事件資料。  
  
|欄位名稱|資料型別|說明|  
|----------|----------|--------|  
|ClrInstanceID|win:Uint16|唯一的執行階段識別項。|  
|Reserved1|win:UInt8|保留的。|  
|Reserved2|win:UInt8|保留的。|  
|FrameCount|win:UInt32|堆疊追蹤中的框架數。|  
|堆疊|win:Pointer|指令指標的資料行。|  
  
## 請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)