---
title: "Scheduling Threads | Microsoft Docs"
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
  - "threading [.NET Framework], scheduling"
  - "scheduling threads"
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Scheduling Threads
所有的執行緒都具有指派給它的執行緒優先權。  在 Common Language Runtime 中建立的執行緒一開始會被指派 **ThreadPriority.Normal** 優先權。  在執行階段以外建立的執行緒則會保留在進入 Managed 環境之前原本的優先權。  您可使用 **Thread.Priority** 屬性來取得或設定任何執行緒的優先權。  
  
 執行緒是根據優先權來排程執行的。  雖然執行緒都是在執行階段內執行，但是作業系統會指派所有執行緒的處理器劃分使用時段。  用來決定執行緒執行順序的排程演算法詳細資訊因作業系統而異。  在某些作業系統下，一定會排程先執行具有最高優先權的執行緒 \(屬於可執行的執行緒\)。  如果具有相同優先權的執行緒均可使用，則排程器會以該優先權循環整個執行緒，並授與每個執行緒執行的固定劃分使用時段。  只要具有較高優先權的執行緒可以執行時，則不會執行較低優先權的執行緒。  當指定的優先權沒有可執行的執行緒時，排程器會移至下一個較低優先權，並以該優先權排程要執行的執行緒。  如果較高優先權的執行緒成為可執行時，則會優先執行較低優先權的執行緒，並允許再次執行較高優先權的執行緒。  最重要的是，當在前景與背景之間移動應用程式使用者介面時，作業系統也可動態調整執行緒優先權。  其他的作業系統可選擇使用不同的排程演算法。  
  
## 請參閱  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)   
 [Managed and Unmanaged Threading in Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)