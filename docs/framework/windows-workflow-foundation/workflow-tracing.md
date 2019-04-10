---
title: 工作流程追蹤
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: cd53ed834fdacb639b38346dca831ef4c3e26337
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321662"
---
# <a name="workflow-tracing"></a><span data-ttu-id="8b106-102">工作流程追蹤</span><span class="sxs-lookup"><span data-stu-id="8b106-102">Workflow Tracing</span></span>
<span data-ttu-id="8b106-103">工作流程追蹤提供使用 .NET Framework 追蹤接聽程式擷取診斷資訊的方式。</span><span class="sxs-lookup"><span data-stu-id="8b106-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="8b106-104">如果偵測到應用程式的問題，可以啟用追蹤，等到問題解決再停用追蹤。</span><span class="sxs-lookup"><span data-stu-id="8b106-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="8b106-105">您可以運用兩種方式啟用工作流程的偵錯追蹤。</span><span class="sxs-lookup"><span data-stu-id="8b106-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="8b106-106">您可以使用事件追蹤檢視器加以設定，也可以使用 <xref:System.Diagnostics>，將追蹤事件傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="8b106-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="8b106-107">啟用 ETW 中的偵錯追蹤</span><span class="sxs-lookup"><span data-stu-id="8b106-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="8b106-108">若要使用 ETW 啟用追蹤，請啟用事件檢視器中的偵錯通道：</span><span class="sxs-lookup"><span data-stu-id="8b106-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="8b106-109">巡覽至事件檢視器中的分析與偵錯記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8b106-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="8b106-110">在樹狀檢視中 事件檢視器中，瀏覽至**事件檢視器-> 應用程式及服務記錄檔-> Microsoft-> Windows-> 應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8b106-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="8b106-111">以滑鼠右鍵按一下**應用程式伺服器-應用程式**，然後選取**檢視]-> [顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="8b106-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="8b106-112">以滑鼠右鍵按一下**偵錯**，然後選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="8b106-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="8b106-113">當工作流程執行偵錯並將追蹤發出至 ETW 偵錯頻道時，即可在事件檢視器中檢視這些追蹤。</span><span class="sxs-lookup"><span data-stu-id="8b106-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="8b106-114">瀏覽至**事件檢視器-> 應用程式及服務記錄檔]-> [Microsoft]-> [Windows]-> [應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8b106-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="8b106-115">以滑鼠右鍵按一下**偵錯**，然後選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="8b106-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="8b106-116">預設的分析追蹤緩衝區大小只有 4 KB；建議您將大小增加至 32 KB。</span><span class="sxs-lookup"><span data-stu-id="8b106-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="8b106-117">若要執行這項操作，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="8b106-117">To do this, perform the following steps.</span></span>  
  
    1.  <span data-ttu-id="8b106-118">目前的 framework 目錄 (例如 C:\Windows\Microsoft.NET\Framework\v4.0.21203) 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8b106-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203):</span></span> `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  <span data-ttu-id="8b106-119">變更\<bufferSize > 32 Windows.ApplicationServer.Applications.man 檔案中的值。</span><span class="sxs-lookup"><span data-stu-id="8b106-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  <span data-ttu-id="8b106-120">目前的 framework 目錄 (例如 C:\Windows\Microsoft.NET\Framework\v4.0.21203) 中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="8b106-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203):</span></span> `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  <span data-ttu-id="8b106-121">如果您使用.NET Framework 4 Client Profile，您必須先從.NET Framework 4 目錄執行下列命令註冊 ETW 資訊清單：</span><span class="sxs-lookup"><span data-stu-id="8b106-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory:</span></span> `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="8b106-122">啟用以 System.Diagnostics 進行偵錯追蹤</span><span class="sxs-lookup"><span data-stu-id="8b106-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="8b106-123">這些接聽程式可在工作流程應用程式的 App.config 檔案或工作流程服務的 Web.config 檔案中設定。</span><span class="sxs-lookup"><span data-stu-id="8b106-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="8b106-124">在此範例中， [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424)設定為將追蹤資訊儲存至目前目錄中的 MyTraceLog.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="8b106-124">In this example, a [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b106-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b106-125">See also</span></span>

- [<span data-ttu-id="8b106-126">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="8b106-126">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="8b106-127">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="8b106-127">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
