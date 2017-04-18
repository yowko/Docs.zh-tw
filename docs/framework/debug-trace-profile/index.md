---
title: "Debugging, Tracing, and Profiling | Microsoft Docs"
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
  - "debugging [.NET Framework]"
  - ".NET Framework application configuration, debugging"
  - "debugging [.NET Framework], .NET Framework application debugging"
  - "troubleshooting applications [.NET Framework], profiling"
  - "application development [.NET Framework], debugging"
  - ".NET Framework application configuration, profiling"
  - "profiling applications"
  - "troubleshooting applications [.NET Framework], debugging"
  - "troubleshooting applications [.NET Framework]"
  - "application development [.NET Framework], profiling"
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
caps.latest.revision: 28
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 28
---
# Debugging, Tracing, and Profiling
若要偵錯 .NET Framework 應用程式，必須設定編譯器和執行階段環境，讓偵錯工具能夠附加至應用程式，並針對應用程式及其相對應的 Microsoft 中繼語言 \(MSIL\) 產生符號和字行對應 \(可能的話\)。  在偵錯 Managed 應用程式後，可將其剖析以提高效能。  程式碼剖析會評估和描述產生最常執行之程式碼的原始程式碼字行，以及花費多少時間執行。  
  
 使用 Visual Studio 可輕易偵錯 .NET Framework 應用程式，它會處理許多組態詳細資料。  如果未安裝 Visual Studio，您可以使用 .NET Framework <xref:System.Diagnostics> 命名空間中的偵錯類別，來檢查並改善 .NET Framework 應用程式的效能。  此命名空間包含用來追蹤執行流程的 <xref:System.Diagnostics.Trace><xref:System.Diagnostics.Debug> 和 <xref:System.Diagnostics.TraceSource> 類別，以及用來剖析程式碼的 <xref:System.Diagnostics.Process>、<xref:System.Diagnostics.EventLog> 和 <xref:System.Diagnostics.PerformanceCounter> 類別。  
  
## 在本節中  
 [Enabling JIT\-Attach Debugging](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 示範如何設定登錄，以將偵錯引擎 JIT 附加至 .NET Framework 應用程式。  
  
 [使映像偵錯更容易](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 示範如何開啟 JIT 追蹤並關閉最佳化，使組件偵錯更容易。  
  
 [Tracing and Instrumenting Applications](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 描述當應用程式執行時，如何監視其執行狀況，以及如何加以檢測，以顯示其執行效能如何，或是否有哪裡發生錯誤。  
  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 描述 Managed 偵錯助理 \(MDA\)，其為偵錯輔助程式，可與 Common Language Runtime \(CLR\) 合作提供執行階段狀態的相關資訊。  
  
 [Enhancing Debugging with the Debugger Display Attributes](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 描述類型的開發人員要如何指定當類型顯示在偵錯工具中時，看起來是什麼樣子。  
  
 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 描述您可以用來追蹤應用程式效能的計數器。  
  
## 相關章節  
 [偵錯 ASP.NET 和 AJAX 應用程式](../Topic/Debugging%20ASP.NET%20and%20AJAX%20Applications.md)  
 提供如何在開發期間或部署之後偵錯 ASP.NET 應用程式的先決條件與指示。  
  
 [開發指南](../../../docs/framework/development-guide.md)  
 提供應用程式開發所有主要技術領域和工作的指引，包括建立、設定、偵錯、保護及部署您的應用程式，以及有關動態程式設計、互通性、擴充性、記憶體管理和執行緒的資訊。