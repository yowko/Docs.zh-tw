---
title: "CLR ETW 提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CLR ETW 提供者"
  - "ETW, CLR 提供者"
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# CLR ETW 提供者
Common Language Runtime \(CLR\) 具有兩個提供者：執行階段提供者和取消提供者。  
  
 執行階段提供者會根據啟用的關鍵字 \(即事件的分類\) 引發事件。  例如，您可以透過啟用 `LoaderKeyword` 關鍵字，收集載入器事件。  
  
 Windows 事件追蹤 \(ETW\) 事件會記錄在副檔名為 .etl 的檔案中，之後您就可以視需要在逗點分隔值 \(.csv\) 檔案中進行後置處理。  如需如何將 .etl 檔案轉換為 .csv 檔案的詳細資訊，請參閱[控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)。  
  
## 執行階段提供者  
 執行階段提供者是主要的 CLR ETW 提供者。  
  
 CLR 執行階段提供者 GUID 為 e13c0d23\-ccbc\-4e12\-931b\-d9cc2eee27e4。  
  
 如需如何使用常用工具來記錄和檢視 CLR ETW 事件的範例，請參閱[控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)。  
  
 除了使用 `LoaderKeyword` 之類的關鍵字以外，您可能還必須啟用關鍵字來記錄極常引發的特定事件。  `StartEnumerationKeyword` 和 `EndEnumerationKeyword` 的關鍵字會啟用這些事件，在[CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)中有摘要說明  
  
## 取消提供者  
 就某些特殊用途而言，您必須開啟取消提供者。  不過，對於大多數使用者而言，有執行階段提供者應該就已足夠。  
  
 CLR 取消提供者 GUID 為 A669021C\-C450\-4609\-A035\-5AF59AF4DF18。  
  
 一般而言，ETW 記錄會在處理序啟動之前啟用，而在處理序結束之後關閉。  不過，如果 ETW 記錄在處理序執行時開啟，就需要處理序的相關額外資訊。  例如，若要進行符號解析，您必須針對在記錄開啟之前就已載入的方法，記錄方法事件。  
  
 `DCStart` 和 `DCEnd` 事件會在資料收集開始和停止時擷取處理序的狀態 \(狀態是指高階資訊，包括已經完成 Just\-In\-Time \(JIT\) 編譯的方法及已經載入的組件\)。這兩個事件可以提供已經發生在處理序中之事件的相關資訊。例如，哪些方法已完成 JIT 編譯等等。  
  
 只有名稱包含 `DC`、`DCStart`、`DCEnd` 或 `DCInit` 的事件會在取消提供者底下引發。  此外，這些事件只會在取消提供者底下引發。  
  
 除了事件關鍵字篩選以外，取消提供者也支援 `StartRundownKeyword` 和 `EndRundownKeyword` 關鍵字來提供目標式篩選。  
  
### 開始取消  
 使用 `StartRundownKeyword` 關鍵字來啟用取消提供者底下的記錄時，就會觸發開始取消。  這會導致系統引發 `DCStart` 事件，並且擷取系統的狀態。  在列舉開始之前，就會引發 `DCStartInit` 事件。  在列舉結束時，則會引發 `DCStartComplete` 事件，以便向控制器通知資料收集已正常終止。  
  
### 結束取消  
 使用 `EndRundownKeyword` 關鍵字來啟用取消提供者底下的記錄時，就會觸發結束取消。  結束取消會停止在繼續執行的處理序上進行程式碼剖析。  當程式碼剖析已停止時，`DCEnd` 事件會擷取系統的狀態。  
  
 在列舉開始之前，就會引發 `DCEndInit` 事件。  在列舉結束時，則會引發 `DCEndComplete` 事件，以便向消費者通知資料收集已正常終止。  開始取消和結束取消主要用於 Managed 符號解析。  在程式碼剖析工作階段啟動之前，開始取消可以針對已經完成 JIT 編譯的方法提供位址範圍資訊。  當程式碼剖析即將關閉時，結束取消可以針對已經完成 JIT 編譯之所有方法提供位址範圍資訊。  
  
 當程式碼剖析工作階段停止時，結束取消不會自動進行。  而是，嘗試執行 Managed 符號解析的工具必須在程式碼剖析停止之前，明確叫用 CLR 取消提供者工作階段並啟用 `EndRundownKeyword` 關鍵字。  
  
 雖然開始取消或結束取消可以提供 Managed 符號解析的方法位址範圍資訊，不過我們建議您使用 `EndRundownKeyword` 關鍵字 \(可提供 `DCEnd` 事件\) 而非 `StartRundownKeyword` 關鍵字 \(可提供 `DCStart` 事件\)。  使用 `StartRundownKeyword` 會導致取消在程式碼剖析工作階段期間進行，因而可能會干擾程式碼剖析案例。  
  
## 使用執行階段和取消提供者的 ETW 資料收集  
 下列範例將示範如何使用 CLR 取消提供者，以便在影響最小的情況下針對 Managed 處理序進行符號解析，不論處理序是在程式碼剖析視窗內部或外部開始或結束都一樣。  
  
1.  使用 CLR 執行階段提供者來開啟 ETW 記錄：  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     記錄檔將會儲存至 clr1.etl 檔案。  
  
2.  若要在處理序繼續執行時停止程式碼剖析，請啟動取消提供者來擷取 `DCEnd` 事件：  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     這樣做就會收集 `DCEnd` 事件，以便啟動取消工作階段。  您可能必須等候 30 至 60 秒，才能收集所有事件。  記錄將會儲存至 clr1.et2 檔案。  
  
3.  關閉所有 ETW 程式碼剖析：  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  合併這些設定檔以建立單一記錄檔：  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     此 merged.etl 檔案將包含來自執行階段和取消提供者工作階段的事件。  
  
 當使用者要求停止程式碼剖析時，工具可以執行步驟 2 和 3 \(啟動取消工作階段，然後終止程式碼剖析\)，而非立即關閉程式碼剖析。  工具也可以執行步驟 4。  
  
## 請參閱  
 [Common Language Runtime 中的 ETW 事件](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)