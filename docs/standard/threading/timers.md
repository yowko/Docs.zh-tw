---
title: "Timers | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], timers"
  - "timers, about timers"
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Timers
計時器是讓您能夠指定在指定時間呼叫之委派的輕量型物件。  執行緒集區中的執行緒會執行等候作業。  
  
 使用 <xref:System.Threading.Timer?displayProperty=fullName> 類別非常簡單。  您會建立 **Timer** \(將 <xref:System.Threading.TimerCallback> 委派傳送至回呼方法\)，以及建立表示將傳給回呼之狀態的物件、初始引發時間，以及表示回呼引動過程之間的時間。  若要取消暫止計時器，請呼叫 **Timer.Dispose** 函式。  
  
> [!NOTE]
>  有兩個其他計時器類別。  <xref:System.Windows.Forms.Timer?displayProperty=fullName> 類別是一個與視覺化設計工具一起使用的控制項，它是要用於使用者介面內容中；它會在使用者介面執行緒上引發事件。  <xref:System.Timers.Timer?displayProperty=fullName> 類別衍生自 <xref:System.ComponentModel.Component>，所以它可以與視覺化設計工具一起使用；它也會引發事件，但是在 <xref:System.Threading.ThreadPool> 執行緒上引發。  <xref:System.Threading.Timer?displayProperty=fullName> 類別會在 <xref:System.Threading.ThreadPool> 執行緒上進行回呼，且完全不會使用此事件模型。  它也會將狀態物件提供給回呼方法，而其他計時器則不會；  它是極為輕量的。  
  
 下列程式碼範例會啟動一個在一秒鐘 \(1000 毫秒\) 之後啟動的計時器，並在每一秒鐘滴答地記錄，直到按下 \[**Enter**\] 鍵為止。  包含計時器的參考之變數為類別層級的欄位，用以確保計時器仍在執行中時不受記憶體回收的控制。  如需積極型記憶體回收的詳細資訊，請參閱 <xref:System.GC.KeepAlive%2A>。  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## 請參閱  
 <xref:System.Threading.Timer>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)