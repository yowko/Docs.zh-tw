---
title: "如何：建立和初始化追蹤來源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1fc1e843bb5841fcd5571bb1b57d6fb449336240
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-initialize-trace-sources"></a>如何：建立和初始化追蹤來源
應用程式會使用 <xref:System.Diagnostics.TraceSource> 類別產生能夠與應用程式相關聯的追蹤。 <xref:System.Diagnostics.TraceSource> 提供了追蹤方法，能讓您輕鬆地追蹤事件、追蹤資料和問題資訊追蹤。 不論是否使用組態檔，都可以從 <xref:System.Diagnostics.TraceSource> 建立及初始化追蹤輸出。 本主題提供這兩個選項的指示。 不過，建議您使用組態檔來協助重新設定追蹤來源於執行階段所產生的追蹤。  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a>若要使用組態檔建立及初始化追蹤來源  
  
1.  建立 Visual Studio 主控台應用程式專案，並且將提供的程式碼取代為下列程式碼。 這個程式碼會記錄錯誤和警告，並且將其中一部分輸出至主控台，而另一部分輸出至 myListener 檔 (該檔案是由組態檔中的項目所建立)。  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  將應用程式組態檔加入至專案 (如果專案中尚未存在該檔案)，以初始化步驟 1 的程式碼範例中名為 `TraceSourceApp` 的追蹤來源。  
  
3.  將預設的組態檔內容取代為下列設定，以初始化主控台追蹤接聽程式，以及步驟 1 中所建立追蹤來源的文字寫入器追蹤接聽程式。  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"   
            switchName="sourceSwitch"   
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"   
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"   
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"   
            type="System.Diagnostics.TextWriterTraceListener"   
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     除了設定追蹤接聽程式之外，組態檔也會針對這兩個接聽程式建立篩選條件，並為追蹤來源建立來源參數。 此外，有示範兩個技巧來加入追蹤接聽項：將接聽項直接加入到追蹤來源，並將接聽項加入到共用接聽項集合，然後根據名稱將它加入到追蹤來源。 會使用不同的來源層級來初始化這兩個接聽項所識別的篩選條件， 如此只會讓其中一個接聽項寫入某些訊息。  
  
     組態檔會在初始化應用程式時，初始化追蹤來源的設定。 應用程式可以動態變更組態檔所設定的屬性，以覆寫使用者指定的任何設定。 例如，您可能會想要確保重大訊息一定會傳送到文字檔，不論目前的組態設定為何。 範例程式碼將示範如何覆寫組態檔設定，以確保重大訊息會輸出到追蹤接聽程式。  
  
     在應用程式執行時變更組態檔設定，並不會變更最初的設定； 若要變更設定，您必須重新啟動應用程式，或是使用 <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> 方法，以程式設計方式重新整理應用程式。  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a>若要在不使用組態檔的情況下初始化追蹤來源、接聽項和篩選條件  
  
-   使用下列範例程式碼可透過追蹤來源進行追蹤，而不需要使用組態檔。 這不是建議的做法，但是在您不想要根據組態檔來確保追蹤作業的情況下，可以採取這個做法。  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [追蹤和檢測應用程式](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
