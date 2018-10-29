---
title: 在 Visual Studio 中建立 Windows 服務應用程式
ms.date: 09/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows service applications, walkthroughs
- Windows service applications, creating
ms.assetid: e24d8a3d-edc6-485c-b6e0-5672d91fb607
author: ghogen
ms.openlocfilehash: 79447ede354de104607117f657182023a2e57127
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123666"
---
# <a name="walkthrough-create-a-windows-service-app"></a><span data-ttu-id="b9391-102">逐步解說：建立 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="b9391-102">Walkthrough: Create a Windows service app</span></span>

<span data-ttu-id="b9391-103">本文示範如何在 Visual Studio 中建立簡單的 Windows 服務應用程式，以將訊息寫入至事件記錄。</span><span class="sxs-lookup"><span data-stu-id="b9391-103">This article demonstrates how to create a simple Windows service app in Visual Studio that writes messages to an event log.</span></span>

## <a name="create-a-service"></a><span data-ttu-id="b9391-104">建立服務</span><span class="sxs-lookup"><span data-stu-id="b9391-104">Create a service</span></span>

<span data-ttu-id="b9391-105">首先，請建立專案並設定服務正常運作所需的值。</span><span class="sxs-lookup"><span data-stu-id="b9391-105">To begin, create the project and set values that are required for the service to function correctly.</span></span>

1. <span data-ttu-id="b9391-106">在 Visual Studio 中，從功能表列選擇 [檔案] > [新增] > [專案] (或按 **Ctrl**+**Shift**+**N**)，以開啟 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b9391-106">In Visual Studio, on the menu bar, choose **File** > **New** > **Project** (or press **Ctrl**+**Shift**+**N**) to open the **New Project** dialog.</span></span>

