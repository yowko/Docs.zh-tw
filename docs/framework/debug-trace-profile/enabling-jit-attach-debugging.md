---
title: "Enabling JIT-Attach Debugging | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "JIT-attach debugging"
  - "debugging [.NET Framework], JIT-attach debugging"
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Enabling JIT-Attach Debugging
JIT 附加偵錯一詞是指在發生錯誤 \(或由特定方法或函式觸發\) 時將偵錯工具附加至處理序的動作。  
  
 JIT 附加偵錯的使用時機是在遇到下列錯誤狀況時：  
  
-   未處理的例外狀況 \(原生程式碼和 Managed 程式碼中的都算\)。  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=fullName> 方法或 [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) 函式 \(Windows 7 系列\)。  
  
-   執行階段嚴重錯誤。  
  
 呼叫下列方法或函式也會觸發 JIT 附加偵錯：  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=fullName> 方法呼叫的。  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=fullName> 方法呼叫的。  
  
-   [DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) 函式 \(Win32\)。  
  
 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]之前，.NET Framework 分開提供登錄機碼來控制原生偵錯工具和 Managed 偵錯工具的行為。  自 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，上述控制已合併至單一登錄機碼下：HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\Current Version\\AeDebug。  您可在該機碼設定的值會決定是否叫用偵錯工具，以及若要叫用，是否以需要使用者互動的對話方塊叫用偵錯工具。  如需設定這個登錄機碼的詳細資訊，請參閱 MSDN Library 中 [設定自動偵錯](http://go.microsoft.com/fwlink/?LinkId=181767) 。  
  
## 請參閱  
 [Debugging, Tracing, and Profiling](../../../docs/framework/debug-trace-profile/index.md)   
 [使映像偵錯更容易](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)   
 [Enabling Profiling](http://msdn.microsoft.com/zh-tw/3b669676-f0e0-4ebf-8674-68986dd2020d)