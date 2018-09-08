---
title: 設定追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: c5064d90c8601ee44be593446b0fd5ad483e57f2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135792"
---
# <a name="configuring-tracing"></a><span data-ttu-id="f5d05-102">設定追蹤</span><span class="sxs-lookup"><span data-stu-id="f5d05-102">Configuring Tracing</span></span>
<span data-ttu-id="f5d05-103">本主題將說明如何啟用追蹤、設定追蹤來源以發出追蹤並設定追蹤層級、設定活動追蹤與傳播以支援端對端追蹤相互關聯，以及設定追蹤接聽項來存取追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-103">This topic describes how you can enable tracing, configure trace sources to emit traces and set trace levels, set activity tracing and propagation to support end-to-end trace correlation, and set trace listeners to access traces.</span></span>  
  
 <span data-ttu-id="f5d05-104">如需在實際執行或偵錯環境中的追蹤設定建議，請參閱[追蹤和訊息記錄的建議設定](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d05-104">For tracing settings recommendations in production or debugging environment, refer to [Recommended Settings for Tracing and Message Logging](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5d05-105">在 Windows 8 上，您必須提高權限來執行應用程式 (以系統管理員身分執行)，您的應用程式才能產生追蹤記錄。</span><span class="sxs-lookup"><span data-stu-id="f5d05-105">On Windows 8 you must run your application elevated (Run as Administrator) in order for your application to generate trace logs.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="f5d05-106">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="f5d05-106">Enabling Tracing</span></span>  
 <span data-ttu-id="f5d05-107">Windows Communication Foundation (WCF) 會輸出下列進行診斷追蹤資料：</span><span class="sxs-lookup"><span data-stu-id="f5d05-107">Windows Communication Foundation (WCF) outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="f5d05-108">所有應用程式元件的處理過程里程碑追蹤，例如作業呼叫、程式碼例外狀況、警告和其他重大處理事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-108">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events.</span></span>  
  
-   <span data-ttu-id="f5d05-109">追蹤功能故障時出現的 Windows 錯誤事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-109">Windows error events when the tracing feature malfunctions.</span></span> <span data-ttu-id="f5d05-110">請參閱[事件記錄](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d05-110">See [Event Logging](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).</span></span>  
  
 <span data-ttu-id="f5d05-111">WCF 追蹤之上的<xref:System.Diagnostics>。</span><span class="sxs-lookup"><span data-stu-id="f5d05-111">WCF tracing is built on top of <xref:System.Diagnostics>.</span></span> <span data-ttu-id="f5d05-112">若要使用追蹤，您應該透過組態檔或程式碼來定義追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="f5d05-112">To use tracing, you should define trace sources in the configuration file or in code.</span></span> <span data-ttu-id="f5d05-113">WCF 會針對每個 WCF 組件定義追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="f5d05-113">WCF defines a trace source for each WCF assembly.</span></span> <span data-ttu-id="f5d05-114">`System.ServiceModel`追蹤來源是最普遍的 WCF 追蹤來源，並跨 WCF 通訊堆疊，從進入/離開傳輸到進入/離開使用者程式碼會記錄處理里程碑。</span><span class="sxs-lookup"><span data-stu-id="f5d05-114">The `System.ServiceModel` trace source is the most general WCF trace source, and records processing milestones across the WCF communication stack, from entering/leaving transport to entering/leaving user code.</span></span> <span data-ttu-id="f5d05-115">`System.ServiceModel.MessageLogging` 追蹤來源會記錄在系統之間來回傳送的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="f5d05-115">The `System.ServiceModel.MessageLogging` trace source records all messages that flow through the system.</span></span>  
  
 <span data-ttu-id="f5d05-116">預設不會啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-116">Tracing is not enabled by default.</span></span> <span data-ttu-id="f5d05-117">若要啟用追蹤，您必須建立追蹤接聽程式，並設定中，設定追蹤層級以外的 「 關閉 」 時選取的追蹤來源否則，WCF 不會產生任何追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-117">To activate tracing, you must create a trace listener and set a trace level other than "Off" for the selected trace source in configuration; otherwise, WCF does not generate any traces.</span></span> <span data-ttu-id="f5d05-118">如果您沒有指定接聽項，就會自動停用追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-118">If you do not specify a listener, tracing is automatically disabled.</span></span> <span data-ttu-id="f5d05-119">如果已定義接聽項，但是未指定層級，則預設會將層級設定為「關閉」，這表示將不會發出任何追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-119">If a listener is defined, but no level is specified, the level is set to "Off" by default, which means that no trace is emitted.</span></span>  
  
 <span data-ttu-id="f5d05-120">如果您使用自訂作業啟動程式這類 WCF 擴充性點，您應該發出自己的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-120">If you use WCF extensibility points such as custom operation invokers, you should emit your own traces.</span></span> <span data-ttu-id="f5d05-121">這是因為如果您實作的擴充點時，WCF 可以不再發出中的預設路徑的標準追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-121">This is because if you implement an extensibility point, WCF can no longer emit the standard traces in the default path.</span></span> <span data-ttu-id="f5d05-122">如果您沒有透過發出追蹤來實作手動追蹤支援，可能無法看見預期的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-122">If you do not implement manual tracing support by emitting traces, you may not see the traces you expect.</span></span>  
  
 <span data-ttu-id="f5d05-123">您可以透過編輯應用程式的組態檔 (Web 主控應用程式的 Web.config，或自我裝載應用程式的 Appname.exe.config) 來設定追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-123">You can configure tracing by editing the application’s configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted applications.</span></span> <span data-ttu-id="f5d05-124">下列是這類編輯的範例。</span><span class="sxs-lookup"><span data-stu-id="f5d05-124">The following is an example of such edit.</span></span> <span data-ttu-id="f5d05-125">如需有關這些設定的詳細資訊，請參閱 「 設定追蹤接聽程式來使用追蹤 > 一節。</span><span class="sxs-lookup"><span data-stu-id="f5d05-125">For more information on these settings, see the "Configuring Trace Listeners to Consume Traces" section.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="f5d05-126">若要編輯的 Visual Studio 中的 WCF 服務專案的組態檔，以滑鼠右鍵按一下應用程式的組態檔 — Web.config Web 裝載的應用程式或在自我裝載的應用程式的 Appname.exe.config**方案總管**.</span><span class="sxs-lookup"><span data-stu-id="f5d05-126">To edit the configuration file of a WCF service project in Visual Studio, right click the application’s configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted application in **Solution Explorer**.</span></span> <span data-ttu-id="f5d05-127">然後選擇**編輯 WCF 組態**操作功能表項目。</span><span class="sxs-lookup"><span data-stu-id="f5d05-127">Then choose the **Edit WCF Configuration** context menu item.</span></span> <span data-ttu-id="f5d05-128">這會啟動[組態編輯器工具 (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)，這可讓您修改 WCF 服務使用圖形化使用者介面的組態設定。</span><span class="sxs-lookup"><span data-stu-id="f5d05-128">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), which enables you to modify configuration settings for WCF services using a graphical user interface.</span></span>  
  
## <a name="configuring-trace-sources-to-emit-traces"></a><span data-ttu-id="f5d05-129">設定追蹤來源來發出追蹤</span><span class="sxs-lookup"><span data-stu-id="f5d05-129">Configuring Trace Sources to Emit Traces</span></span>  
 <span data-ttu-id="f5d05-130">WCF 會針對每個組件定義追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="f5d05-130">WCF defines a trace source for each assembly.</span></span> <span data-ttu-id="f5d05-131">組件中產生的追蹤是由針對該來源而定義的接聽項所存取。</span><span class="sxs-lookup"><span data-stu-id="f5d05-131">Traces generated within an assembly are accessed by the listeners defined for that source.</span></span> <span data-ttu-id="f5d05-132">下列為定義的追蹤來源：</span><span class="sxs-lookup"><span data-stu-id="f5d05-132">The following trace sources are defined:</span></span>  
  
-   <span data-ttu-id="f5d05-133">System.ServiceModel： 記錄所有階段的 WCF 處理，每當在讀取組態、 已處理訊息傳輸、 安全性處理，訊息會分派在使用者程式碼，並依此類推。</span><span class="sxs-lookup"><span data-stu-id="f5d05-133">System.ServiceModel: Logs all stages of WCF processing, whenever configuration is read, a message is processed in transport, security processing, a message is dispatched in user code, and so on.</span></span>  
  
-   <span data-ttu-id="f5d05-134">System.ServiceModel.MessageLogging：記錄在整個系統來回傳送的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="f5d05-134">System.ServiceModel.MessageLogging: Logs all messages that flow through the system.</span></span>  
  
-   <span data-ttu-id="f5d05-135">System.IdentityModel。</span><span class="sxs-lookup"><span data-stu-id="f5d05-135">System.IdentityModel.</span></span>  
  
-   <span data-ttu-id="f5d05-136">System.ServiceModel.Activation。</span><span class="sxs-lookup"><span data-stu-id="f5d05-136">System.ServiceModel.Activation.</span></span>  
  
-   <span data-ttu-id="f5d05-137">System.IO.Log：記錄一般記錄檔系統 (CLFS) 的 .NET Framework 介面。</span><span class="sxs-lookup"><span data-stu-id="f5d05-137">System.IO.Log: Logging for the .NET Framework interface to the Common Log File System (CLFS).</span></span>  
  
-   <span data-ttu-id="f5d05-138">System.Runtime.Serialization：記錄何時讀取或寫入物件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-138">System.Runtime.Serialization: Logs when objects are read or written.</span></span>  
  
-   <span data-ttu-id="f5d05-139">CardSpace。</span><span class="sxs-lookup"><span data-stu-id="f5d05-139">CardSpace.</span></span>  
  
 <span data-ttu-id="f5d05-140">您可以設定每個追蹤來源來使用相同 (共用) 的接聽項，如下列組態範例所示。</span><span class="sxs-lookup"><span data-stu-id="f5d05-140">You can configure each trace source to use the same (shared) listener, as indicated in the following configuration example.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="f5d05-141">此外，您可以新增使用者定義的追蹤來源 (如下列範例所示範) 來發出使用者程式碼追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-141">In addition, you can add user-defined trace sources, as demonstrated by the following example, to emit user code traces.</span></span>  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 <span data-ttu-id="f5d05-142">如需建立使用者定義的追蹤來源的詳細資訊，請參閱 <<c0> [ 擴充追蹤](../../../../../docs/framework/wcf/samples/extending-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d05-142">For more information about creating user-defined trace sources, see [Extending Tracing](../../../../../docs/framework/wcf/samples/extending-tracing.md).</span></span>  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a><span data-ttu-id="f5d05-143">設定追蹤接聽項來使用追蹤</span><span class="sxs-lookup"><span data-stu-id="f5d05-143">Configuring Trace Listeners to Consume Traces</span></span>  
 <span data-ttu-id="f5d05-144">在執行階段，WCF 會負責處理資料的接聽項摘要追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="f5d05-144">At runtime, WCF feeds trace data to the listeners which process the data.</span></span> <span data-ttu-id="f5d05-145">WCF 提供數個預先定義的接聽程式<xref:System.Diagnostics>，其格式與輸出時使用的格式不同。</span><span class="sxs-lookup"><span data-stu-id="f5d05-145">WCF provides several predefined listeners for <xref:System.Diagnostics>, which differ in the format they use for output.</span></span> <span data-ttu-id="f5d05-146">您也可以新增自訂接聽項型別。</span><span class="sxs-lookup"><span data-stu-id="f5d05-146">You can also add custom listener types.</span></span>  
  
 <span data-ttu-id="f5d05-147">您可以使用 `add` 來指定要使用的追蹤接聽項名稱與型別。</span><span class="sxs-lookup"><span data-stu-id="f5d05-147">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="f5d05-148">在我們的組態範例中，我們將接聽項命名為 `traceListener` 並將標準 .NET Framework 追蹤接聽項 (`System.Diagnostics.XmlWriterTraceListener`) 當成要使用的型別加入。</span><span class="sxs-lookup"><span data-stu-id="f5d05-148">In our example configuration, we named the Listener `traceListener` and added the standard .NET Framework trace listener (`System.Diagnostics.XmlWriterTraceListener`) as the type we want to use.</span></span> <span data-ttu-id="f5d05-149">您可以為每一個來源新增任何數量的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="f5d05-149">You can add any number of trace listeners for each source.</span></span> <span data-ttu-id="f5d05-150">如果追蹤接聽項將追蹤發出到檔案中，則您必須在組態檔中指定輸出檔案位置與名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d05-150">If the trace listener emits the trace to a file, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="f5d05-151">您可以將 `initializeData` 設定為該接聽項的檔案名稱來完成。</span><span class="sxs-lookup"><span data-stu-id="f5d05-151">This is done by setting `initializeData` to the name of the file for that listener.</span></span> <span data-ttu-id="f5d05-152">如果您沒有指定檔案名稱，就會根據使用的接聽項型別產生隨機檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d05-152">If you do not specify a file name, a random file name is generated based on the listener type used.</span></span> <span data-ttu-id="f5d05-153">如果使用了 <xref:System.Diagnostics.XmlWriterTraceListener>，則會產生不含副檔名的檔名。</span><span class="sxs-lookup"><span data-stu-id="f5d05-153">If <xref:System.Diagnostics.XmlWriterTraceListener> is used, a file name with no extension is generated.</span></span> <span data-ttu-id="f5d05-154">如果您實作自訂接聽項，也可以同時使用此屬性來接收初始化資料 (而不是檔名)。</span><span class="sxs-lookup"><span data-stu-id="f5d05-154">If you implement a custom listener, you can also use this attribute to receive initialization data other than a filename.</span></span> <span data-ttu-id="f5d05-155">例如，您可以為此屬性指定資料庫識別項。</span><span class="sxs-lookup"><span data-stu-id="f5d05-155">For example, you can specify a database identifier for this attribute.</span></span>  
  
 <span data-ttu-id="f5d05-156">您可以設定自訂追蹤接聽項，以將追蹤傳送到 Wire，例如傳送至遠端資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5d05-156">You can configure a custom trace listener to send traces on the wire, for example, to a remote database.</span></span> <span data-ttu-id="f5d05-157">身為應用程式的部署者，您應該在遠端電腦的追蹤記錄上強制執行適當的存取控制。</span><span class="sxs-lookup"><span data-stu-id="f5d05-157">As an application deployer, you should enforce proper access control on the trace logs in the remote machine.</span></span>  
  
 <span data-ttu-id="f5d05-158">您也可以使用程式設計方式來設定追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="f5d05-158">You can also configure a trace listener programmatically.</span></span> <span data-ttu-id="f5d05-159">如需詳細資訊，請參閱 <<c0> [ 如何： 建立和初始化追蹤接聽項](https://go.microsoft.com/fwlink/?LinkId=94648)並[建立自訂 TraceListener](https://go.microsoft.com/fwlink/?LinkId=96239)。</span><span class="sxs-lookup"><span data-stu-id="f5d05-159">For more information, see [How to: Create and Initialize Trace Listeners](https://go.microsoft.com/fwlink/?LinkId=94648) and [Creating a Custom TraceListener](https://go.microsoft.com/fwlink/?LinkId=96239).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f5d05-160">因為 `System.Diagnostics.XmlWriterTraceListener` 不具備執行緒安全，追蹤來源可能會在輸出追蹤時特別鎖定資源。</span><span class="sxs-lookup"><span data-stu-id="f5d05-160">Because `System.Diagnostics.XmlWriterTraceListener` is not thread-safe, the trace source may lock resources exclusively when outputting traces.</span></span> <span data-ttu-id="f5d05-161">當許多執行緒將追蹤輸出至設定為使用此接聽項的追蹤來源時，可能會發生資源爭用的情況，進而造成顯著的效能問題。</span><span class="sxs-lookup"><span data-stu-id="f5d05-161">When many threads output traces to a trace source configured to use this listener, resource contention may occur, which results in a significant performance issue.</span></span> <span data-ttu-id="f5d05-162">若要解決這個問題，您應該實作具備執行緒安全的自訂接聽項。</span><span class="sxs-lookup"><span data-stu-id="f5d05-162">To resolve this problem, you should implement a custom listener that is thread-safe.</span></span>  
  
## <a name="trace-level"></a><span data-ttu-id="f5d05-163">追蹤層級</span><span class="sxs-lookup"><span data-stu-id="f5d05-163">Trace Level</span></span>  
 <span data-ttu-id="f5d05-164">追蹤層級是透過追蹤來源的 `switchValue` 設定來控制。</span><span class="sxs-lookup"><span data-stu-id="f5d05-164">The tracing level is controlled by the `switchValue` setting of the trace source.</span></span> <span data-ttu-id="f5d05-165">下表描述可使用的追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="f5d05-165">The available tracing levels are described in the following table.</span></span>  
  
|<span data-ttu-id="f5d05-166">追蹤層級</span><span class="sxs-lookup"><span data-stu-id="f5d05-166">Trace Level</span></span>|<span data-ttu-id="f5d05-167">追蹤事件的本質</span><span class="sxs-lookup"><span data-stu-id="f5d05-167">Nature of the Tracked Events</span></span>|<span data-ttu-id="f5d05-168">追蹤事件的內容</span><span class="sxs-lookup"><span data-stu-id="f5d05-168">Content of the Tracked Events</span></span>|<span data-ttu-id="f5d05-169">追蹤事件</span><span class="sxs-lookup"><span data-stu-id="f5d05-169">Tracked Events</span></span>|<span data-ttu-id="f5d05-170">使用者目標</span><span class="sxs-lookup"><span data-stu-id="f5d05-170">User Target</span></span>|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="f5d05-171">Off</span><span class="sxs-lookup"><span data-stu-id="f5d05-171">Off</span></span>|<span data-ttu-id="f5d05-172">N/A</span><span class="sxs-lookup"><span data-stu-id="f5d05-172">N/A</span></span>|<span data-ttu-id="f5d05-173">N/A</span><span class="sxs-lookup"><span data-stu-id="f5d05-173">N/A</span></span>|<span data-ttu-id="f5d05-174">未發出任何追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-174">No traces are emitted.</span></span>|<span data-ttu-id="f5d05-175">N/A</span><span class="sxs-lookup"><span data-stu-id="f5d05-175">N/A</span></span>|  
|<span data-ttu-id="f5d05-176">Critical</span><span class="sxs-lookup"><span data-stu-id="f5d05-176">Critical</span></span>|<span data-ttu-id="f5d05-177">「 負面 」 事件： 指示非預期的處理或錯誤狀況的事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-177">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>||<span data-ttu-id="f5d05-178">已記錄包含下列的未處理例外狀況：</span><span class="sxs-lookup"><span data-stu-id="f5d05-178">Unhandled exceptions including the following are logged:</span></span><br /><br /> <span data-ttu-id="f5d05-179">-OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="f5d05-179">-   OutOfMemoryException</span></span><br /><span data-ttu-id="f5d05-180">-ThreadAbortException （CLR 會叫用任何 ThreadAbortExceptionHandler）</span><span class="sxs-lookup"><span data-stu-id="f5d05-180">-   ThreadAbortException (the CLR invokes any ThreadAbortExceptionHandler)</span></span><br /><span data-ttu-id="f5d05-181">-StackOverflowException （無法攔截）</span><span class="sxs-lookup"><span data-stu-id="f5d05-181">-   StackOverflowException (cannot be caught)</span></span><br /><span data-ttu-id="f5d05-182">-ConfigurationErrorsException</span><span class="sxs-lookup"><span data-stu-id="f5d05-182">-   ConfigurationErrorsException</span></span><br /><span data-ttu-id="f5d05-183">-SEHException</span><span class="sxs-lookup"><span data-stu-id="f5d05-183">-   SEHException</span></span><br /><span data-ttu-id="f5d05-184">-應用程式啟動錯誤</span><span class="sxs-lookup"><span data-stu-id="f5d05-184">-   Application start errors</span></span><br /><span data-ttu-id="f5d05-185">-Failfast 事件</span><span class="sxs-lookup"><span data-stu-id="f5d05-185">-   Failfast events</span></span><br /><span data-ttu-id="f5d05-186">系統停止回應</span><span class="sxs-lookup"><span data-stu-id="f5d05-186">-   System hangs</span></span><br /><span data-ttu-id="f5d05-187">-有害訊息： 訊息會導致應用程式失敗的追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-187">-   Poison messages: message traces that cause the application to fail.</span></span>|<span data-ttu-id="f5d05-188">系統管理員</span><span class="sxs-lookup"><span data-stu-id="f5d05-188">Administrators</span></span><br /><br /> <span data-ttu-id="f5d05-189">應用程式開發人員</span><span class="sxs-lookup"><span data-stu-id="f5d05-189">Application developers</span></span>|  
|<span data-ttu-id="f5d05-190">錯誤</span><span class="sxs-lookup"><span data-stu-id="f5d05-190">Error</span></span>|<span data-ttu-id="f5d05-191">「 負面 」 事件： 指示非預期的處理或錯誤狀況的事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-191">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="f5d05-192">發生未預期的處理。</span><span class="sxs-lookup"><span data-stu-id="f5d05-192">Unexpected processing has happened.</span></span> <span data-ttu-id="f5d05-193">應用程式無法如預期般執行工作。</span><span class="sxs-lookup"><span data-stu-id="f5d05-193">The application was not able to perform a task as expected.</span></span> <span data-ttu-id="f5d05-194">然而，應用程式仍舊繼續執行。</span><span class="sxs-lookup"><span data-stu-id="f5d05-194">However, the application is still up and running.</span></span>|<span data-ttu-id="f5d05-195">已記錄所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f5d05-195">All exceptions are logged.</span></span>|<span data-ttu-id="f5d05-196">系統管理員</span><span class="sxs-lookup"><span data-stu-id="f5d05-196">Administrators</span></span><br /><br /> <span data-ttu-id="f5d05-197">應用程式開發人員</span><span class="sxs-lookup"><span data-stu-id="f5d05-197">Application developers</span></span>|  
|<span data-ttu-id="f5d05-198">警告</span><span class="sxs-lookup"><span data-stu-id="f5d05-198">Warning</span></span>|<span data-ttu-id="f5d05-199">「 負面 」 事件： 指示非預期的處理或錯誤狀況的事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-199">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="f5d05-200">潛在問題已經發生或是可能發生，但是應用程式仍舊正常運作。</span><span class="sxs-lookup"><span data-stu-id="f5d05-200">A possible problem has occurred or may occur, but the application still functions correctly.</span></span> <span data-ttu-id="f5d05-201">然而，它可能無法繼續正常運作。</span><span class="sxs-lookup"><span data-stu-id="f5d05-201">However, it may not continue to work properly.</span></span>|<span data-ttu-id="f5d05-202">-應用程式已收到的要求超過其節流設定允許。</span><span class="sxs-lookup"><span data-stu-id="f5d05-202">-   The application is receiving more requests than its throttling settings allow.</span></span><br /><span data-ttu-id="f5d05-203">-按收佇列已接近其最大的已設定容量。</span><span class="sxs-lookup"><span data-stu-id="f5d05-203">-   The receiving queue is near its maximum configured capacity.</span></span><br /><span data-ttu-id="f5d05-204">已超過逾時。</span><span class="sxs-lookup"><span data-stu-id="f5d05-204">-   Timeout has exceeded.</span></span><br /><span data-ttu-id="f5d05-205">-認證被拒。</span><span class="sxs-lookup"><span data-stu-id="f5d05-205">-   Credentials are rejected.</span></span>|<span data-ttu-id="f5d05-206">系統管理員</span><span class="sxs-lookup"><span data-stu-id="f5d05-206">Administrators</span></span><br /><br /> <span data-ttu-id="f5d05-207">應用程式開發人員</span><span class="sxs-lookup"><span data-stu-id="f5d05-207">Application developers</span></span>|  
|<span data-ttu-id="f5d05-208">資訊</span><span class="sxs-lookup"><span data-stu-id="f5d05-208">Information</span></span>|<span data-ttu-id="f5d05-209">「 正面 」 事件： 標示為成功里程碑的事件</span><span class="sxs-lookup"><span data-stu-id="f5d05-209">"Positive" events: events that mark successful milestones</span></span>|<span data-ttu-id="f5d05-210">不管應用程式是否正常運作，都屬於應用程式執行的重要與成功里程碑。</span><span class="sxs-lookup"><span data-stu-id="f5d05-210">Important and successful milestones of application execution, regardless of whether the application is working properly or not.</span></span>|<span data-ttu-id="f5d05-211">一般來說，會產生對監控與診斷系統狀態、衡量效能，或描述分析有幫助的訊息。</span><span class="sxs-lookup"><span data-stu-id="f5d05-211">In general, messages helpful for monitoring and diagnosing system status, measuring performance or profiling are generated.</span></span> <span data-ttu-id="f5d05-212">您可以使用這類資訊來進行容量規劃與效能管理：</span><span class="sxs-lookup"><span data-stu-id="f5d05-212">You can use such information for capacity planning and performance management:</span></span><br /><br /> <span data-ttu-id="f5d05-213">的已建立通道。</span><span class="sxs-lookup"><span data-stu-id="f5d05-213">-   Channels are created.</span></span><br /><span data-ttu-id="f5d05-214">建立端點接聽程式。</span><span class="sxs-lookup"><span data-stu-id="f5d05-214">-   Endpoint listeners are created.</span></span><br /><span data-ttu-id="f5d05-215">訊息進入/離開傳輸。</span><span class="sxs-lookup"><span data-stu-id="f5d05-215">-   Message enters/leaves transport.</span></span><br /><span data-ttu-id="f5d05-216">擷取安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="f5d05-216">-   Security token is retrieved.</span></span><br /><span data-ttu-id="f5d05-217">會讀取組態設定。</span><span class="sxs-lookup"><span data-stu-id="f5d05-217">-   Configuration setting is read.</span></span>|<span data-ttu-id="f5d05-218">系統管理員</span><span class="sxs-lookup"><span data-stu-id="f5d05-218">Administrators</span></span><br /><br /> <span data-ttu-id="f5d05-219">應用程式開發人員</span><span class="sxs-lookup"><span data-stu-id="f5d05-219">Application developers</span></span><br /><br /> <span data-ttu-id="f5d05-220">產品開發人員。</span><span class="sxs-lookup"><span data-stu-id="f5d05-220">Product developers.</span></span>|  
|<span data-ttu-id="f5d05-221">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f5d05-221">Verbose</span></span>|<span data-ttu-id="f5d05-222">「 正面 」 事件： 標示為成功里程碑的事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-222">"Positive" events: events that mark successful milestones.</span></span>|<span data-ttu-id="f5d05-223">已針對使用者程式碼與服務發出低層級事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-223">Low level events for both user code and servicing are emitted.</span></span>|<span data-ttu-id="f5d05-224">一般來說，您可以使用此層級來進行偵錯或應用程式最佳化。</span><span class="sxs-lookup"><span data-stu-id="f5d05-224">In general, you can use this level for debugging or application optimization.</span></span><br /><br /> <span data-ttu-id="f5d05-225">-了解訊息標頭。</span><span class="sxs-lookup"><span data-stu-id="f5d05-225">-   Understood message header.</span></span>|<span data-ttu-id="f5d05-226">系統管理員</span><span class="sxs-lookup"><span data-stu-id="f5d05-226">Administrators</span></span><br /><br /> <span data-ttu-id="f5d05-227">應用程式開發人員</span><span class="sxs-lookup"><span data-stu-id="f5d05-227">Application developers</span></span><br /><br /> <span data-ttu-id="f5d05-228">產品開發人員。</span><span class="sxs-lookup"><span data-stu-id="f5d05-228">Product developers.</span></span>|  
|<span data-ttu-id="f5d05-229">ActivityTracing</span><span class="sxs-lookup"><span data-stu-id="f5d05-229">ActivityTracing</span></span>||<span data-ttu-id="f5d05-230">介於處理活動與元件之間的流程事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-230">Flow events between processing activities and components.</span></span>|<span data-ttu-id="f5d05-231">這個層級可以讓系統管理員與開發人員相互關聯相同應用程式定義域中的多個應用程式：</span><span class="sxs-lookup"><span data-stu-id="f5d05-231">This level allows administrators and developers to correlate applications in the same application domain:</span></span><br /><br /> <span data-ttu-id="f5d05-232">-活動界限，例如開始/停止追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-232">-   Traces for activity boundaries, such as start/stop.</span></span><br /><span data-ttu-id="f5d05-233">-傳輸追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-233">-   Traces for transfers.</span></span>|<span data-ttu-id="f5d05-234">全部</span><span class="sxs-lookup"><span data-stu-id="f5d05-234">All</span></span>|  
|<span data-ttu-id="f5d05-235">全部</span><span class="sxs-lookup"><span data-stu-id="f5d05-235">All</span></span>||<span data-ttu-id="f5d05-236">應用程式可以正常運作。</span><span class="sxs-lookup"><span data-stu-id="f5d05-236">Application may function properly.</span></span> <span data-ttu-id="f5d05-237">已發出所有事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-237">All events are emitted.</span></span>|<span data-ttu-id="f5d05-238">所有先前的事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-238">All previous events.</span></span>|<span data-ttu-id="f5d05-239">全部</span><span class="sxs-lookup"><span data-stu-id="f5d05-239">All</span></span>|  
  
 <span data-ttu-id="f5d05-240">從「詳細資訊」到「嚴重」的層級會彼此交互堆疊，也就是說，每一個追蹤層級都會包含其上的所有層級 (除了「關閉」層級以外)。</span><span class="sxs-lookup"><span data-stu-id="f5d05-240">The levels from Verbose to Critical are stacked on top of each other, that is, each trace level includes all levels above it except the Off level.</span></span> <span data-ttu-id="f5d05-241">例如，在「警告」層級上接聽的接聽項會收到「嚴重」、「錯誤」以及「警告」追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-241">For example, a listener listening at the Warning level receives Critical, Error, and Warning traces.</span></span> <span data-ttu-id="f5d05-242">「全部」層級包含從「詳細資訊」到「嚴重」與「活動」追蹤事件的所有事件。</span><span class="sxs-lookup"><span data-stu-id="f5d05-242">The All level includes events from Verbose to Critical and Activity tracing events.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f5d05-243">「資訊」、「詳細資訊」以及「ActivityTracing」層級會產生許多追蹤，如果您已經用完電腦上所有可用的資源，則這些追蹤可能會對訊息輸送量產生負面的影響。</span><span class="sxs-lookup"><span data-stu-id="f5d05-243">The Information, Verbose, and ActivityTracing levels generate a lot of traces, which may negatively impact message throughput if you have used up all available resources on the machine.</span></span>  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a><span data-ttu-id="f5d05-244">設定活動追蹤與傳播來進行相互關聯</span><span class="sxs-lookup"><span data-stu-id="f5d05-244">Configuring Activity Tracing and Propagation for Correlation</span></span>  
 <span data-ttu-id="f5d05-245">針對 `activityTracing` 屬性而指定的 `switchValue` 值可用來啟用活動追蹤，活動追蹤會為活動界限發出追蹤並在端點之間進行傳送。</span><span class="sxs-lookup"><span data-stu-id="f5d05-245">The `activityTracing` value specified for the `switchValue` attribute is used to enable activity tracing, which emits traces for activity boundaries and transfers within endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5d05-246">當您在 WCF 中使用的特定擴充功能時，您可能會收到<xref:System.NullReferenceException>時啟用活動追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-246">When you use certain extensibility features in WCF, you might get a <xref:System.NullReferenceException> when activity tracing is enabled.</span></span> <span data-ttu-id="f5d05-247">若要修正這個問題，請檢查您應用程式的組態檔，並確定追蹤來源的 `switchValue` 屬性不是設定為 `activityTracing`。</span><span class="sxs-lookup"><span data-stu-id="f5d05-247">To fix this problem, check your application's configuration file and ensure that the `switchValue` attribute for your trace source is not set to `activityTracing`.</span></span>  
  
 <span data-ttu-id="f5d05-248">`propagateActivity` 屬性會指出是否應該將活動傳播至其他參與訊息交換的端點。</span><span class="sxs-lookup"><span data-stu-id="f5d05-248">The `propagateActivity` attribute indicates whether the activity should be propagated to other endpoints that participate in the message exchange.</span></span> <span data-ttu-id="f5d05-249">將這個值設定為 `true` 之後，您就可以使用任意兩個端點所產生的追蹤檔，來觀察一個端點上的一組追蹤如何流動至另一個端點的一組追蹤。</span><span class="sxs-lookup"><span data-stu-id="f5d05-249">By setting this value to `true`, you can take trace files generated by any two endpoints and observe how a set of traces on one endpoint flowed to a set of traces on another endpoint.</span></span>  
  
 <span data-ttu-id="f5d05-250">如需有關活動追蹤與傳播的詳細資訊，請參閱[傳播](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d05-250">For more information about activity tracing and propagation, see [Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).</span></span>  
  
 <span data-ttu-id="f5d05-251">兩者`propagateActivity`和`ActivityTracing`布林值都會套用至 System.ServiceModel TraceSource。</span><span class="sxs-lookup"><span data-stu-id="f5d05-251">Both `propagateActivity` and `ActivityTracing` Boolean values apply to the System.ServiceModel TraceSource.</span></span> <span data-ttu-id="f5d05-252">`ActivityTracing`值也會套用至任何追蹤來源，包括 WCF 或使用者定義的。</span><span class="sxs-lookup"><span data-stu-id="f5d05-252">The `ActivityTracing` value also applies to any trace source, including WCF or user-defined ones.</span></span>  
  
 <span data-ttu-id="f5d05-253">您無法使用具有使用者定義追蹤來源的 `propagateActivity` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f5d05-253">You cannot use the `propagateActivity` attribute with user-defined trace sources.</span></span> <span data-ttu-id="f5d05-254">若要進行使用者程式碼活動識別碼傳播，請確定您未設定 ServiceModel `ActivityTracing`，而且讓 ServiceModel `propagateActivity` 屬性仍舊設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="f5d05-254">For user code activity ID propagation, make sure you do not set ServiceModel `ActivityTracing`, while still having ServiceModel `propagateActivity` attribute set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d05-255">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5d05-255">See Also</span></span>  
 [<span data-ttu-id="f5d05-256">追蹤</span><span class="sxs-lookup"><span data-stu-id="f5d05-256">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f5d05-257">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="f5d05-257">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="f5d05-258">如何：建立和初始設定追蹤接聽項</span><span class="sxs-lookup"><span data-stu-id="f5d05-258">How to: Create and Initialize Trace Listeners</span></span>](https://go.microsoft.com/fwlink/?LinkId=94648)  
 [<span data-ttu-id="f5d05-259">建立自訂的 TraceListener</span><span class="sxs-lookup"><span data-stu-id="f5d05-259">Creating a Custom TraceListener</span></span>](https://go.microsoft.com/fwlink/?LinkId=96239)
