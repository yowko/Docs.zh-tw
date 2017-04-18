---
title: "Thread.Suspend, Garbage Collection, and Safe Points | Microsoft Docs"
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
  - "suspending threads"
  - "safe points"
  - "threading [.NET Framework], suspending"
  - "threading [.NET Framework], garbage collection"
  - "garbage collection, threads"
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Thread.Suspend, Garbage Collection, and Safe Points
當您在執行緒上呼叫 <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> 時，系統會注意到出現暫止執行緒的要求，並且會讓執行緒繼續執行，直到執行緒到達安全點之後才會實際暫止執行緒。  執行緒的安全點就是在它執行時可以進行記憶體回收的點。  
  
 一旦到達安全點，Runtime 會保證已暫止的執行緒不會在 Managed 程式碼中繼續進行。  在 Managed 程式碼之外執行的執行緒永遠可安全地進行記憶體回收，並且會持續進行，直到執行緒嘗試繼續執行 Managed 程式碼。  
  
> [!NOTE]
>  為執行記憶體回收，執行階段必須暫止所有執行緒 \(除了執行回收的執行緒之外\)。  每個執行緒都必須達到安全點後才能暫止。  
  
## 請參閱  
 <xref:System.Threading.Thread>   
 <xref:System.GC>   
 [Threading](../../../docs/standard/threading/index.md)   
 [自動記憶體管理](../../../docs/standard/automatic-memory-management.md)