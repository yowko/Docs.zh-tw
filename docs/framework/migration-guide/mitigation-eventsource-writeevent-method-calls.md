---
title: "風險降低：EventSource.WriteEvent 方法呼叫 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cde809989d89c10caeb97ec853c8649a108cd72d
ms.contentlocale: zh-tw
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-eventsourcewriteevent-method-calls"></a>風險降低：EventSource.WriteEvent 方法呼叫
[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 會在衍生自 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 之類別的 ETW 事件方法和其基底類別的 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法之間強制協定。 ETW 事件方法必須對 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法傳遞事件 ID，後面跟著傳遞至此事件方法的相同引數。  
  
## <a name="impact"></a>影響  
 以下列方式定義的 ETW 事件方法會中斷協定：  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message, "-");  
}  
```  
  
 違反此協定時，如果 <xref:System.Diagnostics.Tracing.EventListener> 物件讀取處理中 <xref:System.Diagnostics.Tracing.EventSource> 資料時，在執行階段會擲回 <xref:System.IndexOutOfRangeException> 例外狀況。  
  
 這個 ETW 事件方法的定義應該遵循這個模式：  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message);  
}  
```  
  
## <a name="mitigation"></a>緩和  
 您必須修改現有的程式碼，以符合所需的模式。  
  
 您必須定義兩個用於呼叫 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法的方法，將需要變更的程式碼數量降到最低，如下所示：  
  
```  
[NonEvent]  
public void Info2(string message)  
{  
   Info2Internal(message, "-");  
}  
  
public void Info2Internal(string message, string prefix)  
{  
   WriteEvent(2, message, prefix);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

