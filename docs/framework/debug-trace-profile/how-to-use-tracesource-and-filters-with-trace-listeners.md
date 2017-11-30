---
title: "如何：使用 TraceSource 和含有追蹤接聽項的篩選條件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b557a9f9f462df2d1afe6d6b61871e0e9f40174
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a>如何：使用 TraceSource 和含有追蹤接聽項的篩選條件
.NET Framework 2.0 版的其中一個新功能是增強型追蹤系統。 基本的前提不變：追蹤訊息透過接聽項的參數來傳送，將資料報告給關聯的輸出媒體。 2.0 版的主要不同之處是可以透過 <xref:System.Diagnostics.TraceSource> 類別的執行個體來起始追蹤。 <xref:System.Diagnostics.TraceSource> 類別預期作為增強型追蹤系統，並可用來取代較舊之 <xref:System.Diagnostics.Trace> 和 <xref:System.Diagnostics.Debug> 追蹤類別的靜態方法。 熟悉的 <xref:System.Diagnostics.Trace> 和 <xref:System.Diagnostics.Debug> 類別仍然存在，但建議的做法是使用 <xref:System.Diagnostics.TraceSource> 類別進行追蹤。  
  
 本主題描述如何將 <xref:System.Diagnostics.TraceSource> 與應用程式組態檔搭配使用。  雖然可以在不使用組態檔的情況下利用 <xref:System.Diagnostics.TraceSource> 來進行追蹤，但不建議這麼做。 如需不使用組態檔進行追蹤的資訊，請參閱[何：建立和初始化追蹤來源](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)。  
  
### <a name="to-create-and-initialize-your-trace-source"></a>建立和初始化追蹤來源  
  
1.  使用追蹤來檢測應用程式的第一步是建立追蹤來源。 在具有各種元件的大型專案中，您可以為每一個元件建立個別的追蹤來源。 建議的做法是使用應用程式名稱當作追蹤來源名稱。 如此可讓您輕鬆地分開保存不同的追蹤。 下列程式碼會建立新的追蹤來源 (`mySource)`，並呼叫一個可追蹤事件的方法 (`Activity1`)。  追蹤訊息是由預設追蹤接聽項所撰寫。  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a>建立和初始化追蹤接聽項與篩選條件  
  
1.  第一個程序中的程式碼不會以程式設計方式識別任何追蹤接聽項或篩選條件。 程式碼本身就會產生寫入到預設追蹤接聽項中的追蹤訊息。 若要設定特定的追蹤接聽項和其關聯的篩選條件，請編輯與應用程式名稱對應的組態檔。 在此檔案中，您可以新增或移除接聽項、為接聽項設定屬性和篩選條件，或是移除接聽項。 下列組態檔範例示範如何針對上一個程序中建立的追蹤來源，初始化主控台追蹤接聽項和文字寫入器追蹤接聽項。 除了設定追蹤接聽項之外，組態檔也會針對這兩個接聽項建立篩選條件，並為追蹤來源建立來源參數。 此外，有示範兩個技巧來加入追蹤接聽項：將接聽項直接加入到追蹤來源，並將接聽項加入到共用接聽項集合，然後根據名稱將它加入到追蹤來源。 會使用不同的來源層級來初始化這兩個接聽項所識別的篩選條件， 如此只會讓其中一個接聽項寫入某些訊息。  
  
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
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a>變更接聽項寫入追蹤訊息的層級  
  
1.  組態檔會在初始化應用程式時，初始化追蹤來源的設定。 若要變更這些設定，您必須變更組態檔並重新啟動應用程式，或是使用 <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> 方法，以程式設計方式重新整理應用程式。 應用程式可以動態變更組態檔所設定的屬性，以覆寫使用者指定的任何設定。  例如，您可能會想要確保重大訊息一定會傳送到文字檔，不論目前的組態設定為何。  
  
    ```  
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =   
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified   
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =   
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures   
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners   
                // for all event types. This statement will override   
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,   
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,   
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,   
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,   
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [如何： 建立和初始化追蹤來源](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)  
 [追蹤接聽項](../../../docs/framework/debug-trace-profile/trace-listeners.md)
