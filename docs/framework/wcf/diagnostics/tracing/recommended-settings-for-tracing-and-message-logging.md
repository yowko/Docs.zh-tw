---
title: 追蹤與訊息記錄的建議設定
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 6e671762edb2d1ca71ce14cb6ef66c64e02bc297
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856091"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="1374c-102">追蹤與訊息記錄的建議設定</span><span class="sxs-lookup"><span data-stu-id="1374c-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="1374c-103">本主題將說明不同作業環境中，建議的追蹤和訊息記錄設定。</span><span class="sxs-lookup"><span data-stu-id="1374c-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="1374c-104">實際執行環境的建議設定</span><span class="sxs-lookup"><span data-stu-id="1374c-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="1374c-105">如果您使用 WCF 追蹤來源，請將實際執行環境的 `switchValue` 設為 Warning。</span><span class="sxs-lookup"><span data-stu-id="1374c-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="1374c-106">如果您使用 WCF `System.ServiceModel` 追蹤來源，請將 `switchValue` 屬性設為 `Warning` 以及將 `propagateActivity` 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="1374c-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="1374c-107">如果您使用的是使用者定義的追蹤來源，請將 `switchValue` 屬性設為 `Warning, ActivityTracing`。</span><span class="sxs-lookup"><span data-stu-id="1374c-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="1374c-108">這可以使用設定[編輯器工具（svcconfigeditor.exe）](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)手動完成。</span><span class="sxs-lookup"><span data-stu-id="1374c-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="1374c-109">如果您無法預測對效能的衝擊，則可在之前提到的所有案例中，將 `switchValue` 屬性設為 `Information`，如此就會產生相當大量的追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="1374c-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="1374c-110">以下範例將示範這些建議的設定。</span><span class="sxs-lookup"><span data-stu-id="1374c-110">The following example demonstrates these recommended settings.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="1374c-111">部署或偵錯的建議設定</span><span class="sxs-lookup"><span data-stu-id="1374c-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="1374c-112">針對部署或偵錯環境，請選擇用於使用者定義或 `Information` 追蹤來源的 `Verbose` 或 `ActivityTracing`，以及 `System.ServiceModel`。</span><span class="sxs-lookup"><span data-stu-id="1374c-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="1374c-113">若要增強偵錯功能，則應同時將額外的追蹤來源 (`System.ServiceModel.MessageLogging`) 加入組態中，以啟用訊息記錄。</span><span class="sxs-lookup"><span data-stu-id="1374c-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="1374c-114">請注意，`switchValue` 屬性不會影響此追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="1374c-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="1374c-115">以下範例將示範建議的設定，其中會使用利用了 `XmlWriterTraceListener` 的共用接聽項。</span><span class="sxs-lookup"><span data-stu-id="1374c-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="1374c-116">使用 WMI 修改設定</span><span class="sxs-lookup"><span data-stu-id="1374c-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="1374c-117">您可以使用 WMI 在執行階段變更組態設定 (藉由啟用組態中的 `wmiProviderEnabled` 屬性，如之前的組態範例中所示範)。</span><span class="sxs-lookup"><span data-stu-id="1374c-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="1374c-118">例如，您可以在 CIM Studio 中使用 WMI，將執行階段的追蹤來源層級從 Warning 變更為 Information。</span><span class="sxs-lookup"><span data-stu-id="1374c-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="1374c-119">您應注意的是，以此方式執行即時偵錯的效能成本可能會相當高。</span><span class="sxs-lookup"><span data-stu-id="1374c-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="1374c-120">如需使用 WMI 的詳細資訊，請參閱[使用 Windows Management Instrumentation 診斷](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1374c-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="1374c-121">啟用 ASP.NET 追蹤中的相互關聯事件</span><span class="sxs-lookup"><span data-stu-id="1374c-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="1374c-122">ASP.NET 事件不會設定相互關聯 ID (ActivityID)，除非 ASP.NET 事件追蹤開啟。</span><span class="sxs-lookup"><span data-stu-id="1374c-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="1374c-123">若要正確查看相互關聯事件，您必須在命令主控台中使用下列命令來開啟 ASP.NET 事件追蹤，方法是前往 [**開始**]、[**執行**]，然後輸入**cmd**，</span><span class="sxs-lookup"><span data-stu-id="1374c-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="1374c-124">若要關閉 ASP.NET 事件追蹤，請使用下列命令，</span><span class="sxs-lookup"><span data-stu-id="1374c-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="1374c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1374c-125">See also</span></span>

- [<span data-ttu-id="1374c-126">使用 Windows Management Instrumentation 進行診斷</span><span class="sxs-lookup"><span data-stu-id="1374c-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
