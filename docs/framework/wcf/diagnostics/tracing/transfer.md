---
title: "傳輸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83bb76cc46d72f3d368de20669391c3e7f24a0f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transfer"></a>傳輸
這個主題會描述 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 活動追蹤模型中的傳輸。  
  
## <a name="transfer-definition"></a>傳輸定義  
 活動之間的傳輸表示在端點內相關活動中事件之間的因果關係。 當控制在這些活動之間流動時 (例如跨活動界限的方法呼叫)，有兩個活動會與傳輸相關。 在 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 中，當位元組傳入服務時，接聽活動就會傳輸至建立訊息物件之接收位元組活動。 如需端對端追蹤案例，以及其個別活動和追蹤設計的清單，請參閱[端對端追蹤案例](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)。  
  
 若要發出傳輸追蹤，請使用追蹤來源的 `ActivityTracing` 設定，如同下列組態程式碼所示。  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>使用傳輸以相互關聯端點內的活動  
 活動和傳輸都可能讓使用者找到錯誤的根本原因。 例如，如果在元件 M 和 N 中的活動 M 和 N 之間來回傳輸，而在傳輸回 M 之後 N 馬上發生當機，很可能是 N 將資料傳遞回 M 時造成。  
  
 當 M 和 N 之間具有控制流程時，就會從活動 M 將傳輸追蹤發出至活動 N。例如，由於跨活動界限的方法呼叫，N 就會執行 M 的部分工作。 N 可能已存在或已建立。 當 N 是執行 M 之部分工作的新活動時，M 就會繁衍 (Spawn) N。  
  
 從 N 傳輸回 M 之後可能不會從 M 傳輸至 N。這是因為當 N 完成該工作時，M 可以繁衍 N 中的部分工作並且不會進行追蹤。 實際上，M 可以在 N 完成其工作之前就終止。 發生這種情況中的"Open ServiceHost"活動 (M) 會繁衍接聽項活動 (N)，並終止。 從 N 傳輸回 M 表示 N 已完成與 M 相關的工作。  
  
 N 則可以繼續執行其他與 M 不相關的處理，例如持續從不同登入活動接收登入要求 (M) 的現有驗證器活動 (N)。  
  
 在活動 M 和 N 之間不需要有巢狀關係，原因可能有兩個。 第一，當活動 M 在即使 M 初始化 N 的情況下，仍未監視在 N 上執行的實際處理時。第二，當 N 已經存在。  
  
## <a name="example-of-transfers"></a>傳輸範例  
 下列將會列出兩個傳輸範例。  
  
-   當您建立服務主機時，建構函式會從呼叫程式碼中取得控制，或者呼叫程式碼會傳輸至建構函式。 建構函式執行完成時，會將控制權傳回呼叫程式碼，或者建構函式會傳輸回呼叫程式碼。 這就是巢狀關係的情況。  
  
-   接聽項開始處理傳輸資料時，會建立新的執行緒，並將適當的內容交給接收位元組活動，以供處理、傳遞控制和資料。 當執行緒完成處理要求時，接收位元組活動不會將任何資料傳遞回接聽項。 在這個情況下，有資料傳輸進來，但沒有資料從新執行緒活動傳輸出去。 這兩個活動彼此相關，但不是巢狀關係。  
  
## <a name="activity-transfer-sequence"></a>活動傳輸順序  
 格式正確的活動傳輸順序包括下列步驟。  
  
1.  開始新活動，而此活動是由選取新 gAId 所組成。  
  
2.  從目前活動識別碼中，將傳輸追蹤發出至該新 gAId  
  
3.  在 TLS 中設定新識別碼  
  
4.  發出啟動追蹤，以指出新活動的起點。  
  
5.  傳回原始活動則包含下列各項：  
  
6.  將傳輸追蹤發出至原始 gAId  
  
7.  發出停止追蹤以指出新活動的結束  
  
8.  將 TLS 設定為舊 gAId。  
  
 下列程式碼範例會示範如何執行這項操作。 這個範例會假設傳輸至新活動時已產生區塊呼叫，而且其中也包含暫止/繼續追蹤。  
  
```  
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  
// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();   
// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  
// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  
// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  
// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  
// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  
// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);   
// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  
// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  
// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;    
// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>請參閱  
 [設定追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [端對端追蹤案例](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
