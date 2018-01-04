---
title: "活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70471705-f55f-4da1-919f-4b580f172665
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbcf33aa734cde1d2458e46cd161f9ea5197a827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="activity"></a>活動
本主題描述 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 追蹤模型中的活動追蹤。 活動指的是協助使用者縮小失敗範圍的處理單位。 發生在同一個活動中的錯誤都是直接相關的。 例如，因為訊息解密失敗而導致作業失敗。 作業與訊息解密失敗的追蹤會同時出現在同一個活動中，顯示解密錯誤與要求錯誤之間直接的相互關聯性。  
  
## <a name="configuring-activity-tracing"></a>設定活動追蹤  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]提供預先定義的活動以處理應用程式 (請參閱[活動清單](../../../../../docs/framework/wcf/diagnostics/tracing/activity-list.md))。 您也可以使用程式設計方式來定義活動，以便將使用者追蹤加以群組。 如需詳細資訊，請參閱[發出使用者程式碼追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)。  
  
 若要在執行階段發出活動追蹤，則針對 `ActivityTracing` 追蹤來源，或其他 `System.ServiceModel` 或自訂追蹤來源，請使用 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 設定，如下列組態程式碼所示。  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
 若要了解有關的組態項目和屬性所使用的詳細資訊，請參閱[設定追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)主題。  
  