2. <span data-ttu-id="b9391-107">瀏覽至 [Windows 服務] 專案範本並加以選取。</span><span class="sxs-lookup"><span data-stu-id="b9391-107">Navigate to and select the **Windows Service** project template.</span></span> <span data-ttu-id="b9391-108">展開 [已安裝] > [Visual C#] 或 [Visual Basic] > [Windows 桌面]，或右上方的搜尋方塊中輸入 **Windows 服務**。</span><span class="sxs-lookup"><span data-stu-id="b9391-108">Expand **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, or type **Windows Service** in the search box on the upper right.</span></span>

   ![Visual Studio 新增專案對話方塊中的 Windows 服務範本](media/new-project-dialog.png)

   > [!NOTE]
   > <span data-ttu-id="b9391-110">如果您未看到 **Windows 服務**範本，您可能需要安裝 **.NET 桌面開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="b9391-110">If you don't see the **Windows Service** template, you may need to install the **.NET desktop development** workload.</span></span> <span data-ttu-id="b9391-111">在 [新增專案] 對話方塊中，按一下左下方顯示為 [開啟 Visual Studio 安裝程式] 的連結。</span><span class="sxs-lookup"><span data-stu-id="b9391-111">In the **New Project** dialog, click the link that says **Open Visual Studio Installer** on the lower left.</span></span> <span data-ttu-id="b9391-112">在 [Visual Studio Installer] 中，選取 [.NET 桌面開發] 工作負載，然後選擇 [修改]。</span><span class="sxs-lookup"><span data-stu-id="b9391-112">In **Visual Studio Installer**, select the **.NET desktop development** workload and then choose **Modify**.</span></span>

3. <span data-ttu-id="b9391-113">將專案命名為 **MyNewService**，然後選擇 [確定]。</span><span class="sxs-lookup"><span data-stu-id="b9391-113">Name the project **MyNewService**, and then choose **OK**.</span></span>

   <span data-ttu-id="b9391-114">專案範本會包含繼承自 <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> 且名為 `Service1` 的元件類別。</span><span class="sxs-lookup"><span data-stu-id="b9391-114">The project template includes a component class named `Service1` that inherits from <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b9391-115">其中包含大部分的基本服務程式碼，例如啟動服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9391-115">It includes much of the basic service code, such as the code to start the service.</span></span>

## <a name="rename-the-service"></a><span data-ttu-id="b9391-116">重新命名服務</span><span class="sxs-lookup"><span data-stu-id="b9391-116">Rename the service</span></span>

<span data-ttu-id="b9391-117">將服務 **Service1** 重新命名為 **MyNewService**。</span><span class="sxs-lookup"><span data-stu-id="b9391-117">Rename the service from **Service1** to **MyNewService**.</span></span>

1. <span data-ttu-id="b9391-118">在 Service1.cs (或 Service1.vb) 的 [設計] 檢視中，按一下**切換至程式碼檢視**的連結。</span><span class="sxs-lookup"><span data-stu-id="b9391-118">In the **Design** view for Service1.cs (or Service1.vb), click the link to **switch to code view**.</span></span> <span data-ttu-id="b9391-119">以滑鼠右鍵按一下 **Service1**，並從內容功能表中選取 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="b9391-119">Right-click on **Service1** and select **Rename** from the context menu.</span></span> <span data-ttu-id="b9391-120">輸入 **MyNewService**，然後按 **Enter** 鍵或按一下 [套用]。</span><span class="sxs-lookup"><span data-stu-id="b9391-120">Enter **MyNewService** and then press **Enter** or click **Apply**.</span></span>

2. <span data-ttu-id="b9391-121">在 **Service1.cs [Design]** 或 **Service1.vb [Design]** 的 [屬性] 視窗中，將 **ServiceName** 值變更為 **MyNewService**。</span><span class="sxs-lookup"><span data-stu-id="b9391-121">In the **Properties** window for **Service1.cs [Design]** or **Service1.vb [Design]**, change the **ServiceName** value to **MyNewService**.</span></span>

3. <span data-ttu-id="b9391-122">在**方案總管**中，將 **Service1.cs** 重新命名為 **MyNewService.cs**，或將 **Service1.vb** 重新命名為 **MyNewService.vb**。</span><span class="sxs-lookup"><span data-stu-id="b9391-122">In **Solution Explorer**, rename **Service1.cs** to **MyNewService.cs**, or rename **Service1.vb** to **MyNewService.vb**.</span></span>

## <a name="add-features-to-the-service"></a><span data-ttu-id="b9391-123">在服務中新增功能</span><span class="sxs-lookup"><span data-stu-id="b9391-123">Add features to the service</span></span>

<span data-ttu-id="b9391-124">在本節中，您要將自訂事件記錄檔加入 Windows 服務中。</span><span class="sxs-lookup"><span data-stu-id="b9391-124">In this section, you add a custom event log to the Windows service.</span></span> <span data-ttu-id="b9391-125">事件記錄檔與 Windows 服務毫無關聯。</span><span class="sxs-lookup"><span data-stu-id="b9391-125">Event logs are not associated in any way with Windows services.</span></span> <span data-ttu-id="b9391-126"><xref:System.Diagnostics.EventLog> 元件在此處用來當做可新增至 Windows 服務的元件類型範例。</span><span class="sxs-lookup"><span data-stu-id="b9391-126">The <xref:System.Diagnostics.EventLog> component is used here as an example of the type of component you can add to a Windows service.</span></span>

### <a name="add-custom-event-log-functionality"></a><span data-ttu-id="b9391-127">新增自訂事件記錄功能</span><span class="sxs-lookup"><span data-stu-id="b9391-127">Add custom event log functionality</span></span>

1. <span data-ttu-id="b9391-128">在 **方案總管中**中，開啟 **MyNewService.cs** 或 **MyNewService.vb**的內容功能表，然後選擇 [設計工具檢視] 。</span><span class="sxs-lookup"><span data-stu-id="b9391-128">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="b9391-129">從 [ **工具箱** ] 的 [ **元件**] 區段，將 <xref:System.Diagnostics.EventLog> 元件拖曳至設計工具中。</span><span class="sxs-lookup"><span data-stu-id="b9391-129">From the **Components** section of the **Toolbox**, drag an <xref:System.Diagnostics.EventLog> component to the designer.</span></span>

3. <span data-ttu-id="b9391-130">在 [方案總管] 中，開啟 **MyNewService.cs** 或 **MyNewService.vb**的內容功能表，然後選擇 [檢視程式碼] 。</span><span class="sxs-lookup"><span data-stu-id="b9391-130">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Code**.</span></span>

4. <span data-ttu-id="b9391-131">編輯建構函式以定義自訂事件記錄：</span><span class="sxs-lookup"><span data-stu-id="b9391-131">Edit the constructor to define a custom event log:</span></span>

   ```csharp
   public MyNewService()
   {
        InitializeComponent();

        eventLog1 = new System.Diagnostics.EventLog();
        if (!System.Diagnostics.EventLog.SourceExists("MySource"))
        {
            System.Diagnostics.EventLog.CreateEventSource(
                "MySource", "MyNewLog");
        }
        eventLog1.Source = "MySource";
        eventLog1.Log = "MyNewLog";
    }
   ```

   [!code-vb[VbRadconService#2](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#2)]

### <a name="define-what-occurs-when-the-service-starts"></a><span data-ttu-id="b9391-132">定義服務啟動時所執行的動作</span><span class="sxs-lookup"><span data-stu-id="b9391-132">Define what occurs when the service starts</span></span>

<span data-ttu-id="b9391-133">在程式碼編輯器中，找出在您建立專案時自動覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b9391-133">In the code editor, locate the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method that was automatically overridden when you created the project.</span></span> <span data-ttu-id="b9391-134">新增會在服務啟動時在事件記錄中寫入項目的一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="b9391-134">Add a line of code that writes an entry to the event log when the service starts:</span></span>

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

<span data-ttu-id="b9391-135">服務應用程式設計為長時間執行，因此它通常會輪詢或監視系統中的一些項目。</span><span class="sxs-lookup"><span data-stu-id="b9391-135">A service application is designed to be long-running, so it usually polls or monitors something in the system.</span></span> <span data-ttu-id="b9391-136">監視工作是在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中設定的。</span><span class="sxs-lookup"><span data-stu-id="b9391-136">The monitoring is set up in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span> <span data-ttu-id="b9391-137">但是， <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 實際上並不進行監視的工作。</span><span class="sxs-lookup"><span data-stu-id="b9391-137">However, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> doesn’t actually do the monitoring.</span></span> <span data-ttu-id="b9391-138">服務的作業開始後， <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法就必須傳回作業系統。</span><span class="sxs-lookup"><span data-stu-id="b9391-138">The <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method must return to the operating system after the service's operation has begun.</span></span> <span data-ttu-id="b9391-139">它不能永遠迴圈或阻斷。</span><span class="sxs-lookup"><span data-stu-id="b9391-139">It must not loop forever or block.</span></span> <span data-ttu-id="b9391-140">若要設定簡單的輪詢機制，您可以如下述使用 <xref:System.Timers.Timer?displayProperty=nameWithType> 元件：在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中，在元件上設定參數，然後再將 <xref:System.Timers.Timer.Enabled%2A> 屬性設定為 `true`.</span><span class="sxs-lookup"><span data-stu-id="b9391-140">To set up a simple polling mechanism, you can use the <xref:System.Timers.Timer?displayProperty=nameWithType> component as follows: In the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, set parameters on the component, and then set the <xref:System.Timers.Timer.Enabled%2A> property to `true`.</span></span> <span data-ttu-id="b9391-141">計時器會定期引發程式碼中的事件，這時候您的服務就可執行本身的監視工作。</span><span class="sxs-lookup"><span data-stu-id="b9391-141">The timer raises events in your code periodically, at which time your service could do its monitoring.</span></span> <span data-ttu-id="b9391-142">您可以使用下列程式碼來執行這項操作：</span><span class="sxs-lookup"><span data-stu-id="b9391-142">You can use the following code to do this:</span></span>

```csharp
// Set up a timer that triggers every minute.
System.Timers.Timer timer = new System.Timers.Timer();
timer.Interval = 60000; // 60 seconds
timer.Elapsed += new System.Timers.ElapsedEventHandler(this.OnTimer);
timer.Start();
```

```vb
' Set up a timer that triggers every minute.
Dim timer As System.Timers.Timer = New System.Timers.Timer()
timer.Interval = 60000 ' 60 seconds
AddHandler timer.Elapsed, AddressOf Me.OnTimer
timer.Start()
```

<span data-ttu-id="b9391-143">將成員變數加入至類別。</span><span class="sxs-lookup"><span data-stu-id="b9391-143">Add a member variable to the class.</span></span> <span data-ttu-id="b9391-144">針對下一個要寫入事件記錄檔的事件，它將包含事件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9391-144">It contains the identifier of the next event to write into the event log.</span></span>

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

<span data-ttu-id="b9391-145">新增用來處理計時器事件的新方法：</span><span class="sxs-lookup"><span data-stu-id="b9391-145">Add a new method to handle the timer event:</span></span>

```csharp
public void OnTimer(object sender, System.Timers.ElapsedEventArgs args)
{
    // TODO: Insert monitoring activities here.
    eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId++);
}
```

```vb
Private Sub OnTimer(sender As Object, e As Timers.ElapsedEventArgs)
    ' TODO: Insert monitoring activities here.
    eventLog1.WriteEntry("Monitoring the System", EventLogEntryType.Information, eventId)
    eventId = eventId + 1
End Sub
```

<span data-ttu-id="b9391-146">您可能想要使用背景工作執行緒執行工作，而不是在主執行緒上執行所有工作。</span><span class="sxs-lookup"><span data-stu-id="b9391-146">You might want to perform tasks by using background worker threads instead of running all your work on the main thread.</span></span> <span data-ttu-id="b9391-147">如需詳細資訊，請參閱<xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="b9391-147">For more information, see <xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>.</span></span>

### <a name="define-what-occurs-when-the-service-is-stopped"></a><span data-ttu-id="b9391-148">定義服務停止時所執行的動作</span><span class="sxs-lookup"><span data-stu-id="b9391-148">Define what occurs when the service is stopped</span></span>

<span data-ttu-id="b9391-149">在 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法中，新增會在服務停止時在事件記錄中新增項目的一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="b9391-149">Add a line of code to the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method that adds an entry to the event log when the service is stopped:</span></span>

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a><span data-ttu-id="b9391-150">為服務定義其他動作</span><span class="sxs-lookup"><span data-stu-id="b9391-150">Define other actions for the service</span></span>

<span data-ttu-id="b9391-151">您可以覆寫 <xref:System.ServiceProcess.ServiceBase.OnPause%2A>、<xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> 方法，以定義額外的元件處理方式。</span><span class="sxs-lookup"><span data-stu-id="b9391-151">You can override the <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>, and <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> methods to define additional processing for your component.</span></span> <span data-ttu-id="b9391-152">下列程式碼範例示範如何覆寫 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b9391-152">The following code shows how you can override the <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> method:</span></span>

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

<span data-ttu-id="b9391-153">當 Windows 服務由 <xref:System.Configuration.Install.Installer> 類別安裝時，必須發生一些自訂的動作。</span><span class="sxs-lookup"><span data-stu-id="b9391-153">Some custom actions have to occur when a Windows service is installed by the <xref:System.Configuration.Install.Installer> class.</span></span> <span data-ttu-id="b9391-154">Visual Studio 可建立專供 Windows 服務使用的安裝程式，並將它們加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="b9391-154">Visual Studio can create these installers specifically for a Windows service and add them to your project.</span></span>

## <a name="set-service-status"></a><span data-ttu-id="b9391-155">設定服務狀態</span><span class="sxs-lookup"><span data-stu-id="b9391-155">Set service status</span></span>

<span data-ttu-id="b9391-156">服務將它們的狀態報告給服務控制管理員，讓使用者也可以知道服務是否運作正常。</span><span class="sxs-lookup"><span data-stu-id="b9391-156">Services report their status to the Service Control Manager, so that users can tell whether a service is functioning correctly.</span></span> <span data-ttu-id="b9391-157">根據預設，繼承自 <xref:System.ServiceProcess.ServiceBase> 的服務，會報告一組有限的狀態設定，包括「已停止」、「已暫停」及「執行中」。</span><span class="sxs-lookup"><span data-stu-id="b9391-157">By default, services that inherit from <xref:System.ServiceProcess.ServiceBase> report a limited set of status settings, including Stopped, Paused, and Running.</span></span> <span data-ttu-id="b9391-158">如果服務需要一些時間才啟動，則報告「開始暫止」狀態可能會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="b9391-158">If a service takes a little while to start up, it might be helpful to report a Start Pending status.</span></span> <span data-ttu-id="b9391-159">您也可以將呼叫的程式碼新增至 Windows [SetServiceStatus 函式](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)，以實作「開始暫止」和「停止暫止」狀態設定。</span><span class="sxs-lookup"><span data-stu-id="b9391-159">You can also implement the Start Pending and Stop Pending status settings by adding code that calls into the Windows [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus).</span></span>

<span data-ttu-id="b9391-160">若要實作服務暫止狀態：</span><span class="sxs-lookup"><span data-stu-id="b9391-160">To implement service pending status:</span></span>

1. <span data-ttu-id="b9391-161">在 MyNewService.cs 或 MyNewService.vb 檔案中，為 <xref:System.Runtime.InteropServices?displayProperty=nameWithType> 命名空間新增 `using` 陳述式或 `Imports` 宣告：</span><span class="sxs-lookup"><span data-stu-id="b9391-161">Add a `using` statement or `Imports` declaration for the <xref:System.Runtime.InteropServices?displayProperty=nameWithType> namespace in the MyNewService.cs or MyNewService.vb file:</span></span>

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. <span data-ttu-id="b9391-162">將下列程式碼加入宣告 `ServiceState` 值的 MyNewService.cs，且加入您將在平台叫用呼叫中使用的狀態結構中：</span><span class="sxs-lookup"><span data-stu-id="b9391-162">Add the following code to MyNewService.cs to declare the `ServiceState` values and to add a structure for the status, which you'll use in a platform invoke call:</span></span>

    ```csharp
    public enum ServiceState
    {
        SERVICE_STOPPED = 0x00000001,
        SERVICE_START_PENDING = 0x00000002,
        SERVICE_STOP_PENDING = 0x00000003,
        SERVICE_RUNNING = 0x00000004,
        SERVICE_CONTINUE_PENDING = 0x00000005,
        SERVICE_PAUSE_PENDING = 0x00000006,
        SERVICE_PAUSED = 0x00000007,
    }

    [StructLayout(LayoutKind.Sequential)]
    public struct ServiceStatus
    {
        public int dwServiceType;
        public ServiceState dwCurrentState;
        public int dwControlsAccepted;
        public int dwWin32ExitCode;
        public int dwServiceSpecificExitCode;
        public int dwCheckPoint;
        public int dwWaitHint;
    };
    ```

    ```vb
    Public Enum ServiceState
        SERVICE_STOPPED = 1
        SERVICE_START_PENDING = 2
        SERVICE_STOP_PENDING = 3
        SERVICE_RUNNING = 4
        SERVICE_CONTINUE_PENDING = 5
        SERVICE_PAUSE_PENDING = 6
        SERVICE_PAUSED = 7
    End Enum

    <StructLayout(LayoutKind.Sequential)>
    Public Structure ServiceStatus
        Public dwServiceType As Long
        Public dwCurrentState As ServiceState
        Public dwControlsAccepted As Long
        Public dwWin32ExitCode As Long
        Public dwServiceSpecificExitCode As Long
        Public dwCheckPoint As Long
        Public dwWaitHint As Long
    End Structure
    ```

3. <span data-ttu-id="b9391-163">接著，在 `MyNewService` 類別中，使用[平台叫用](../interop/consuming-unmanaged-dll-functions.md)宣告 [SetServiceStatus 函式](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)：</span><span class="sxs-lookup"><span data-stu-id="b9391-163">Now, in the `MyNewService` class, declare the [SetServiceStatus function](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) by using [platform invoke](../interop/consuming-unmanaged-dll-functions.md):</span></span>

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. <span data-ttu-id="b9391-164">若要實作「開始暫止」狀態，請將下列程式碼加入至 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法開頭：</span><span class="sxs-lookup"><span data-stu-id="b9391-164">To implement the Start Pending status, add the following code to the beginning of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method:</span></span>

    ```csharp
    // Update the service state to Start Pending.
    ServiceStatus serviceStatus = new ServiceStatus();
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING;
    serviceStatus.dwWaitHint = 100000;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Start Pending.
    Dim serviceStatus As ServiceStatus = New ServiceStatus()
    serviceStatus.dwCurrentState = ServiceState.SERVICE_START_PENDING
    serviceStatus.dwWaitHint = 100000
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

5. <span data-ttu-id="b9391-165">在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法結尾處加入程式碼，以將狀態設定為「執行中」。</span><span class="sxs-lookup"><span data-stu-id="b9391-165">Add code to set the status to Running at the end of the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method.</span></span>

    ```csharp
    // Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING;
    SetServiceStatus(this.ServiceHandle, ref serviceStatus);
    ```

    ```vb
    ' Update the service state to Running.
    serviceStatus.dwCurrentState = ServiceState.SERVICE_RUNNING
    SetServiceStatus(Me.ServiceHandle, serviceStatus)
    ```

6. <span data-ttu-id="b9391-166">(選擇性) 為 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法重複這個程序。</span><span class="sxs-lookup"><span data-stu-id="b9391-166">(Optional) Repeat this procedure for the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="b9391-167">[服務控制管理員](/windows/desktop/Services/service-control-manager)會使用 [SERVICE_STATUS 結構](/windows/desktop/api/winsvc/ns-winsvc-_service_status)的 `dwWaitHint` 和 `dwCheckpoint` 成員來判斷等候啟動或關閉 Windows 服務的時間。</span><span class="sxs-lookup"><span data-stu-id="b9391-167">The [Service Control Manager](/windows/desktop/Services/service-control-manager) uses the `dwWaitHint` and `dwCheckpoint` members of the [SERVICE_STATUS structure](/windows/desktop/api/winsvc/ns-winsvc-_service_status) to determine how much time to wait for a Windows service to start or shut down.</span></span> <span data-ttu-id="b9391-168">如果您的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法需長時間執行，則您可以使用遞增的 `dwCheckPoint` 值再次呼叫 [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)，以要求更多時間。</span><span class="sxs-lookup"><span data-stu-id="b9391-168">If your <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods run long, your service can request more time by calling [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus) again with an incremented `dwCheckPoint` value.</span></span>

## <a name="add-installers-to-the-service"></a><span data-ttu-id="b9391-169">將安裝程式新增至服務</span><span class="sxs-lookup"><span data-stu-id="b9391-169">Add installers to the service</span></span>

<span data-ttu-id="b9391-170">您必須先安裝 Windows 服務，使其註冊至服務控制管理員，才能執行此服務。</span><span class="sxs-lookup"><span data-stu-id="b9391-170">Before you can run a Windows service, you need to install it, which registers it with the Service Control Manager.</span></span> <span data-ttu-id="b9391-171">您可以將安裝程式加入至處理註冊詳細資料的專案。</span><span class="sxs-lookup"><span data-stu-id="b9391-171">You can add installers to your project that handle the registration details.</span></span>

1. <span data-ttu-id="b9391-172">在 **方案總管中**中，開啟 **MyNewService.cs** 或 **MyNewService.vb**的內容功能表，然後選擇 [設計工具檢視] 。</span><span class="sxs-lookup"><span data-stu-id="b9391-172">In **Solution Explorer**, open the context menu for **MyNewService.cs** or **MyNewService.vb**, and then choose **View Designer**.</span></span>

2. <span data-ttu-id="b9391-173">按一下設計工具的背景以選取服務本身，而不是服務的內容。</span><span class="sxs-lookup"><span data-stu-id="b9391-173">Click the background of the designer to select the service itself, instead of any of its contents.</span></span>

3. <span data-ttu-id="b9391-174">開啟設計工具視窗的內容功能表 (如果您使用指標裝置，以滑鼠右鍵按一下視窗)，然後選擇 [加入安裝程式] 。</span><span class="sxs-lookup"><span data-stu-id="b9391-174">Open the context menu for the designer window (if you’re using a pointing device, right-click inside the window), and then choose **Add Installer**.</span></span>

   <span data-ttu-id="b9391-175">依預設會將包含兩個安裝程式的元件類別加入您的專案中。</span><span class="sxs-lookup"><span data-stu-id="b9391-175">By default, a component class that contains two installers is added to your project.</span></span> <span data-ttu-id="b9391-176">元件命名為 **ProjectInstaller**，而其所包含的安裝程式分別為服務的安裝程式和服務相關處理序的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="b9391-176">The component is named **ProjectInstaller**, and the installers it contains are the installer for your service and the installer for the service's associated process.</span></span>

4. <span data-ttu-id="b9391-177">在 **ProjectInstaller** 的 [設計] 檢視中，選擇 **serviceInstaller1** (針對 Visual C# 專案) 或 **ServiceInstaller1** (針對 Visual Basic 專案)。</span><span class="sxs-lookup"><span data-stu-id="b9391-177">In **Design** view for **ProjectInstaller**, choose **serviceInstaller1** for a Visual C# project, or **ServiceInstaller1** for a Visual Basic project.</span></span>

5. <span data-ttu-id="b9391-178">在 [屬性]  視窗中，請確定 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性已設為 **MyNewService**。</span><span class="sxs-lookup"><span data-stu-id="b9391-178">In the **Properties** window, make sure the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to **MyNewService**.</span></span>

6. <span data-ttu-id="b9391-179">將 **描述** 屬性設定一些文字，例如 "A sample service"。</span><span class="sxs-lookup"><span data-stu-id="b9391-179">Set the **Description** property to some text, such as "A sample service".</span></span> <span data-ttu-id="b9391-180">這段文字會出現在 [服務] 視窗中，並協助使用者識別服務，以及了解它的用途。</span><span class="sxs-lookup"><span data-stu-id="b9391-180">This text appears in the Services window and helps the user identify the service and understand what it’s used for.</span></span>

7. <span data-ttu-id="b9391-181">將 <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> 屬性設定為您想要出現在 [服務] 視窗的 [名稱]  欄中的文字。</span><span class="sxs-lookup"><span data-stu-id="b9391-181">Set the <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> property to the text that you want to appear in the Services window in the **Name** column.</span></span> <span data-ttu-id="b9391-182">例如，您可以輸入 "MyNewService Display Name"。</span><span class="sxs-lookup"><span data-stu-id="b9391-182">For example, you can enter "MyNewService Display Name".</span></span> <span data-ttu-id="b9391-183">這個名稱可以和 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性不同，因為這是由系統使用的名稱 (例如，當您使用 `net start` 命令來啟動您的服務)。</span><span class="sxs-lookup"><span data-stu-id="b9391-183">This name can be different from the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property, which is the name used by the system (for example, when you use the `net start` command to start your service).</span></span>

8. <span data-ttu-id="b9391-184">將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為 <xref:System.ServiceProcess.ServiceStartMode.Automatic>。</span><span class="sxs-lookup"><span data-stu-id="b9391-184">Set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to <xref:System.ServiceProcess.ServiceStartMode.Automatic>.</span></span>

     <span data-ttu-id="b9391-185">![Windows 服務的安裝程式屬性](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span><span class="sxs-lookup"><span data-stu-id="b9391-185">![Installer Properties for a Windows service](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")</span></span>

9. <span data-ttu-id="b9391-186">在設計工具中，選擇 **serviceProcessInstaller1** (針對 Visual C# 專案) 或 **ServiceProcessInstaller1** (針對 Visual Basic 專案)。</span><span class="sxs-lookup"><span data-stu-id="b9391-186">In the designer, choose **serviceProcessInstaller1** for a Visual C# project, or **ServiceProcessInstaller1** for a Visual Basic project.</span></span> <span data-ttu-id="b9391-187">將 <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> 屬性設定為 <xref:System.ServiceProcess.ServiceAccount.LocalSystem>。</span><span class="sxs-lookup"><span data-stu-id="b9391-187">Set the <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> property to <xref:System.ServiceProcess.ServiceAccount.LocalSystem>.</span></span> <span data-ttu-id="b9391-188">如此即會安裝服務，並使用本機服務帳戶執行。</span><span class="sxs-lookup"><span data-stu-id="b9391-188">This causes the service to be installed and to run using the local system account.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b9391-189"><xref:System.ServiceProcess.ServiceAccount.LocalSystem> 帳戶具有概括性的使用權限，包括寫入事件記錄檔的能力。</span><span class="sxs-lookup"><span data-stu-id="b9391-189">The <xref:System.ServiceProcess.ServiceAccount.LocalSystem> account has broad permissions, including the ability to write to the event log.</span></span> <span data-ttu-id="b9391-190">因此，請謹慎使用這個帳戶，因為它會增加您遭受惡意軟體攻擊的風險。</span><span class="sxs-lookup"><span data-stu-id="b9391-190">Use this account with caution, because it might increase your risk of attacks from malicious software.</span></span> <span data-ttu-id="b9391-191">至於其他工作，建議使用 <xref:System.ServiceProcess.ServiceAccount.LocalService> 帳戶，可在本機電腦上做為沒有權限的使用者，並提供匿名認證給任何遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="b9391-191">For other tasks, consider using the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, which acts as a non-privileged user on the local computer and presents anonymous credentials to any remote server.</span></span> <span data-ttu-id="b9391-192">如果您嘗試使用 <xref:System.ServiceProcess.ServiceAccount.LocalService> 帳戶，因為需要寫入事件記錄檔的權限，所以這個範例會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9391-192">This example fails if you try to use the <xref:System.ServiceProcess.ServiceAccount.LocalService> account, because it needs permission to write to the event log.</span></span>

<span data-ttu-id="b9391-193">如需安裝程式的詳細資訊，請參閱[操作說明：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="b9391-193">For more information about installers, see [How to: Add Installers to Your service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>

## <a name="optional-set-startup-parameters"></a><span data-ttu-id="b9391-194">(選擇性) 設定啟動參數</span><span class="sxs-lookup"><span data-stu-id="b9391-194">(Optional) Set startup parameters</span></span>

<span data-ttu-id="b9391-195">Windows 服務就像任何其他可執行檔，可以接受命令列引數或啟動參數。</span><span class="sxs-lookup"><span data-stu-id="b9391-195">A Windows service, like any other executable, can accept command-line arguments, or startup parameters.</span></span> <span data-ttu-id="b9391-196">當您加入程式碼以處理啟動參數時，使用者可以使用 Windows 控制台中的 [服務] 視窗，以自己的自訂啟動參數啟動您的服務。</span><span class="sxs-lookup"><span data-stu-id="b9391-196">When you add code to process startup parameters, users can start your service with their own custom startup parameters by using the Services window in the Windows Control Panel.</span></span> <span data-ttu-id="b9391-197">不過，這些啟動參數不會保留到下次服務啟動時。</span><span class="sxs-lookup"><span data-stu-id="b9391-197">However, these startup parameters are not persisted the next time the service starts.</span></span> <span data-ttu-id="b9391-198">若要永久設定啟動參數，可以在登錄中設定它們，如這個程序所示範。</span><span class="sxs-lookup"><span data-stu-id="b9391-198">To set startup parameters permanently, you can set them in the registry, as shown in this procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="b9391-199">決定加入啟動參數之前，請考慮那是否為將資訊傳遞給您服務的最佳的方式。</span><span class="sxs-lookup"><span data-stu-id="b9391-199">Before you decide to add startup parameters, consider whether that is the best way to pass information to your service.</span></span> <span data-ttu-id="b9391-200">雖然啟動參數很容易使用及剖析，使用者也可以輕易地覆寫它們，但在沒有文件時，使用者可能較難探索和使用它們。</span><span class="sxs-lookup"><span data-stu-id="b9391-200">Although startup parameters are easy to use and to parse, and users can easily override them, they might be harder for users to discover and use without documentation.</span></span> <span data-ttu-id="b9391-201">一般而言，如果您的服務需要較多的啟動參數，您應該考慮改用登錄或組態檔。</span><span class="sxs-lookup"><span data-stu-id="b9391-201">Generally, if your service requires more than just a few startup parameters, you should consider using the registry or a configuration file instead.</span></span> <span data-ttu-id="b9391-202">每個 Windows 服務在 **HKLM\System\CurrentControlSet\services** 下都有登錄項目。</span><span class="sxs-lookup"><span data-stu-id="b9391-202">Every Windows service has an entry in the registry under **HKLM\System\CurrentControlSet\services**.</span></span> <span data-ttu-id="b9391-203">在服務的機碼下，您可以使用 **Parameters** 子機碼，來儲存您服務可以存取的資訊。</span><span class="sxs-lookup"><span data-stu-id="b9391-203">Under the service's key, you can use the **Parameters** subkey to store information that your service can access.</span></span> <span data-ttu-id="b9391-204">對於 Windows 服務，您可以用與其他類型的程式相同的方式來使用應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="b9391-204">You can use application configuration files for a Windows service the same way you do for other types of programs.</span></span> <span data-ttu-id="b9391-205">如需範例程式碼，請參閱 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>。</span><span class="sxs-lookup"><span data-stu-id="b9391-205">For example code, see <xref:System.Configuration.ConfigurationManager.AppSettings%2A>.</span></span>

<span data-ttu-id="b9391-206">若要新增啟動參數：</span><span class="sxs-lookup"><span data-stu-id="b9391-206">To add startup parameters:</span></span>

1. <span data-ttu-id="b9391-207">在 Program.cs 或 MyNewService.Designer.vb 的 `Main` 方法中，新增要傳至服務建構函式的輸入參數：</span><span class="sxs-lookup"><span data-stu-id="b9391-207">In the `Main` method in Program.cs or in MyNewService.Designer.vb, add an input parameter to pass to the service constructor:</span></span>

   ```csharp
   static void Main(string[] args)
   {
       ServiceBase[] ServicesToRun;
       ServicesToRun = new ServiceBase[]
       {
           new MyNewService(args)
       };
       ServiceBase.Run(ServicesToRun);
   }
   ```

   ```vb
   Shared Sub Main(ByVal cmdArgs() As String)
       Dim ServicesToRun() As System.ServiceProcess.ServiceBase = New System.ServiceProcess.ServiceBase() {New MyNewServiceVB(cmdArgs)}
       System.ServiceProcess.ServiceBase.Run(ServicesToRun)
   End Sub
   ```

2. <span data-ttu-id="b9391-208">變更 `MyNewService` 建構函式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b9391-208">Change the `MyNewService` constructor as follows:</span></span>

   ```csharp
   public MyNewService(string[] args)
   {
       InitializeComponent();

        string eventSourceName = "MySource";
        string logName = "MyNewLog";

        if (args.Length > 0)
        {
            eventSourceName = args[0];
        }

        if (args.Length > 1)
        {
            logName = args[1];
        }

        eventLog1 = new System.Diagnostics.EventLog();

        if (!System.Diagnostics.EventLog.SourceExists(eventSourceName))
        {
            System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName);
        }

        eventLog1.Source = eventSourceName;
        eventLog1.Log = logName;
   }
   ```

   ```vb
   Public Sub New(ByVal cmdArgs() As String)
       InitializeComponent()
       Dim eventSourceName As String = "MySource"
       Dim logName As String = "MyNewLog"
       If (cmdArgs.Count() > 0) Then
           eventSourceName = cmdArgs(0)
       End If
       If (cmdArgs.Count() > 1) Then
           logName = cmdArgs(1)
       End If
       eventLog1 = New System.Diagnostics.EventLog()
       If (Not System.Diagnostics.EventLog.SourceExists(eventSourceName)) Then
           System.Diagnostics.EventLog.CreateEventSource(eventSourceName, logName)
       End If
       eventLog1.Source = eventSourceName
       eventLog1.Log = logName
   End Sub
   ```

   <span data-ttu-id="b9391-209">如果沒有提供引數，此程式碼會根據提供的啟動參數，或使用預設值，設定事件來源和記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="b9391-209">This code sets the event source and log name according to the supplied startup parameters, or uses default values if no arguments are supplied.</span></span>

3. <span data-ttu-id="b9391-210">若要指定命令列引數，請將下列程式碼加入 ProjectInstaller.cs 或 ProjectInstaller.vb 中的 `ProjectInstaller` 類別：</span><span class="sxs-lookup"><span data-stu-id="b9391-210">To specify the command-line arguments, add the following code to the `ProjectInstaller` class in ProjectInstaller.cs or ProjectInstaller.vb:</span></span>

   ```csharp
   protected override void OnBeforeInstall(IDictionary savedState)
   {
       string parameter = "MySource1\" \"MyLogFile1";
       Context.Parameters["assemblypath"] = "\"" + Context.Parameters["assemblypath"] + "\" \"" + parameter + "\"";
       base.OnBeforeInstall(savedState);
   }
   ```

   ```vb
   Protected Overrides Sub OnBeforeInstall(ByVal savedState As IDictionary)
       Dim parameter As String = "MySource1"" ""MyLogFile1"
       Context.Parameters("assemblypath") = """" + Context.Parameters("assemblypath") + """ """ + parameter + """"
       MyBase.OnBeforeInstall(savedState)
   End Sub
   ```

   <span data-ttu-id="b9391-211">這個程式碼會藉由新增預設參數值修改 **ImagePath** 登錄機碼，其中通常包含 Windows 服務可執行檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b9391-211">This code modifies the **ImagePath** registry key, which typically contains the full path to the executable for the Windows service, by adding the default parameter values.</span></span> <span data-ttu-id="b9391-212">需要以引號括住路徑 (以及每個個別參數) 才能正確地啟動服務。</span><span class="sxs-lookup"><span data-stu-id="b9391-212">The quotation marks around the path (and around each individual parameter) are required for the service to start up correctly.</span></span> <span data-ttu-id="b9391-213">若要變更此 Windows 服務的啟動參數，使用者可以變更 **ImagePath** 登錄機碼中指定的參數，雖然較好的方式是以程式設計方式變更，並以易懂的方式將功能公開給使用者 (例如，在管理或組態公用程式中)。</span><span class="sxs-lookup"><span data-stu-id="b9391-213">To change the startup parameters for this Windows service, users can change the parameters given in the **ImagePath** registry key, although the better way is to change it programmatically and expose the functionality to users in a friendly way (for example, in a management or configuration utility).</span></span>

## <a name="build-the-service"></a><span data-ttu-id="b9391-214">建置服務</span><span class="sxs-lookup"><span data-stu-id="b9391-214">Build the service</span></span>

1. <span data-ttu-id="b9391-215">在 [方案總管] 中，開啟專案的內容功能表，然後選擇 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="b9391-215">In **Solution Explorer**, open the context menu for your project, and then choose **Properties**.</span></span>

   <span data-ttu-id="b9391-216">專案的屬性頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b9391-216">The property pages for your project appear.</span></span>

2. <span data-ttu-id="b9391-217">在 [應用程式] 索引標籤的 [啟始物件] 清單中，選擇 **MyNewService.Program**。</span><span class="sxs-lookup"><span data-stu-id="b9391-217">On the **Application** tab, in the **Startup object** list, choose **MyNewService.Program**.</span></span>

3. <span data-ttu-id="b9391-218">在 [方案總管] 中開啟您專案的內容功能表，然後選擇 [建置] 以建置專案 (或按 **Ctrl**+**Shift**+**B**)。</span><span class="sxs-lookup"><span data-stu-id="b9391-218">In **Solution Explorer**, open the context menu for your project, and then choose **Build** to build the project (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="install-the-service"></a><span data-ttu-id="b9391-219">安裝服務</span><span class="sxs-lookup"><span data-stu-id="b9391-219">Install the service</span></span>

<span data-ttu-id="b9391-220">建置 Windows 服務之後，您就可以安裝它了。</span><span class="sxs-lookup"><span data-stu-id="b9391-220">Now that you've built the Windows service, you can install it.</span></span> <span data-ttu-id="b9391-221">若要安裝 Windows 服務，您在要安裝服務的電腦上必須具有系統管理員認證。</span><span class="sxs-lookup"><span data-stu-id="b9391-221">To install a Windows service, you must have administrator credentials on the computer on which you're installing it.</span></span>

1. <span data-ttu-id="b9391-222">以系統管理認證開啟 [Visual Studio 的開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="b9391-222">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span> <span data-ttu-id="b9391-223">如果您使用滑鼠，請在 Windows 的 [開始] 功能表中以滑鼠右鍵按一下 [VS 2017 的開發人員命令提示字元] ，然後選擇 [更多] > [以系統管理員身分執行]。</span><span class="sxs-lookup"><span data-stu-id="b9391-223">If you’re using a mouse, right-click on **Developer Command Prompt for VS 2017** in the Windows Start menu, and then choose **More** > **Run as Administrator**.</span></span>

2. <span data-ttu-id="b9391-224">在 [開發人員命令提示字元] 視窗中，瀏覽至包含專案輸出的資料夾 (預設為專案的 *\bin\Debug* 子目錄)。</span><span class="sxs-lookup"><span data-stu-id="b9391-224">In the **Developer Command Prompt** window, navigate to the folder that contains your project's output (by default, it's the *\bin\Debug* subdirectory of your project).</span></span>

3. <span data-ttu-id="b9391-225">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b9391-225">Enter the following command:</span></span>

    ```shell
    installutil.exe MyNewService.exe
    ```

    <span data-ttu-id="b9391-226">如果成功安裝服務，**installutil.exe** 會報告成功訊息。</span><span class="sxs-lookup"><span data-stu-id="b9391-226">If the service installs successfully, **installutil.exe** reports success.</span></span> <span data-ttu-id="b9391-227">如果系統找不到 **InstallUtil.exe**，請確定它存在於您的電腦中。</span><span class="sxs-lookup"><span data-stu-id="b9391-227">If the system could not find **InstallUtil.exe**, make sure that it exists on your computer.</span></span> <span data-ttu-id="b9391-228">此工具會透過 .NET Framework 安裝至資料夾 *%windir%\Microsoft.NET\Framework[64]\\[Framework 版本]*。</span><span class="sxs-lookup"><span data-stu-id="b9391-228">This tool is installed with the .NET Framework to the folder *%windir%\Microsoft.NET\Framework[64]\\[framework version]*.</span></span> <span data-ttu-id="b9391-229">例如，32 位元版本的預設路徑是 *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*。</span><span class="sxs-lookup"><span data-stu-id="b9391-229">For example, the default path for the 32-bit version is *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*.</span></span>

    <span data-ttu-id="b9391-230">如果 **installutil.exe** 程序回報失敗，請檢查安裝記錄以找出原因。</span><span class="sxs-lookup"><span data-stu-id="b9391-230">If the **installutil.exe** process reports failure, check the install log to find out why.</span></span> <span data-ttu-id="b9391-231">根據預設，記錄檔與服務可執行檔位於相同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b9391-231">By default the log is in the same folder as the service executable.</span></span> <span data-ttu-id="b9391-232">若 `ProjectInstaller` 類別中沒有 <xref:System.ComponentModel.RunInstallerAttribute> 類別、屬性未設為 **true**，或 `ProjectInstaller` 類別未標記為**公用**，則安裝可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="b9391-232">The installation can fail if  the <xref:System.ComponentModel.RunInstallerAttribute> Class is not present on the `ProjectInstaller` class, if the attribute is not set to **true**, or if the `ProjectInstaller` class is not marked **public**.</span></span>

<span data-ttu-id="b9391-233">如需詳細資訊，請參閱 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b9391-233">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="start-and-run-the-service"></a><span data-ttu-id="b9391-234">啟動並執行服務</span><span class="sxs-lookup"><span data-stu-id="b9391-234">Start and run the service</span></span>

1. <span data-ttu-id="b9391-235">在 Windows 中，開啟 [服務] 桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9391-235">In Windows, open the **Services** desktop app.</span></span> <span data-ttu-id="b9391-236">按 **Windows**+**R** 以開啟 [執行] 方塊，並輸入 **services.msc**，然後按 **Enter** 鍵或按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="b9391-236">Press **Windows**+**R** to open the **Run** box, and then enter **services.msc** and press **Enter** or click **OK**.</span></span>

     <span data-ttu-id="b9391-237">您應該會看到您的服務列在 [服務] 中，並以您為其設定的顯示名稱按字母順序顯示。</span><span class="sxs-lookup"><span data-stu-id="b9391-237">You should see your service listed in **Services**, displayed alphabetically by the display name that you set for it.</span></span>

     ![在 [服務] 視窗中的 MyNewService。](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. <span data-ttu-id="b9391-239">在 [服務] 中，開啟您服務的捷徑功能表，然後選擇 [開始]。</span><span class="sxs-lookup"><span data-stu-id="b9391-239">In **Services**, open the shortcut menu for your service, and then choose **Start**.</span></span>

3. <span data-ttu-id="b9391-240">若要停止服務，請開啟服務的捷徑功能表，然後選擇 [停止]。</span><span class="sxs-lookup"><span data-stu-id="b9391-240">To stop the service, open the shortcut menu for the service, and then choose **Stop**.</span></span>

4. <span data-ttu-id="b9391-241">(選擇性) 您可以從命令列中，使用命令 `net start ServiceName` 和 `net stop ServiceName` 來啟動及停止您的服務。</span><span class="sxs-lookup"><span data-stu-id="b9391-241">(Optional) From the command line, you can use the commands `net start ServiceName` and `net stop ServiceName` to start and stop your service.</span></span>

### <a name="verify-the-event-log-output-of-your-service"></a><span data-ttu-id="b9391-242">確認服務的事件記錄輸出</span><span class="sxs-lookup"><span data-stu-id="b9391-242">Verify the event log output of your service</span></span>

1. <span data-ttu-id="b9391-243">藉由在 Windows 工作列上的搜尋方塊中輸入**事件檢視器**，然後從搜尋結果中選取 [事件檢視器]，以開啟 [事件檢視器]。</span><span class="sxs-lookup"><span data-stu-id="b9391-243">Open **Event Viewer** by starting to type **Event Viewer** in the search box on the Windows task bar, and then selecting **Event Viewer** from the search results.</span></span>

   > [!TIP]
   > <span data-ttu-id="b9391-244">在 Visual Studio 中，您可以開啟 [伺服器總管] (鍵盤：**Ctrl**+**Alt**+**S**)，然後展開本機電腦的 [事件記錄] 節點，以存取事件記錄。</span><span class="sxs-lookup"><span data-stu-id="b9391-244">In Visual Studio, you can access event logs by opening **Server Explorer** (Keyboard: **Ctrl**+**Alt**+**S**) and expanding the **Event Logs** node for the local computer.</span></span>

2. <span data-ttu-id="b9391-245">在 [事件檢視器] 中，展開 [應用程式及服務記錄]。</span><span class="sxs-lookup"><span data-stu-id="b9391-245">In **Event Viewer**, expand **Applications and Services Logs**.</span></span>

3. <span data-ttu-id="b9391-246">找出 **MyNewLog** 的清單 (如果您依照選擇性程序加入命令列引數，則為 **MyLogFile1**)，並加以展開。</span><span class="sxs-lookup"><span data-stu-id="b9391-246">Locate the listing for **MyNewLog** (or **MyLogFile1**, if you followed the optional procedure to add command-line arguments) and expand it.</span></span> <span data-ttu-id="b9391-247">您應該會看到服務已執行兩個動作 (啟動和停止) 的項目。</span><span class="sxs-lookup"><span data-stu-id="b9391-247">You should see entries for the two actions (start and stop) that your service performed.</span></span>

     ![使用事件檢視器查看事件記錄項目](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a><span data-ttu-id="b9391-249">解除安裝服務</span><span class="sxs-lookup"><span data-stu-id="b9391-249">Uninstall the service</span></span>

1. <span data-ttu-id="b9391-250">以系統管理認證開啟 [Visual Studio 的開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="b9391-250">Open **Developer Command Prompt for Visual Studio** with administrative credentials.</span></span>

2. <span data-ttu-id="b9391-251">在命令提示字元視窗中，瀏覽至包含專案輸出的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b9391-251">In the command prompt window, navigate to the folder that contains your project's output.</span></span>

3. <span data-ttu-id="b9391-252">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b9391-252">Enter the following command:</span></span>

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   <span data-ttu-id="b9391-253">如果服務已成功解除安裝，**installutil.exe** 會回報已成功移除您的服務。</span><span class="sxs-lookup"><span data-stu-id="b9391-253">If the service uninstalls successfully, **installutil.exe** reports that your service was successfully removed.</span></span> <span data-ttu-id="b9391-254">如需詳細資訊，請參閱 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b9391-254">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b9391-255">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b9391-255">Next steps</span></span>

<span data-ttu-id="b9391-256">您已建立服務，現在您可以建立獨立安裝程式，讓其他人用來安裝您的 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="b9391-256">Now that you've created the service, you might want to create a standalone setup program that others can use to install your Windows service.</span></span> <span data-ttu-id="b9391-257">ClickOnce 不支援 Windows 服務，但您可以使用 [WiX 工具組](http://wixtoolset.org/)來建立 Windows 服務的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="b9391-257">ClickOnce doesn't support Windows services, but you can use the [WiX Toolset](http://wixtoolset.org/) to create an installer for a Windows service.</span></span> <span data-ttu-id="b9391-258">如需相關資訊，請參閱[建立安裝程式套件](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client)。</span><span class="sxs-lookup"><span data-stu-id="b9391-258">For other ideas, see [Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client).</span></span>

<span data-ttu-id="b9391-259">您可以瀏覽 <xref:System.ServiceProcess.ServiceController> 元件的用法，這可讓您將命令傳送至已安裝的服務。</span><span class="sxs-lookup"><span data-stu-id="b9391-259">You might explore the use of a <xref:System.ServiceProcess.ServiceController> component, which enables you to send commands to the service you've installed.</span></span>

<span data-ttu-id="b9391-260">您可以使用安裝程式，在安裝應用程式時建立事件記錄檔，而不是在應用程式執行時才建立事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b9391-260">You can use an installer to create an event log when the application is installed instead of creating the event log when the application runs.</span></span> <span data-ttu-id="b9391-261">此外在應用程式解除安裝時，安裝程式會刪除事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b9391-261">Additionally, the event log will be deleted by the installer when the application is uninstalled.</span></span> <span data-ttu-id="b9391-262">如需詳細資訊，請參閱 <xref:System.Diagnostics.EventLogInstaller> 參考頁面。</span><span class="sxs-lookup"><span data-stu-id="b9391-262">For more information, see the <xref:System.Diagnostics.EventLogInstaller> reference page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9391-263">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9391-263">See also</span></span>

- [<span data-ttu-id="b9391-264">Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="b9391-264">Windows service applications</span></span>](../../../docs/framework/windows-services/index.md)
- [<span data-ttu-id="b9391-265">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="b9391-265">Introduction to Windows service applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="b9391-266">操作方式：偵錯 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="b9391-266">How to: Debug Windows service applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- <span data-ttu-id="b9391-267">[服務 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="b9391-267">[Services (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx)</span></span>
