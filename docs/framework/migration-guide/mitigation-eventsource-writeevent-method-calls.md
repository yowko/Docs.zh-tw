---
title: "緩和：EventSource.WriteEvent 方法呼叫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 緩和：EventSource.WriteEvent 方法呼叫
[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 強制在類別中的 ETW 事件方法間遵循協定，此類別是從其基底類別的 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 及 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法取得。 ETW 事件方法必須對 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法傳遞事件 ID，後面跟著傳遞至此事件方法的相同引數。  
  
## 影響  
 以下列方式定義的 ETW 事件方法會中斷協定：  
  
```  
  
[Event(2, Level = EventLevel.Informational)] public void Info2(string message) { base.WriteEvent(2, message, "-"); }  
  
```  
  
 當違反本協定時，如果 <xref:System.Diagnostics.Tracing.EventListener> 物件在程序中讀取 <xref:System.Diagnostics.Tracing.EventSource> 資料，<xref:System.IndexOutOfRangeException> 就會在執行階段擲回例外狀況。  
  
 這個 ETW 事件方法的定義應該遵循這個模式：  
  
```  
  
[Event(2, Level = EventLevel.Informational)] public void Info2(string message) { base.WriteEvent(2, message); }  
  
```  
  
## 緩和  
 您必須修改現有的程式碼，以符合所需的模式。  
  
 您必須定義兩個用於呼叫 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法的方法，將需要變更的程式碼數量降到最低，如下所示：  
  
```  
  
[NonEvent] public void Info2(string message) { Info2Internal(message, "-"); } public void Info2Internal(string message, string prefix) { WriteEvent(2, message, prefix); }  
  
```  
  
## 請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)