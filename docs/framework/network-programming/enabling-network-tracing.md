---
title: "啟用網路追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "追蹤目的地"
  - "傳送追蹤給記錄檔"
  - "追蹤接聽程式，網路追蹤"
  - "網路追蹤，啟用"
  - "CLR 偵錯工具"
  - "預設接聽程式"
  - "記錄檔，追蹤"
  - "追蹤輸出的目的地"
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# 啟用網路追蹤
網路追蹤提供的相關資訊。方法引動和 Managed 應用程式產生的網路流量。  您必須完成下列工作在應用程式中啟用網路追蹤:  
  
-   編譯以啟用追蹤的程式碼。  請參閱 [How to: Compile Conditionally with Trace and Debug](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) 與所要求之編譯器選項的詳細資訊啟用追蹤。  
  
-   用於追蹤輸出指定目的端。  
  
-   設定網路追蹤行為。  如需詳細資訊請參閱 [HOW TO:設定網路追蹤](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) 。  
  
 最常見的追蹤目的端，也稱為追蹤接聽項，是預設接聽項和記錄檔。  
  
 如果您未指定追蹤接聽程式，使用預設追蹤接聽項。  您可以使用 .NET Framework SDK 檢視傳送至預設接聽程式會執行您在一個 Managed 程式碼啟用偵錯工具中執行程式碼 \(例如傳輸的 CLR 偵錯工具或 DBwin32.exe 隨附於 Windows SDK。  使用 CLR 偵錯工具，追蹤訊息便會出現 **輸出** 視窗。  
  
 如果您想要使用檔案接收追蹤，以便使用組態設定，如下列範例所示，您可以指定記錄檔。  \(如需組態檔的一般性討論，請參閱 [組態檔](../../../docs/framework/configure-apps/index.md)\)。  
  
 若要傳送至追蹤記錄檔中，加入下列節點加入至適當的組態檔的 `<system.diagnostics>` 節點 \(應用程式或電腦\)。  您可以將檔案 \(trace.log\) 的名稱符合您的需求。  
  
```  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## 請參閱  
 [解譯網路追蹤](../../../docs/framework/network-programming/interpreting-network-tracing.md)   
 [以 .NET Framework 進行網路追蹤](../../../docs/framework/network-programming/network-tracing.md)   
 [Introduction to Instrumentation and Tracing](http://msdn.microsoft.com/zh-tw/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)