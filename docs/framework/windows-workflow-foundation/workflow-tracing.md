---
title: 工作流程追蹤
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 7bca78b24963d94bfa0f2e2245a677b7dce455c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933446"
---
# <a name="workflow-tracing"></a><span data-ttu-id="9062a-102">工作流程追蹤</span><span class="sxs-lookup"><span data-stu-id="9062a-102">Workflow Tracing</span></span>
<span data-ttu-id="9062a-103">工作流程追蹤提供使用 .NET Framework 追蹤接聽程式擷取診斷資訊的方式。</span><span class="sxs-lookup"><span data-stu-id="9062a-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="9062a-104">如果偵測到應用程式的問題，可以啟用追蹤，等到問題解決再停用追蹤。</span><span class="sxs-lookup"><span data-stu-id="9062a-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="9062a-105">您可以運用兩種方式啟用工作流程的偵錯追蹤。</span><span class="sxs-lookup"><span data-stu-id="9062a-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="9062a-106">您可以使用事件追蹤檢視器加以設定，也可以使用 <xref:System.Diagnostics>，將追蹤事件傳送至檔案。</span><span class="sxs-lookup"><span data-stu-id="9062a-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="9062a-107">啟用 ETW 中的偵錯追蹤</span><span class="sxs-lookup"><span data-stu-id="9062a-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="9062a-108">若要使用 ETW 啟用追蹤，請啟用事件檢視器中的偵錯通道：</span><span class="sxs-lookup"><span data-stu-id="9062a-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="9062a-109">巡覽至事件檢視器中的分析與偵錯記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9062a-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="9062a-110">在事件檢視器的樹狀檢視中, 流覽至**事件檢視器 > 的應用程式和服務記錄-> Microsoft > Windows > 應用程式伺服器-應用**程式。</span><span class="sxs-lookup"><span data-stu-id="9062a-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="9062a-111">以滑鼠右鍵按一下 [**應用程式伺服器-應用程式**], 然後選取 [ **View-> 顯示分析和偵錯工具記錄**]。</span><span class="sxs-lookup"><span data-stu-id="9062a-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="9062a-112">以滑鼠右鍵按一下 [ **Debug** ], 然後選取 [**啟用記錄**]。</span><span class="sxs-lookup"><span data-stu-id="9062a-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="9062a-113">當工作流程執行偵錯並將追蹤發出至 ETW 偵錯頻道時，即可在事件檢視器中檢視這些追蹤。</span><span class="sxs-lookup"><span data-stu-id="9062a-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="9062a-114">流覽至**事件檢視器 > 的應用程式和服務記錄-> Microsoft > Windows-> 應用程式伺服器-應用**程式。</span><span class="sxs-lookup"><span data-stu-id="9062a-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="9062a-115">以滑鼠右鍵按一下 [ **Debug** ], 然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="9062a-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="9062a-116">預設的分析追蹤緩衝區大小只有 4 KB；建議您將大小增加至 32 KB。</span><span class="sxs-lookup"><span data-stu-id="9062a-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="9062a-117">若要執行這項操作，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="9062a-117">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="9062a-118">在目前的 Framework 目錄 (例如 C:\Windows\Microsoft.NET\Framework\v4.0.21203) 中執行下列命令：`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="9062a-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="9062a-119">將 ApplicationServer \<中的 bufferSize > 值變更為32。</span><span class="sxs-lookup"><span data-stu-id="9062a-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="9062a-120">在目前的 Framework 目錄 (例如 C:\Windows\Microsoft.NET\Framework\v4.0.21203) 中執行下列命令：`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="9062a-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9062a-121">如果您使用 .NET Framework 4 用戶端設定檔, 您必須先從 .NET Framework 4 目錄執行下列命令, 以註冊 ETW 資訊清單:`ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="9062a-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="9062a-122">啟用以 System.Diagnostics 進行偵錯追蹤</span><span class="sxs-lookup"><span data-stu-id="9062a-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="9062a-123">這些接聽程式可在工作流程應用程式的 App.config 檔案或工作流程服務的 Web.config 檔案中設定。</span><span class="sxs-lookup"><span data-stu-id="9062a-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="9062a-124">在此範例中, 會將[TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424)設定為將追蹤資訊儲存至目前目錄中的 mytracelog.txt。</span><span class="sxs-lookup"><span data-stu-id="9062a-124">In this example, a [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9062a-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9062a-125">See also</span></span>

- [<span data-ttu-id="9062a-126">Windows Server App Fabric 監視</span><span class="sxs-lookup"><span data-stu-id="9062a-126">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="9062a-127">使用 App Fabric 監視應用程式</span><span class="sxs-lookup"><span data-stu-id="9062a-127">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
