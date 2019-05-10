---
title: HOW TO：建立和初始化追蹤來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 805e1cc7d1def74a2a3e7b28afd052be1c4836c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596829"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="1991c-102">HOW TO：建立和初始化追蹤來源</span><span class="sxs-lookup"><span data-stu-id="1991c-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="1991c-103">應用程式會使用 <xref:System.Diagnostics.TraceSource> 類別產生能夠與應用程式相關聯的追蹤。</span><span class="sxs-lookup"><span data-stu-id="1991c-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="1991c-104"><xref:System.Diagnostics.TraceSource> 提供了追蹤方法，能讓您輕鬆地追蹤事件、追蹤資料和問題資訊追蹤。</span><span class="sxs-lookup"><span data-stu-id="1991c-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="1991c-105">不論是否使用組態檔，都可以從 <xref:System.Diagnostics.TraceSource> 建立及初始化追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="1991c-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="1991c-106">本主題提供這兩個選項的指示。</span><span class="sxs-lookup"><span data-stu-id="1991c-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="1991c-107">不過，建議您使用組態檔來協助重新設定追蹤來源於執行階段所產生的追蹤。</span><span class="sxs-lookup"><span data-stu-id="1991c-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="1991c-108">若要使用組態檔建立及初始化追蹤來源</span><span class="sxs-lookup"><span data-stu-id="1991c-108">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="1991c-109">建立 Visual Studio 主控台應用程式專案，並且將提供的程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="1991c-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="1991c-110">這個程式碼會記錄錯誤和警告，並且將其中一部分輸出至主控台，而另一部分輸出至 myListener 檔 (該檔案是由組態檔中的項目所建立)。</span><span class="sxs-lookup"><span data-stu-id="1991c-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="1991c-111">將應用程式組態檔加入至專案 (如果專案中尚未存在該檔案)，以初始化步驟 1 的程式碼範例中名為 `TraceSourceApp` 的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1991c-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="1991c-112">將預設的組態檔內容取代為下列設定，以初始化主控台追蹤接聽程式，以及步驟 1 中所建立追蹤來源的文字寫入器追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="1991c-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="1991c-113">除了設定追蹤接聽程式之外，組態檔也會針對這兩個接聽程式建立篩選條件，並為追蹤來源建立來源參數。</span><span class="sxs-lookup"><span data-stu-id="1991c-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="1991c-114">此外，有示範兩個技巧來加入追蹤接聽項：將接聽項直接加入到追蹤來源，並將接聽項加入到共用接聽項集合，然後根據名稱將它加入到追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1991c-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="1991c-115">會使用不同的來源層級來初始化這兩個接聽項所識別的篩選條件，</span><span class="sxs-lookup"><span data-stu-id="1991c-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="1991c-116">如此只會讓其中一個接聽項寫入某些訊息。</span><span class="sxs-lookup"><span data-stu-id="1991c-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="1991c-117">組態檔會在初始化應用程式時，初始化追蹤來源的設定。</span><span class="sxs-lookup"><span data-stu-id="1991c-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="1991c-118">應用程式可以動態變更組態檔所設定的屬性，以覆寫使用者指定的任何設定。</span><span class="sxs-lookup"><span data-stu-id="1991c-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="1991c-119">例如，您可能會想要確保重大訊息一定會傳送到文字檔，不論目前的組態設定為何。</span><span class="sxs-lookup"><span data-stu-id="1991c-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="1991c-120">範例程式碼將示範如何覆寫組態檔設定，以確保重大訊息會輸出到追蹤接聽程式。</span><span class="sxs-lookup"><span data-stu-id="1991c-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="1991c-121">在應用程式執行時變更組態檔設定，並不會變更最初的設定；</span><span class="sxs-lookup"><span data-stu-id="1991c-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="1991c-122">若要變更設定，您必須重新啟動應用程式，或是使用 <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> 方法，以程式設計方式重新整理應用程式。</span><span class="sxs-lookup"><span data-stu-id="1991c-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="1991c-123">若要在不使用組態檔的情況下初始化追蹤來源、接聽項和篩選條件</span><span class="sxs-lookup"><span data-stu-id="1991c-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
- <span data-ttu-id="1991c-124">使用下列範例程式碼可透過追蹤來源進行追蹤，而不需要使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="1991c-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="1991c-125">這不是建議的做法，但是在您不想要根據組態檔來確保追蹤作業的情況下，可以採取這個做法。</span><span class="sxs-lookup"><span data-stu-id="1991c-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1991c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1991c-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="1991c-127">追蹤和檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="1991c-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
