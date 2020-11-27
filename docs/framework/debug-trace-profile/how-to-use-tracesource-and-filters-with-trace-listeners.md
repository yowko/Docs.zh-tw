---
title: 作法：使用 TraceSource 和含有追蹤接聽項的篩選條件
description: 使用 TraceSource 類別，並使用 .NET 中的追蹤接聽程式來篩選。 TraceSource 取代舊版追蹤和偵錯工具類別的靜態方法。
ms.date: 03/30/2017
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
ms.openlocfilehash: 94af872e0417941f17c043710688c7b723cd4004
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272796"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="a8554-104">作法：使用 TraceSource 和含有追蹤接聽項的篩選條件</span><span class="sxs-lookup"><span data-stu-id="a8554-104">How to: Use TraceSource and Filters with Trace Listeners</span></span>

<span data-ttu-id="a8554-105">.NET Framework 2.0 版的其中一個新功能是增強型追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="a8554-105">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="a8554-106">基本的前提不變：追蹤訊息透過接聽項的參數來傳送，將資料報告給關聯的輸出媒體。</span><span class="sxs-lookup"><span data-stu-id="a8554-106">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="a8554-107">2.0 版的主要不同之處是可以透過 <xref:System.Diagnostics.TraceSource> 類別的執行個體來起始追蹤。</span><span class="sxs-lookup"><span data-stu-id="a8554-107">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="a8554-108"><xref:System.Diagnostics.TraceSource> 類別預期作為增強型追蹤系統，並可用來取代較舊之 <xref:System.Diagnostics.Trace> 和 <xref:System.Diagnostics.Debug> 追蹤類別的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="a8554-108"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="a8554-109">熟悉的 <xref:System.Diagnostics.Trace> 和 <xref:System.Diagnostics.Debug> 類別仍然存在，但建議的做法是使用 <xref:System.Diagnostics.TraceSource> 類別進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="a8554-109">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="a8554-110">本主題描述如何將 <xref:System.Diagnostics.TraceSource> 與應用程式組態檔搭配使用。</span><span class="sxs-lookup"><span data-stu-id="a8554-110">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="a8554-111">雖然可以在不使用組態檔的情況下利用 <xref:System.Diagnostics.TraceSource> 來進行追蹤，但不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="a8554-111">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="a8554-112">如需不使用組態檔進行追蹤的資訊，請參閱[何：建立和初始化追蹤來源](how-to-create-and-initialize-trace-sources.md)。</span><span class="sxs-lookup"><span data-stu-id="a8554-112">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="a8554-113">建立和初始化追蹤來源</span><span class="sxs-lookup"><span data-stu-id="a8554-113">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="a8554-114">使用追蹤來檢測應用程式的第一步是建立追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="a8554-114">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="a8554-115">在具有各種元件的大型專案中，您可以為每一個元件建立個別的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="a8554-115">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="a8554-116">建議的做法是使用應用程式名稱當作追蹤來源名稱。</span><span class="sxs-lookup"><span data-stu-id="a8554-116">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="a8554-117">如此可讓您輕鬆地分開保存不同的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a8554-117">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="a8554-118">下列程式碼會建立新的追蹤來源 (`mySource)`，並呼叫一個可追蹤事件的方法 (`Activity1`)。</span><span class="sxs-lookup"><span data-stu-id="a8554-118">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="a8554-119">追蹤訊息是由預設追蹤接聽項所撰寫。</span><span class="sxs-lookup"><span data-stu-id="a8554-119">The trace messages are written by the default trace listener.</span></span>  
  
    ```csharp
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="a8554-120">建立和初始化追蹤接聽項與篩選條件</span><span class="sxs-lookup"><span data-stu-id="a8554-120">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="a8554-121">第一個程序中的程式碼不會以程式設計方式識別任何追蹤接聽項或篩選條件。</span><span class="sxs-lookup"><span data-stu-id="a8554-121">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="a8554-122">程式碼本身就會產生寫入到預設追蹤接聽項中的追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="a8554-122">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="a8554-123">若要設定特定的追蹤接聽項和其關聯的篩選條件，請編輯與應用程式名稱對應的組態檔。</span><span class="sxs-lookup"><span data-stu-id="a8554-123">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="a8554-124">在此檔案中，您可以新增或移除接聽項、為接聽項設定屬性和篩選條件，或是移除接聽項。</span><span class="sxs-lookup"><span data-stu-id="a8554-124">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="a8554-125">下列組態檔範例示範如何針對上一個程序中建立的追蹤來源，初始化主控台追蹤接聽項和文字寫入器追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="a8554-125">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="a8554-126">除了設定追蹤接聽項之外，組態檔也會針對這兩個接聽項建立篩選條件，並為追蹤來源建立來源參數。</span><span class="sxs-lookup"><span data-stu-id="a8554-126">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="a8554-127">此外，有示範兩個技巧來加入追蹤接聽項：將接聽項直接加入到追蹤來源，並將接聽項加入到共用接聽項集合，然後根據名稱將它加入到追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="a8554-127">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="a8554-128">會使用不同的來源層級來初始化這兩個接聽項所識別的篩選條件，</span><span class="sxs-lookup"><span data-stu-id="a8554-128">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="a8554-129">如此只會讓其中一個接聽項寫入某些訊息。</span><span class="sxs-lookup"><span data-stu-id="a8554-129">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="a8554-130">變更接聽項寫入追蹤訊息的層級</span><span class="sxs-lookup"><span data-stu-id="a8554-130">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="a8554-131">組態檔會在初始化應用程式時，初始化追蹤來源的設定。</span><span class="sxs-lookup"><span data-stu-id="a8554-131">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="a8554-132">若要變更這些設定，您必須變更組態檔並重新啟動應用程式，或是使用 <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> 方法，以程式設計方式重新整理應用程式。</span><span class="sxs-lookup"><span data-stu-id="a8554-132">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a8554-133">應用程式可以動態變更組態檔所設定的屬性，以覆寫使用者指定的任何設定。</span><span class="sxs-lookup"><span data-stu-id="a8554-133">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="a8554-134">例如，您可能會想要確保重大訊息一定會傳送到文字檔，不論目前的組態設定為何。</span><span class="sxs-lookup"><span data-stu-id="a8554-134">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
    ```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="a8554-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8554-135">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="a8554-136">作法：建立和初始化追蹤來源</span><span class="sxs-lookup"><span data-stu-id="a8554-136">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="a8554-137">追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="a8554-137">Trace Listeners</span></span>](trace-listeners.md)
