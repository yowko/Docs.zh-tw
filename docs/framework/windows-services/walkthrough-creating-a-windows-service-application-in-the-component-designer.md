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
manager: douge
ms.openlocfilehash: 27acdac5d34b96dd04fec1bb763edec9077ff928
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46493603"
---
# <a name="walkthrough-create-a-windows-service-app"></a>逐步解說：建立 Windows 服務應用程式

本文示範如何在 Visual Studio 中建立簡單的 Windows 服務應用程式，以將訊息寫入至事件記錄。

## <a name="create-a-service"></a>建立服務

首先，請建立專案並設定服務正常運作所需的值。

1. 在 Visual Studio 中，從功能表列選擇 [檔案] > [新增] > [專案] (或按 **Ctrl**+**Shift**+**N**)，以開啟 [新增專案] 對話方塊。

2. 瀏覽至 [Windows 服務] 專案範本並加以選取。 展開 [已安裝] > [Visual C#] 或 [Visual Basic] > [Windows 桌面]，或右上方的搜尋方塊中輸入 **Windows 服務**。

   ![Visual Studio 新增專案對話方塊中的 Windows 服務範本](media/new-project-dialog.png)

   > [!NOTE]
   > 如果您未看到 **Windows 服務**範本，您可能需要安裝 **.NET 桌面開發**工作負載。 在 [新增專案] 對話方塊中，按一下左下方顯示為 [開啟 Visual Studio 安裝程式] 的連結。 在 [Visual Studio Installer] 中，選取 [.NET 桌面開發] 工作負載，然後選擇 [修改]。

3. 將專案命名為 **MyNewService**，然後選擇 [確定]。

   專案範本會包含繼承自 <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> 且名為 `Service1` 的元件類別。 其中包含大部分的基本服務程式碼，例如啟動服務的程式碼。

## <a name="rename-the-service"></a>重新命名服務

將服務 **Service1** 重新命名為 **MyNewService**。

1. 在 Service1.cs (或 Service1.vb) 的 [設計] 檢視中，按一下**切換至程式碼檢視**的連結。 以滑鼠右鍵按一下 **Service1**，並從內容功能表中選取 [重新命名]。 輸入 **MyNewService**，然後按 **Enter** 鍵或按一下 [套用]。

2. 在 **Service1.cs [Design]** 或 **Service1.vb [Design]** 的 [屬性] 視窗中，將 **ServiceName** 值變更為 **MyNewService**。

3. 在**方案總管**中，將 **Service1.cs** 重新命名為 **MyNewService.cs**，或將 **Service1.vb** 重新命名為 **MyNewService.vb**。

## <a name="add-features-to-the-service"></a>在服務中新增功能

在本節中，您要將自訂事件記錄檔加入 Windows 服務中。 事件記錄檔與 Windows 服務毫無關聯。 <xref:System.Diagnostics.EventLog> 元件在此處用來當做可新增至 Windows 服務的元件類型範例。

### <a name="add-custom-event-log-functionality"></a>新增自訂事件記錄功能

1. 在 **方案總管中**中，開啟 **MyNewService.cs** 或 **MyNewService.vb**的內容功能表，然後選擇 [設計工具檢視] 。

2. 從 [ **工具箱** ] 的 [ **元件**] 區段，將 <xref:System.Diagnostics.EventLog> 元件拖曳至設計工具中。

3. 在 [方案總管] 中，開啟 **MyNewService.cs** 或 **MyNewService.vb**的內容功能表，然後選擇 [檢視程式碼] 。

4. 編輯建構函式以定義自訂事件記錄：

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

### <a name="define-what-occurs-when-the-service-starts"></a>定義服務啟動時所執行的動作

在程式碼編輯器中，找出在您建立專案時自動覆寫的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法。 新增會在服務啟動時在事件記錄中寫入項目的一行程式碼：

[!code-csharp[VbRadconService#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#3)]
[!code-vb[VbRadconService#3](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#3)]

服務應用程式設計為長時間執行，因此它通常會輪詢或監視系統中的一些項目。 監視工作是在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中設定的。 但是， <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 實際上並不進行監視的工作。 服務的作業開始後， <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法就必須傳回作業系統。 它不能永遠迴圈或阻斷。 若要設定簡單的輪詢機制，您可以如下述使用 <xref:System.Timers.Timer?displayProperty=nameWithType> 元件：在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中，在元件上設定參數，然後再將 <xref:System.Timers.Timer.Enabled%2A> 屬性設定為 `true`。 計時器會定期引發程式碼中的事件，這時候您的服務就可執行本身的監視工作。 您可以使用下列程式碼來執行這項操作：

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

將成員變數加入至類別。 針對下一個要寫入事件記錄檔的事件，它將包含事件的識別碼。

```csharp
private int eventId = 1;
```

```vb
Private eventId As Integer = 1
```

新增用來處理計時器事件的新方法：

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

您可能想要使用背景工作執行緒執行工作，而不是在主執行緒上執行所有工作。 如需詳細資訊，請參閱<xref:System.ComponentModel.BackgroundWorker?displayProperty=fullName>。

### <a name="define-what-occurs-when-the-service-is-stopped"></a>定義服務停止時所執行的動作

在 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法中，新增會在服務停止時在事件記錄中新增項目的一行程式碼：

```csharp
eventLog1.WriteEntry("In OnStop.");
```

[!code-vb[VbRadconService#4](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#4)]

### <a name="define-other-actions-for-the-service"></a>為服務定義其他動作

您可以覆寫 <xref:System.ServiceProcess.ServiceBase.OnPause%2A>、<xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> 方法，以定義額外的元件處理方式。 下列程式碼範例示範如何覆寫 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 方法。

[!code-csharp[VbRadconService#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#5)]
[!code-vb[VbRadconService#5](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#5)]

當 Windows 服務由 <xref:System.Configuration.Install.Installer> 類別安裝時，必須發生一些自訂的動作。 Visual Studio 可建立專供 Windows 服務使用的安裝程式，並將它們加入至您的專案。

## <a name="set-service-status"></a>設定服務狀態

服務將它們的狀態報告給服務控制管理員，讓使用者也可以知道服務是否運作正常。 根據預設，繼承自 <xref:System.ServiceProcess.ServiceBase> 的服務，會報告一組有限的狀態設定，包括「已停止」、「已暫停」及「執行中」。 如果服務需要一些時間才啟動，則報告「開始暫止」狀態可能會很有幫助。 您也可以將呼叫的程式碼新增至 Windows [SetServiceStatus 函式](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)，以實作「開始暫止」和「停止暫止」狀態設定。

若要實作服務暫止狀態：

1. 在 MyNewService.cs 或 MyNewService.vb 檔案中，為 <xref:System.Runtime.InteropServices?displayProperty=nameWithType> 命名空間新增 `using` 陳述式或 `Imports` 宣告：

    ```csharp
    using System.Runtime.InteropServices;
    ```

    ```vb
    Imports System.Runtime.InteropServices
    ```

2. 將下列程式碼加入宣告 `ServiceState` 值的 MyNewService.cs，且加入您將在平台叫用呼叫中使用的狀態結構中：

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

3. 接著，在 `MyNewService` 類別中，使用[平台叫用](../interop/consuming-unmanaged-dll-functions.md)宣告 [SetServiceStatus 函式](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)：

    ```csharp
    [DllImport("advapi32.dll", SetLastError = true)]
    private static extern bool SetServiceStatus(System.IntPtr handle, ref ServiceStatus serviceStatus);
    ```

    ```vb
    Declare Auto Function SetServiceStatus Lib "advapi32.dll" (ByVal handle As IntPtr, ByRef serviceStatus As ServiceStatus) As Boolean
    ```

4. 若要實作「開始暫止」狀態，請將下列程式碼加入至 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法開頭：

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

5. 在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法結尾處加入程式碼，以將狀態設定為「執行中」。

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

6. (選擇性) 為 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法重複這個程序。

> [!NOTE]
> [服務控制管理員](/windows/desktop/Services/service-control-manager)會使用 [SERVICE_STATUS 結構](/windows/desktop/api/winsvc/ns-winsvc-_service_status)的 `dwWaitHint` 和 `dwCheckpoint` 成員來判斷等候啟動或關閉 Windows 服務的時間。 如果您的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法需長時間執行，則您可以使用遞增的 `dwCheckPoint` 值再次呼叫 [SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)，以要求更多時間。

## <a name="add-installers-to-the-service"></a>將安裝程式新增至服務

您必須先安裝 Windows 服務，使其註冊至服務控制管理員，才能執行此服務。 您可以將安裝程式加入至處理註冊詳細資料的專案。

1. 在 **方案總管中**中，開啟 **MyNewService.cs** 或 **MyNewService.vb**的內容功能表，然後選擇 [設計工具檢視] 。

2. 按一下設計工具的背景以選取服務本身，而不是服務的內容。

3. 開啟設計工具視窗的內容功能表 (如果您使用指標裝置，以滑鼠右鍵按一下視窗)，然後選擇 [加入安裝程式] 。

   依預設會將包含兩個安裝程式的元件類別加入您的專案中。 元件命名為 **ProjectInstaller**，而其所包含的安裝程式分別為服務的安裝程式和服務相關處理序的安裝程式。

4. 在 **ProjectInstaller** 的 [設計] 檢視中，選擇 **serviceInstaller1** (針對 Visual C# 專案) 或 **ServiceInstaller1** (針對 Visual Basic 專案)。

5. 在 [屬性]  視窗中，請確定 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性已設為 **MyNewService**。

6. 將 **描述** 屬性設定一些文字，例如 "A sample service"。 這段文字會出現在 [服務] 視窗中，並協助使用者識別服務，以及了解它的用途。

7. 將 <xref:System.ServiceProcess.ServiceInstaller.DisplayName%2A> 屬性設定為您想要出現在 [服務] 視窗的 [名稱]  欄中的文字。 例如，您可以輸入 "MyNewService Display Name"。 這個名稱可以和 <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> 屬性不同，因為這是由系統使用的名稱 (例如，當您使用 `net start` 命令來啟動您的服務)。

8. 將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為 <xref:System.ServiceProcess.ServiceStartMode.Automatic>。

     ![Windows 服務的安裝程式屬性](../../../docs/framework/windows-services/media/windowsservice-installerproperties.PNG "WindowsService_InstallerProperties")

9. 在設計工具中，選擇 **serviceProcessInstaller1** (針對 Visual C# 專案) 或 **ServiceProcessInstaller1** (針對 Visual Basic 專案)。 將 <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> 屬性設定為 <xref:System.ServiceProcess.ServiceAccount.LocalSystem>。 如此即會安裝服務，並使用本機服務帳戶執行。

    > [!IMPORTANT]
    > <xref:System.ServiceProcess.ServiceAccount.LocalSystem> 帳戶具有概括性的使用權限，包括寫入事件記錄檔的能力。 因此，請謹慎使用這個帳戶，因為它會增加您遭受惡意軟體攻擊的風險。 至於其他工作，建議使用 <xref:System.ServiceProcess.ServiceAccount.LocalService> 帳戶，可在本機電腦上做為沒有權限的使用者，並提供匿名認證給任何遠端伺服器。 如果您嘗試使用 <xref:System.ServiceProcess.ServiceAccount.LocalService> 帳戶，因為需要寫入事件記錄檔的權限，所以這個範例會失敗。

如需安裝程式的詳細資訊，請參閱[操作說明：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。

## <a name="optional-set-startup-parameters"></a>(選擇性) 設定啟動參數

Windows 服務就像任何其他可執行檔，可以接受命令列引數或啟動參數。 當您加入程式碼以處理啟動參數時，使用者可以使用 Windows 控制台中的 [服務] 視窗，以自己的自訂啟動參數啟動您的服務。 不過，這些啟動參數不會保留到下次服務啟動時。 若要永久設定啟動參數，可以在登錄中設定它們，如這個程序所示範。

> [!NOTE]
> 決定加入啟動參數之前，請考慮那是否為將資訊傳遞給您服務的最佳的方式。 雖然啟動參數很容易使用及剖析，使用者也可以輕易地覆寫它們，但在沒有文件時，使用者可能較難探索和使用它們。 一般而言，如果您的服務需要較多的啟動參數，您應該考慮改用登錄或組態檔。 每個 Windows 服務在 **HKLM\System\CurrentControlSet\services** 下都有登錄項目。 在服務的機碼下，您可以使用 **Parameters** 子機碼，來儲存您服務可以存取的資訊。 對於 Windows 服務，您可以用與其他類型的程式相同的方式來使用應用程式組態檔。 如需範例程式碼，請參閱 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>。

若要新增啟動參數：

1. 在 Program.cs 或 MyNewService.Designer.vb 的 `Main` 方法中，新增要傳至服務建構函式的輸入參數：

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

2. 變更 `MyNewService` 建構函式，如下所示：

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

   如果沒有提供引數，此程式碼會根據提供的啟動參數，或使用預設值，設定事件來源和記錄檔名稱。

3. 若要指定命令列引數，請將下列程式碼加入 ProjectInstaller.cs 或 ProjectInstaller.vb 中的 `ProjectInstaller` 類別：

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

   這個程式碼會藉由新增預設參數值修改 **ImagePath** 登錄機碼，其中通常包含 Windows 服務可執行檔的完整路徑。 需要以引號括住路徑 (以及每個個別參數) 才能正確地啟動服務。 若要變更此 Windows 服務的啟動參數，使用者可以變更 **ImagePath** 登錄機碼中指定的參數，雖然較好的方式是以程式設計方式變更，並以易懂的方式將功能公開給使用者 (例如，在管理或組態公用程式中)。

## <a name="build-the-service"></a>建置服務

1. 在 [方案總管] 中，開啟專案的內容功能表，然後選擇 [屬性] 。

   專案的屬性頁面隨即出現。

2. 在 [應用程式] 索引標籤的 [啟始物件] 清單中，選擇 **MyNewService.Program**。

3. 在 [方案總管] 中開啟您專案的內容功能表，然後選擇 [建置] 以建置專案 (或按 **Ctrl**+**Shift**+**B**)。

## <a name="install-the-service"></a>安裝服務

建置 Windows 服務之後，您就可以安裝它了。 若要安裝 Windows 服務，您在要安裝服務的電腦上必須具有系統管理員認證。

1. 以系統管理認證開啟 [Visual Studio 的開發人員命令提示字元]。 如果您使用滑鼠，請在 Windows 的 [開始] 功能表中以滑鼠右鍵按一下 [VS 2017 的開發人員命令提示字元] ，然後選擇 [更多] > [以系統管理員身分執行]。

2. 在 [開發人員命令提示字元] 視窗中，瀏覽至包含專案輸出的資料夾 (預設為專案的 *\bin\Debug* 子目錄)。

3. 輸入下列命令：

    ```shell
    installutil.exe MyNewService.exe
    ```

    如果成功安裝服務，**installutil.exe** 會報告成功訊息。 如果系統找不到 **InstallUtil.exe**，請確定它存在於您的電腦中。 此工具會透過 .NET Framework 安裝至資料夾 *%windir%\Microsoft.NET\Framework[64]\\[Framework 版本]*。 例如，32 位元版本的預設路徑是 *%windir%\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*。

    如果 **installutil.exe** 程序回報失敗，請檢查安裝記錄以找出原因。 根據預設，記錄檔與服務可執行檔位於相同的資料夾。 若 `ProjectInstaller` 類別中沒有 <xref:System.ComponentModel.RunInstallerAttribute> 類別、屬性未設為 **true**，或 `ProjectInstaller` 類別未標記為**公用**，則安裝可能會失敗。

如需詳細資訊，請參閱 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。

## <a name="start-and-run-the-service"></a>啟動並執行服務

1. 在 Windows 中，開啟 [服務] 桌面應用程式。 按 **Windows**+**R** 以開啟 [執行] 方塊，並輸入 **services.msc**，然後按 **Enter** 鍵或按一下 [確定]。

     您應該會看到您的服務列在 [服務] 中，並以您為其設定的顯示名稱按字母順序顯示。

     ![在 [服務] 視窗中的 MyNewService。](../../../docs/framework/windows-services/media/windowsservices-serviceswindow.PNG)

2. 在 [服務] 中，開啟您服務的捷徑功能表，然後選擇 [開始]。

3. 若要停止服務，請開啟服務的捷徑功能表，然後選擇 [停止]。

4. (選擇性) 您可以從命令列中，使用命令 `net start ServiceName` 和 `net stop ServiceName` 來啟動及停止您的服務。

### <a name="verify-the-event-log-output-of-your-service"></a>確認服務的事件記錄輸出

1. 藉由在 Windows 工作列上的搜尋方塊中輸入**事件檢視器**，然後從搜尋結果中選取 [事件檢視器]，以開啟 [事件檢視器]。

   > [!TIP]
   > 在 Visual Studio 中，您可以開啟 [伺服器總管] (鍵盤：**Ctrl**+**Alt**+**S**)，然後展開本機電腦的 [事件記錄] 節點，以存取事件記錄。

2. 在 [事件檢視器] 中，展開 [應用程式及服務記錄]。

3. 找出 **MyNewLog** 的清單 (如果您依照選擇性程序加入命令列引數，則為 **MyLogFile1**)，並加以展開。 您應該會看到服務已執行兩個動作 (啟動和停止) 的項目。

     ![使用事件檢視器查看事件記錄項目](../../../docs/framework/windows-services/media/windows-service-event-viewer.png)

## <a name="uninstall-the-service"></a>解除安裝服務

1. 以系統管理認證開啟 [Visual Studio 的開發人員命令提示字元]。

2. 在命令提示字元視窗中，瀏覽至包含專案輸出的資料夾。

3. 輸入下列命令：

    ```shell
    installutil.exe /u MyNewService.exe
    ```

   如果服務已成功解除安裝，**installutil.exe** 會回報已成功移除您的服務。 如需詳細資訊，請參閱 [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。

## <a name="next-steps"></a>後續步驟

您已建立服務，現在您可以建立獨立安裝程式，讓其他人用來安裝您的 Windows 服務。 ClickOnce 不支援 Windows 服務，但您可以使用 [WiX 工具組](http://wixtoolset.org/)來建立 Windows 服務的安裝程式。 如需相關資訊，請參閱[建立安裝程式套件](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client)。

您可以瀏覽 <xref:System.ServiceProcess.ServiceController> 元件的用法，這可讓您將命令傳送至已安裝的服務。

您可以使用安裝程式，在安裝應用程式時建立事件記錄檔，而不是在應用程式執行時才建立事件記錄檔。 此外在應用程式解除安裝時，安裝程式會刪除事件記錄檔。 如需詳細資訊，請參閱 <xref:System.Diagnostics.EventLogInstaller> 參考頁面。

## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式](../../../docs/framework/windows-services/index.md)
- [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [操作方式：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [服務 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms685141.aspx) \(英文\)
