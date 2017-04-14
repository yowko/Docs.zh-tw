---
title: "Exception Thrown_V1 ETW 事件 | Microsoft Docs"
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
  - "ETW, ExceptionThrown_V1 事件 (CLR)"
  - "ExceptionThrown_V1 事件 [.NET Framework]"
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: 6
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 6
---
# Exception Thrown_V1 ETW 事件
這個事件會擷取有關所擲回之例外狀況的資訊。  
  
 下表會說明引發事件的關鍵字，以及事件的層級：\(如需詳細資訊，請參閱 [CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)\)。  
  
|引發事件的關鍵字|層級|  
|--------------|--------|  
|`ExceptionKeyword` \(0x8000\)|警告 \(2\)|  
  
 下表顯示事件資訊。  
  
|事件|事件識別碼|引發時機|  
|--------|-----------|----------|  
|`ExceptionThrown_V1`|80|擲回 Managed 例外狀況。|  
  
 下表顯示事件資料。  
  
|欄位名稱|資料型別|說明|  
|----------|----------|--------|  
|例外狀況類型|win:UnicodeString|例外狀況的類型，例如 `System.NullReferenceException`。|  
|例外狀況訊息|win:UnicodeString|實際的例外狀況訊息。|  
|EIPCodeThrow|win:Pointer|發生例外狀況的指令指標。|  
|ExceptionHR|win:UInt32|例外狀況 [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679)。|  
|ExceptionFlags|win:UInt16|0x01：HasInnerException \(請參閱 Visual Basic 文件中的 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)\)。<br /><br /> 0x02：IsNestedException。<br /><br /> 0x04：IsRethrownException。<br /><br /> 0x08: IsCorruptedStateException \(表示處理序狀態已損毀。請參閱 MSDN 上的[處理損毀狀態的例外狀況](http://go.microsoft.com/fwlink/?LinkId=179681)\)。<br /><br /> 0x10：IsCLSCompliant \(衍生自 <xref:System.Exception> 的例外狀況符合 CLS 標準。否則，它不符合 CLS 標準\)。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## 請參閱  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)