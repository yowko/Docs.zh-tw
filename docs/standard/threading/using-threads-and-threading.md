---
title: "Using Threads and Threading | Microsoft Docs"
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
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Using Threads and Threading
本章節中的主題會討論 Managed 執行緒的建立和管理、如何將資料傳遞給 Managed 執行緒及取回結果，以及如何部署執行緒及處理 <xref:System.Threading.ThreadAbortException>。  
  
## 在本節中  
 [Creating Threads and Passing Data at Start Time](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 討論及示範如何建立 Managed 執行緒，其中包括如何將資料傳遞給新的執行緒以及如何取回資料。  
  
 [Pausing and Resuming Threads](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 討論暫止和繼續 Managed 執行緒的細節。  
  
 [Destroying Threads](../../../docs/standard/threading/destroying-threads.md)  
 討論損毀 Managed 執行緒的細節以及如何處理 <xref:System.Threading.ThreadAbortException>。  
  
 [Scheduling Threads](../../../docs/standard/threading/scheduling-threads.md)  
 討論執行緒優先權以及其對執行緒排程的影響。  
  
## 參考  
 <xref:System.Threading.Thread>  
 提供 <xref:System.Threading.Thread> 類別的參考文件，無論是來自於 Unmanaged 程式碼的執行緒，或是在 Managed 應用程式中建立的執行緒，都代表 Managed 執行緒。  
  
 <xref:System.Threading.ThreadStart>  
 為表示無參數之執行緒程序的 <xref:System.Threading.ThreadStart> 委派提供參考文件。  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 提供一個簡單的方法將資料傳遞給執行緒程序 \(即使是沒有強型別\)。  
  
## 相關章節  
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)  
 提供 Managed 執行緒處理的簡介。