## <a name="viewing-activities"></a>檢視活動  
 您可以檢視的活動和其公用程式中的[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。 啟用 ActivityTracing 時，此工具會取得追蹤並依據活動加以排序。 您也可以看見追蹤傳輸的情況。 追蹤傳輸表示不同活動之間彼此的關係。 您可以看到特定活動導致另一個活動啟動。 例如，訊息要求啟動了安全性交換來取得安全對話權杖。  
  
### <a name="correlating-activities-in-service-trace-viewer"></a>透過服務追蹤檢視器來關聯活動  
 服務追蹤檢視器工具提供兩種活動檢視：  
  
-   **清單**檢視，其中的活動識別碼會用來直接與追蹤相互關聯跨處理序。 來自不同處理序 (例如用戶端與服務) 但具有相同活動 ID 的追蹤，會群組成相同的活動。 因此，發生在服務上的錯誤並進而導致用戶端的錯誤，兩者將同時顯示在工具的相同活動檢視中。  
  
-   **圖形**檢視的活動在處理序所組成。 在此檢視中，具有相同活動識別碼的用戶端與服務在不同的活動中都有自己的追蹤。 若要在不同的處理序當中以相同的活動識別碼來關聯活動，工具會顯示相關活動之間的訊息流程。  
  
 如需詳細資訊，以及查看服務追蹤檢視器工具的圖形化檢視，請參閱[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)和[使用服務追蹤檢視器檢視相關追蹤並疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)。  
  
## <a name="defining-the-scope-of-an-activity"></a>定義活動範圍  
 活動係於設計階段定義，代表工作的邏輯單位。 發出的追蹤 (具有相同的活動識別項) 是直接相關的，因為它們隸屬於相同的活動。 由於活動可以跨越端點界限 (要求)，因此會定義兩個活動範圍。  
  
-   每個應用程式的 `Global` 範圍。 在此範圍中，活動是由本身的 128 位元全域唯一活動識別項 (亦即 gAId) 所識別。 在端點之間傳播的識別項就是 gAid。  
  
-   每個端點的 `Local` 範圍。 在此範圍中，活動是由本身的 gAId，加上發出活動追蹤與處理序識別碼的追蹤來源名稱所識別。此三項一體構成了本地活動識別碼，亦即 lAId。 lAId 可用來定義活動的 (本地) 界限。  
  
## <a name="trace-schema"></a>追蹤結構描述  
 您可以使用任何結構描述並跨各種 Microsoft 平台來發出追蹤。 "e2e"（代表 「 端對端 」） 是常用的結構描述。 這個結構描述包含 128 位元的識別項 (gAId)、追蹤來源名稱與處理序識別碼。 在 Managed 程式碼中，<xref:System.Diagnostics.XmlWriterTraceListener> 會在 E2E 結構描述中發出追蹤。  
  
 開發人員可以使用執行緒區域儲存區 (TLS) 上的 GUID 來設定 <xref:System.Diagnostics.CorrelationManager.ActivityId%2A> 屬性，藉此設定使用追蹤來發出的 AID。 下列範例為其示範。  
  
```  
// set the current Activity ID to a new GUID.  
CorrelationManager.ActivityId = Guid.NewGuid();  
```  
  
 當追蹤透過追蹤來源發出時，很明顯便能看出已在 TLS 中設定 gAId，如下列範例所示。  
  
```  
TraceSource traceSource = new TraceSource("myTraceSource");  
traceSource.TraceEvent(TraceEventType.Warning, eventId, "Information");  
```  
  
 發出的追蹤將包含目前位於 TLS 中的 gAId、將追蹤來源名稱當成參數傳遞至追蹤來源的建構函式，以及目前處理序 ID。  
  
## <a name="activity-lifetime"></a>活動存留期  
 嚴格地說，活動證據會在發出的追蹤第一次使用活動識別碼時開始，並於最後一次使用活動識別碼時停止。 <xref:System.Diagnostics> 會提供預先定義的追蹤類型組合，包括「開始」與「停止」，以明確標記活動的存留期界限。  
  
-   開始：表示活動的開頭。 「 開始 」 追蹤會提供開始新的處理里程碑的記錄。 它包含特定處理序中所指定之追蹤來源的全新活動識別碼 (除非活動識別碼已傳播至各端點，我們才會在每個端點看到一個「開始」)。 開始新活動的範例包括建立新的執行緒以供處理，或是輸入新的公用方法。  
  
-   停止：表示活動的結尾。 「 停止 」 追蹤會提供結束現有處理里程碑的記錄。 它包含特定處理序中所指定之追蹤來源的現有活動識別碼，除非活動識別碼已傳播至各端點時，我們才會在每個端點看到一個「停止」。  停止活動的範例包括結束處理執行緒，或結束的方法，其開頭已加註 「 開始 」 追蹤。  
  
-   暫停：表示活動處理暫停。 「 暫停 」 追蹤包含現有的活動識別碼，其處理必須在稍後繼續進行。 在「暫停」與「繼續」事件之間，不會從目前的追蹤來源使用此識別碼發出任何追蹤。 範例包括呼叫外部程式庫函式，或等候 I/O 完成連接埠等資源時暫停活動。  
  
-   繼續：表示繼續處理活動。 「 繼續 」 追蹤包含現有的活動識別碼，從目前的追蹤來源的最後一個發出的追蹤是 「 暫停 」 追蹤。 範例包括從呼叫外部程式庫函式返回，或是 I/O 完成連接埠等資源表示繼續處理時返回。  
  
-   傳輸： 由於某些活動其他人所造成，或與其他類別相關，活動可以是其他活動相關透過 「 傳輸 」 追蹤。 傳輸會記錄活動之間的導向關係  
  
 「開始」與「停止」追蹤對相互關聯並不重要。 然而，這兩項追蹤有助於提升效能、進行分析，以及驗證活動範圍。  
  
 透過這些類型，工具可以最佳化追蹤記錄的瀏覽工作，以找到與相同活動立即相關的事件，或是相關活動中的事件 (如果工具遵循傳輸追蹤的話)。 例如，當工具看到「開始」與「停止」追蹤時，就會針對特定活動停止剖析記錄。  
  
 這些追蹤類型也可用來進行分析。 開始與停止資料標記之間所使用的資源代表活動的內含時間 (包括內含的邏輯活動)。 減去「暫停」與「繼續」追蹤之間的時間間隔便能提供實際的活動時間。  
  
 「停止」追蹤也很適合用來驗證已實作之活動的範圍。 如果某些處理中的追蹤在「停止」追蹤之後出現，而不是在特定活動中出現，表示可能出現程式碼缺失。  
  
## <a name="guidelines-for-using-activity-tracing"></a>使用活動追蹤的方針  
 下列為使用 ActivityTracing 追蹤 (開始、停止、暫停、繼續與傳輸) 的方針。  
  
-   追蹤是直接循環的圖形，而不是樹狀結構。 您可以將控制項傳回已繁衍 (Spawn) 活動的活動。  
  
-   活動代表處理界限，這對系統管理員或支援能力而言十分重要。  
  
-   每個 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 方法 (不管在用戶端或伺服器上) 的界限都是由開始新的活動，並在完成工作之後結束新活動，最後返回環境活動來加以界定。  
  
-   例如，接聽連線或等候訊息的長時間 (持續) 活動，將以相對應的開始/停止資料標記來表示。  
  
-   因為接收或處理訊息而觸發的活動將由追蹤介面來表示。  
  
-   活動就是代表活動，但不一定代表物件。 活動應該解譯為 「 它的發生時。 。 。 (已發出有意義的追蹤)」。  
  
## <a name="see-also"></a>請參閱  
 [設定追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [端對端追蹤案例](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [發出使用者程式碼追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/emitting-user-code-traces.md)
