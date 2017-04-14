---
title: "Foreground and Background Threads | Microsoft Docs"
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
  - "threading [.NET Framework], foreground"
  - "threading [.NET Framework], background"
  - "foreground threads"
  - "background threads"
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Foreground and Background Threads
Managed 執行緒如果不是背景執行緒，就是前景執行緒。  背景執行緒與前景執行緒完全一樣，只有一項例外，就是背景執行緒不會將 Managed 執行環境維持在執行狀態。  一旦已在 Managed 處理序 \(其中 .exe 檔案是 Managed 組譯碼\) 中停止所有前景執行緒，則系統會停止所有的背景執行緒並結束。  
  
> [!NOTE]
>  當處理序關閉而造成執行階段停止背景執行緒時，執行緒中不會擲回任何例外狀況。  不過，當 <xref:System.AppDomain.Unload%2A?displayProperty=fullName> 方法卸載應用程式定義域而造成執行緒停止時，前景執行緒和背景執行緒中都會擲回 <xref:System.Threading.ThreadAbortException>。  
  
 請使用 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName> 屬性來判斷某個執行緒是背景執行緒或前景執行緒，或者變更它的狀態。  經由將執行緒的 <xref:System.Threading.Thread.IsBackground%2A> 屬性設定為 `true`，您隨時都可以將它變更為背景執行緒。  
  
> [!IMPORTANT]
>  執行緒的前景或背景狀態並不會影響執行緒中未處理之例外狀況的結果。  在 .NET Framework 2.0 版中，前景或背景執行緒中的未處理例外狀況會造成應用程式終止。  請參閱 [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md)。  
  
 屬於 Managed 執行緒集區中的執行緒 \(亦即，其 <xref:System.Threading.Thread.IsThreadPoolThread%2A> 屬性為 `true` 的執行緒\) 是背景執行緒。  從 Unmanaged 程式碼進入 Managed 執行環境的所有執行緒均會被標記為背景執行緒。  藉由建立及啟動新 <xref:System.Threading.Thread> 物件所產生的所有執行緒預設都是前景執行緒。  
  
 如果您使用執行緒來監視某個活動 \(例如通訊端連接\)，請將它的 <xref:System.Threading.Thread.IsBackground%2A> 屬性設為 `true`，這樣執行緒就不會阻止處理序終止。  
  
## 請參閱  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName>   
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadAbortException>