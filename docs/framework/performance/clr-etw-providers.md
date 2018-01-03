---
title: "CLR ETW 提供者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b76b3a1d4969a5ed81e5fa90afb06050b780804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clr-etw-providers"></a>CLR ETW 提供者
Common Language Runtime (CLR) 有兩個提供者：執行階段提供者和取消提供者。  
  
 執行階段提供者會根據啟用哪些關鍵字 (事件的類別) 來引發事件。 例如，您可以啟用 `LoaderKeyword` 關鍵字來收集載入器事件。  
  
 Windows (ETW) 事件的事件追蹤會記錄至副檔名為 .etl 的檔案，稍後可視需要在逗號分隔值 (.csv) 檔案中後置處理。 如需如何將 .etl 檔案轉換成 .csv 檔案的資訊，請參閱[控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)。  
  
## <a name="the-runtime-provider"></a>執行階段提供者  
 執行階段提供者是主要 CLR ETW 提供者。  
  
 CLR 執行階段提供者 GUID 是 e13c0d23-ccbc-4e12-931b-d9cc2eee27e4。  
  
 如需如何使用常用工具來記錄和檢視 CLR ETW 事件的範例，請參閱[控制 .NET Framework 記錄](../../../docs/framework/performance/controlling-logging.md)。  
  
 除了使用 `LoaderKeyword` 這類關鍵字之外，您可能還需要啟用關鍵字來記錄可能太頻繁引發的事件。 `StartEnumerationKeyword` 和 `EndEnumerationKeyword` 關鍵字會啟用這些事件，[CLR ETW 關鍵字和層級](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)中會有摘要說明。  
  
## <a name="the-rundown-provider"></a>取消提供者  
 針對某些特殊用途，必須開啟取消提供者。 不過，對大部分的使用者而言，執行階段提供者應該就已足夠。  
  
 CLR 取消提供者 GUID 是 A669021C-C450-4609-A035-5AF59AF4DF18。  
  
 一般來說，會在啟動處理序之前啟用 ETW 記錄，並在處理序結束之後關閉記錄。 不過，如果在處理序執行時開啟 ETW 記錄，則需要處理序的額外資訊。 例如，進行符號解析時，您必須針對已在開啟記錄之前載入的方法，來記錄方法事件。  
  
 `DCStart` 和 `DCEnd` 事件會擷取啟動和停止資料收集時的處理序狀態 (狀態是指高階資訊，包含已進行 Just-In-Time (JIT) 編譯的方法，以及已載入的組件)。這兩個事件都可以提供處理序中發生情況的相關資訊；例如，哪些方法已進行 JIT 編譯，依此類推。  
  
 在取消提供者下，只會引發其名稱含有 `DC`、`DCStart`、`DCEnd` 或 `DCInit` 的事件。 此外，只會在取消提供者下引發這些事件。  
  
 除了事件關鍵字篩選之外，取消提供者也支援 `StartRundownKeyword` 和 `EndRundownKeyword` 關鍵字，以提供目標篩選。  
  
### <a name="start-rundown"></a>開始取消  
 使用 `StartRundownKeyword` 關鍵字啟用取消提供者下的記錄時，會觸發開始取消。 這會引發 `DCStart` 事件，並擷取系統的狀態。 開始列舉之前，會引發 `DCStartInit` 事件。 列舉結束時，會引發 `DCStartComplete` 事件，以通知控制器資料收集已正常終止。  
  
### <a name="end-rundown"></a>結束取消  
 使用 `EndRundownKeyword` 關鍵字啟用取消提供者下的記錄時，會觸發結束取消。 結束取消會停止對繼續執行之處理序的分析。 `DCEnd` 事件會擷取停止分析時的系統狀態。  
  
 開始列舉之前，會引發 `DCEndInit` 事件。 列舉結束時，會引發 `DCEndComplete` 事件，以通知消費者資料收集已正常終止。 開始取消和結束取消主要用於 Managed 符號解析。 開始取消可以提供已在啟動分析工作階段之前進行 JIT 編譯之方法的位址範圍資訊。 結束取消可以提供已在即將關閉分析時進行 JIT 編譯之所有方法的位址範圍資訊。  
  
 停止分析工作階段時，不會自動發生結束取消。 相反地，就在停止分析之前，嘗試執行 Managed 符號解析的工具必須在啟用 `EndRundownKeyword` 關鍵字的情況下明確地叫用 CLR 取消提供者工作階段。  
  
 雖然開始取消或結束取消可以提供 Managed 符號解析的方法位址範圍資訊，但是建議您使用 `EndRundownKeyword` 關鍵字 (其提供 `DCEnd` 事件)，而非 `StartRundownKeyword` 關鍵字 (其提供 `DCStart` 事件)。 使用 `StartRundownKeyword` 可在分析工作階段期間發生取消，而這可能會干擾分析的案例。  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a>使用執行階段和取消提供者的 ETW 資料收集  
 下列範例示範如何使用 CLR 取消提供者，而方式是允許 Managed 處理序的符號解析，並且影響最少，而且不論處理序是在分析的時間範圍內部或外部開始或結束。  
  
1.  使用 CLR 執行階段提供者開啟 ETW 記錄：  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     記錄會儲存至 clr1.etl 檔案。  
  
2.  若要在處理序繼續執行時停止分析，請啟動取消提供者來擷取 `DCEnd` 事件：  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     這會啟用 `DCEnd` 事件的收集來啟動取消工作階段。 您可能需要等待 30 到 60 秒的時間，以收集所有事件。 記錄會儲存至 clr1.et2 檔案。  
  
3.  關閉所有 ETW 分析：  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  合併設定檔以建立一個記錄檔：  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     merged.etl 檔案將包含來自執行階段和取消提供者工作階段的事件。  
  
 工具可以執行步驟 2 和 3 (啟動取消工作階段，然後終止分析)，而不是在使用者要求停止分析時立即關閉分析。 工具也可以執行步驟 4。  
  
## <a name="see-also"></a>請參閱  
 [Common Language Runtime 中的 ETW 事件](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
