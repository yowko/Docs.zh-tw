---
title: "contextSwitchDeadlock MDA | Microsoft Docs"
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
  - "deadlocks [.NET Framework]"
  - "pumping messages"
  - "STA message pumping"
  - "single-threaded COM components"
  - "MDAs (managed debugging assistants), context switching deadlocks"
  - "managed debugging assistants (MDAs), context switching deadlocks"
  - "ContextSwitchDeadlock MDA"
  - "message pumping"
  - "context switching deadlocks"
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: 22
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 22
---
# contextSwitchDeadlock MDA
試圖進行 COM 內容轉換期間，偵測到死結時，會啟用 `contextSwitchDeadlock` Managed 偵錯助理 \(MDA\)。  
  
## 徵兆  
 最常見的徵兆是，在 Unmanaged COM 元件上從 Managed 程式碼進行的呼叫未傳回。  另一個徵兆是記憶體使用量隨著時間增加。  
  
## 原因  
 最有可能的原因是，單一執行緒 Apartment \(STA\) 執行緒沒有提取訊息。  STA 執行緒可能正在等待而沒有提取訊息，或是正在執行長時間作業，不允許訊息佇列提取。  
  
 記憶體使用量隨著時間增加的原因，是因為完成項執行緒試圖在 Unmanaged COM 元件上呼叫 `Release`，而該元件未傳回。  這會導致完成項無法回收其他物件。  
  
 根據預設，Visual Basic 主控台應用程式主要執行緒的執行緒模型為 STA。  如果 STA 執行緒直接或間接透過通用語言執行平台或協力廠商控制項來使用 COM 互通性，就會啟用此 MDA。  若要避免在 Visual Basic 主控台應用程式中啟用此 MDA，請將 <xref:System.MTAThreadAttribute> 屬性套用至 Main 方法，或修改應用程式來提取訊問。  
  
 在符合下列所有條件的情況下，有可能會錯誤地啟用此 MDA：  
  
-   應用程式直接或間接透過程式庫，從 STA 執行緒建立 COM 元件。  
  
-   已在偵錯工具中停止應用程式，而使用者繼續應用程式，或執行步驟作業。  
  
-   未啟用 Unmanaged 偵錯。  
  
 若要判斷是否錯誤地啟用 MDA，請停用所有中斷點、重新啟動應用程式，並且讓它不間斷地執行。  如果未啟用 MDA，則可能初始啟用時發生錯誤。  若是如此，請停用 MDA，以避免阻礙偵錯工作階段。  
  
> [!NOTE]
>  此 MDA 在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 及較新版本的預設集中。  當 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中啟用裝載處理序時，您無法停用預設集中的 MDA。  預設會啟用裝載處理序，所以必須明確將其停用。  如需如何停用 MDA 的相關資訊，請參閱[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)中的＜啟用和停用 MDA＞。  
  
## 解決方式  
 遵循有關 STA 訊息幫浦的 COM 規則。  
  
## 對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  它只會提報 COM 內容的相關資料。  
  
## 輸出  
 描述目前內容和目標內容的訊息。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)