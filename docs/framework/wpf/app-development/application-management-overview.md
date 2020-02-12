---
title: 應用程式管理概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: dbc5bd9f699415fb47f21c6a45b1c58cfcff0f33
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124516"
---
# <a name="application-management-overview"></a>應用程式管理概觀

所有應用程式通常會共用一組適用於應用程式實作和管理的通用功能。 本主題提供建立和管理應用程式之 <xref:System.Windows.Application> 類別中的功能總覽。

## <a name="the-application-class"></a>Application 類別

在 WPF 中，通用應用程式範圍的功能會封裝在 <xref:System.Windows.Application> 類別中。 <xref:System.Windows.Application> 類別包含下列功能：

- 追蹤應用程式存留期並與其互動。

- 擷取及處理命令列參數。

- 偵測及回應未處理的例外狀況。

- 共用應用程式範圍的屬性和資源。

- 管理獨立應用程式中的視窗。

- 追蹤及管理瀏覽。

<a name="The_Application_Class"></a>

## <a name="how-to-perform-common-tasks-using-the-application-class"></a>如何使用 Application 類別執行一般工作

如果您對 <xref:System.Windows.Application> 類別的所有詳細資料不感興趣，下表會列出 <xref:System.Windows.Application> 的一些常見工作，以及如何完成這些作業。 您可以檢視相關的 API 和主題，來尋找詳細資訊和範例程式碼。

|工作|方法|
|----------|--------------|
|取得代表目前應用程式的物件|請使用 <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> 屬性。|
|將啟動畫面新增至應用程式|請參閱[將啟動顯示畫面新增至 WPF 應用程式](how-to-add-a-splash-screen-to-a-wpf-application.md)。|
|啟動應用程式|請使用 <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> 方法。|
|停止應用程式|使用 <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> 物件的 <xref:System.Windows.Application.Shutdown%2A> 方法。|
|從命令列取得引數|處理 <xref:System.Windows.Application.Startup?displayProperty=nameWithType> 事件並使用 <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> 屬性。 如需範例，請參閱 <xref:System.Windows.Application.Startup?displayProperty=nameWithType> 事件。|
|取得及設定應用程式結束代碼|在 <xref:System.Windows.Application.Exit?displayProperty=nameWithType> 事件處理常式中設定 <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> 屬性，或呼叫 <xref:System.Windows.Application.Shutdown%2A> 方法並傳入整數。|
|偵測及回應未處理的例外狀況|處理 <xref:System.Windows.Application.DispatcherUnhandledException> 事件。|
|取得及設定應用程式範圍的資源|請使用 <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> 屬性。|
|使用應用程式範圍的資源字典|請參閱[使用應用程式範圍的資源字典](how-to-use-an-application-scope-resource-dictionary.md)。|
|取得及設定應用程式範圍的屬性|請使用 <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> 屬性。|
|取得及儲存應用程式的狀態|請參閱[跨應用程式會話保存和還原應用程式範圍的屬性](persist-and-restore-application-scope-properties.md)。|
|管理非程式碼資料檔案，包括資源檔、內容檔案和來源網站檔案。|請參閱[WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)。|
|管理獨立應用程式中的視窗|請參閱 [WPF 視窗概觀](wpf-windows-overview.md)。|
|追蹤及管理瀏覽|請參閱[導覽總覽](navigation-overview.md)。|

<a name="The_Application_Definition"></a>

## <a name="the-application-definition"></a>應用程式定義

若要利用 <xref:System.Windows.Application> 類別的功能，您必須執行應用程式定義。 WPF 應用程式定義是衍生自 <xref:System.Windows.Application> 的類別，而且會使用特殊的 MSBuild 設定進行設定。

### <a name="implementing-an-application-definition"></a>實作應用程式定義

一般的 WPF 應用程式定義會同時使用標記和程式碼後置來執行。 這可讓您使用標記，以宣告方式設定應用程式屬性、資源和註冊事件，同時在程式碼後置中，處理事件及實作應用程式特定行為。

下列範例示範如何使用標記和程式碼後置，來實作應用程式定義：

[!code-xaml[ApplicationSnippets#ApplicationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]

[!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
[!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]

若要搭配使用標記檔案和程式碼後置檔案，下列情況必須成立：

- 在標記中，`Application` 元素必須包含 `x:Class` 屬性。 建立應用程式時，標記檔案中的 `x:Class` 存在，會導致 MSBuild 建立衍生自 <xref:System.Windows.Application> 的 `partial` 類別，且其名稱是由 `x:Class` 屬性所指定。 這需要新增 XAML 架構的 XML 命名空間宣告（`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`）。

- 在程式碼後置中，類別必須是 `partial` 類別，且名稱與標記中的 `x:Class` 屬性所指定相同，而且必須衍生自 <xref:System.Windows.Application>。 這可讓程式碼後置檔案與建立應用程式時為標記檔案產生的 `partial` 類別相關聯（請參閱[建立 WPF 應用程式](building-a-wpf-application-wpf.md)）。

> [!NOTE]
> 當您使用 Visual Studio 建立新的 WPF 應用程式專案或 WPF 瀏覽器應用程式專案時，預設會包含應用程式定義，並使用標記和程式碼後置來定義。

此程式碼是實作應用程式定義的最低需求。 不過，在建立和執行應用程式之前，必須先對應用程式定義進行其他的 MSBuild 設定。

### <a name="configuring-the-application-definition-for-msbuild"></a>設定 MSBuild 的應用程式定義

獨立應用程式和 XAML 瀏覽器應用程式（Xbap）需要先執行特定層級的基礎結構，才能執行。 此基礎結構的最重要部分是進入點。 當使用者啟動應用程式時，作業系統會呼叫進入點，這是用於啟動應用程式的已知函式。

傳統上，開發人員必須自行撰寫這段程式碼的一部分或全部 (視使用技術而定)。 不過，當應用程式定義的標記檔案設定為 MSBuild `ApplicationDefinition` 專案時，WPF 會為您產生此程式碼，如下列 MSBuild 專案檔所示：

```xml
<Project
  DefaultTargets="Build"
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  ...
  <ApplicationDefinition Include="App.xaml" />
  <Compile Include="App.xaml.cs" />
  ...
</Project>
```

由於程式碼後置檔案包含程式碼，因此會將它標示為 MSBuild `Compile` 專案，如同平常一般。

將這些 MSBuild 設定應用於應用程式定義的標記和程式碼後置檔案，會導致 MSBuild 產生如下所示的程式碼：

[!code-csharp[auto-generated-code](~/samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs)]
[!code-vb[auto-generated-code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb)]

產生的程式碼會以額外的基礎結構程式碼（包括 `Main`的進入點方法）來增強您的應用程式定義。 <xref:System.STAThreadAttribute> 屬性會套用至 `Main` 方法，以指出 WPF 應用程式的主要 UI 執行緒是 WPF 應用程式所需的 STA 執行緒。 呼叫時，`Main` 會先建立 `App` 的新實例，然後再呼叫 `InitializeComponent` 方法來註冊事件，並設定在標記中執行的屬性。 因為會為您產生 `InitializeComponent`，所以您不需要明確地從應用程式定義中呼叫 `InitializeComponent`，就像您針對 <xref:System.Windows.Controls.Page> 和 <xref:System.Windows.Window> 的執行所做的一樣。 最後，會呼叫 <xref:System.Windows.Application.Run%2A> 方法來啟動應用程式。

<a name="Getting_the_Current_Application"></a>

## <a name="getting-the-current-application"></a>取得目前的應用程式

由於 <xref:System.Windows.Application> 類別的功能會在應用程式之間共用，因此每個 <xref:System.AppDomain>只能有一個 <xref:System.Windows.Application> 類別的實例。 若要強制執行這項工作，<xref:System.Windows.Application> 類別會實作為單一類別（請參閱[在中C#執行 singleton ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650316(v=pandp.10))），這會建立本身的單一實例，並使用 `static`<xref:System.Windows.Application.Current%2A> 屬性為其提供共用存取。

下列程式碼顯示如何取得目前 <xref:System.AppDomain>之 <xref:System.Windows.Application> 物件的參考。

[!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]

<xref:System.Windows.Application.Current%2A> 會傳回 <xref:System.Windows.Application> 類別之實例的參考。 如果您想要 <xref:System.Windows.Application> 衍生類別的參考，則必須轉換 <xref:System.Windows.Application.Current%2A> 屬性的值，如下列範例所示。

[!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
[!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]

您可以在 <xref:System.Windows.Application> 物件存留期的任何時間點，檢查 <xref:System.Windows.Application.Current%2A> 的值。 不過，您應該要小心。 具現化 <xref:System.Windows.Application> 類別之後，<xref:System.Windows.Application> 物件的狀態會不一致的期間。 在這段期間，<xref:System.Windows.Application> 執行您的程式碼所需的各種初始化工作，包括建立應用程式基礎結構、設定屬性和註冊事件。 如果您嘗試在這段期間內使用 <xref:System.Windows.Application> 物件，您的程式碼可能會產生非預期的結果，特別是當它相依于所設定的各種 <xref:System.Windows.Application> 屬性時。

當 <xref:System.Windows.Application> 完成其初始化工作時，其存留期就會真正開始。

<a name="Application_Lifetime"></a>

## <a name="application-lifetime"></a>應用程式存留期

WPF 應用程式的存留期會由 <xref:System.Windows.Application> 所引發的數個事件加以標記，讓您知道應用程式何時啟動、已啟用並停用，而且已關閉。

<a name="Splash_Screen"></a>

### <a name="splash-screen"></a>啟動顯示畫面

從 .NET Framework 3.5 SP1 開始，您可以指定要在啟動視窗或啟動顯示*畫面*中使用的映射。 [<xref:System.Windows.SplashScreen>] 類別可讓您在應用程式載入時輕鬆顯示啟動視窗。 [<xref:System.Windows.SplashScreen>] 視窗隨即建立，並在呼叫 <xref:System.Windows.Application.Run%2A> 之前顯示。 如需詳細資訊，請參閱[應用程式啟動時間](../advanced/application-startup-time.md)和[將啟動顯示畫面新增至 WPF 應用程式](how-to-add-a-splash-screen-to-a-wpf-application.md)。

<a name="Starting_an_Application"></a>

### <a name="starting-an-application"></a>啟動應用程式

呼叫 <xref:System.Windows.Application.Run%2A> 並初始化應用程式之後，應用程式就已準備好執行。 這段時間是在引發 <xref:System.Windows.Application.Startup> 事件時表示：

[!code-csharp[Startup-event](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs?range=3-11,31-33)]
[!code-vb[Startup-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb?range=5-11,30-32)]

此時，在應用程式的存留期內，最常見的做法是顯示 UI。

<a name="Showing_a_User_Interface"></a>

### <a name="showing-a-user-interface"></a>顯示使用者介面

大部分獨立的 Windows 應用程式會在開始執行時開啟 <xref:System.Windows.Window>。 <xref:System.Windows.Application.Startup> 事件處理常式是您可以從中執行此動作的一個位置，如下列程式碼所示。

[!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]

[!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
[!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]

> [!NOTE]
> 在獨立應用程式中具現化的第一個 <xref:System.Windows.Window> 預設會成為主應用程式視窗。 這個 <xref:System.Windows.Window> 的物件是由 <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> 屬性所參考。 如果與第一個具現化 <xref:System.Windows.Window> 不同的視窗應該是主視窗，則可以透過程式設計方式變更 <xref:System.Windows.Application.MainWindow%2A> 屬性的值。

當 XBAP 第一次啟動時，它很可能會流覽至 <xref:System.Windows.Controls.Page>。 如下列程式碼所示。

[!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]

[!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
[!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]

如果您處理 <xref:System.Windows.Application.Startup> 只開啟 <xref:System.Windows.Window> 或流覽至 <xref:System.Windows.Controls.Page>，您可以改為在標記中設定 `StartupUri` 屬性。

下列範例顯示如何使用獨立應用程式中的 <xref:System.Windows.Application.StartupUri%2A> 來開啟 <xref:System.Windows.Window>。

[!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]

下列範例示範如何使用 XBAP 的 <xref:System.Windows.Application.StartupUri%2A> 來流覽至 <xref:System.Windows.Controls.Page>。

[!code-xaml[PageSnippets#XBAPStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]

此標記與前述用來開啟視窗的程式碼有相同的效果。

> [!NOTE]
> 如需有關導覽的詳細資訊，請參閱[流覽總覽](navigation-overview.md)。

如果您需要使用非參數化的函式將它具現化，或者必須先設定其屬性或訂閱其事件，才能顯示 <xref:System.Windows.Window>，您需要處理 <xref:System.Windows.Application.Startup> 事件以開啟該專案，或者您需要處理啟動應用程式時所提供的任何命令列引數。

<a name="Processing_Command_Line_Arguments"></a>

### <a name="processing-command-line-arguments"></a>處理命令列引數

在 Windows 中，可以從命令提示字元或桌面啟動獨立應用程式。 在這兩種情況下，都會將命令列引數傳遞至應用程式。 下列範例顯示以單一命令列引數 "/StartMinimized" 啟動的應用程式：

`wpfapplication.exe /StartMinimized`

在應用程式初始化期間，WPF 會從作業系統抓取命令列引數，並透過 <xref:System.Windows.StartupEventArgs> 參數的 <xref:System.Windows.StartupEventArgs.Args%2A> 屬性，將它們傳遞至 <xref:System.Windows.Application.Startup> 事件處理常式。 您可以使用如下的程式碼擷取及儲存命令列引數。

[!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]

[!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
[!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]

程式碼會處理 <xref:System.Windows.Application.Startup>，以檢查是否已提供 **/StartMinimized**命令列引數。若是如此，它會開啟 <xref:System.Windows.WindowState> 為 <xref:System.Windows.WindowState.Minimized>的主視窗。 請注意，因為 <xref:System.Windows.Window.WindowState%2A> 屬性必須以程式設計方式設定，所以必須在程式碼中明確開啟主要 <xref:System.Windows.Window>。

Xbap 無法取出和處理命令列引數，因為它們是使用 ClickOnce 部署啟動的（請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)）。 不過，它們可以透過用來啟動的 URL 擷取及處理查詢字串參數。

<a name="Application_Activation_and_Deactivation"></a>

### <a name="application-activation-and-deactivation"></a>應用程式啟用和停用

Windows 可讓使用者在應用程式之間切換。 最常見的做法是使用 ALT+TAB 按鍵組合。 只有當應用程式具有可供使用者選取的可見 <xref:System.Windows.Window> 時，才可以切換為。 目前選取的 <xref:System.Windows.Window> 是*使用中視窗*（也稱為*前景視窗*），而是接收使用者輸入的 <xref:System.Windows.Window>。 具有使用中視窗的應用程式是使用中的*應用程式*（或*前景應用*程式）。 在下列情況中，應用程式會變成使用中應用程式：

- 它會啟動並顯示 <xref:System.Windows.Window>。

- 使用者藉由選取應用程式中的 <xref:System.Windows.Window>，從另一個應用程式切換。

您可以藉由處理 <xref:System.Windows.Application.Activated?displayProperty=nameWithType> 事件來偵測應用程式何時變成使用中狀態。

同樣地，在下列情況中，應用程式會變成非使用中：

- 使用者從目前的應用程式切換至另一個應用程式。

- 應用程式關閉時。

您可以藉由處理 <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> 事件來偵測應用程式何時變成非作用中。

下列程式碼會示範如何處理 <xref:System.Windows.Application.Activated> 和 <xref:System.Windows.Application.Deactivated> 事件，以判斷應用程式是否為使用中狀態。

[!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]

[!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
[!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]

也可以啟用和停用 <xref:System.Windows.Window>。 如需詳細資訊，請參閱<xref:System.Windows.Window.Activated?displayProperty=nameWithType>和<xref:System.Windows.Window.Deactivated?displayProperty=nameWithType>。

> [!NOTE]
> 不會為 Xbap 引發 <xref:System.Windows.Application.Activated?displayProperty=nameWithType> 或 <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType>。

<a name="Application_Shutdown"></a>

### <a name="application-shutdown"></a>應用程式關閉

應用程式一旦關閉，其存留期間便告結束，而應用程式關閉的可能原因包括：

- 使用者關閉每個 <xref:System.Windows.Window>。

- 使用者關閉主要 <xref:System.Windows.Window>。

- 使用者藉由登出或關閉來結束 Windows 會話。

- 已符合應用程式特定條件。

為了協助您管理應用程式關閉，<xref:System.Windows.Application> 提供 <xref:System.Windows.Application.Shutdown%2A> 方法、<xref:System.Windows.Application.ShutdownMode%2A> 屬性，以及 <xref:System.Windows.Application.SessionEnding> 和 <xref:System.Windows.Application.Exit> 事件。

> [!NOTE]
> 只能從具有 <xref:System.Security.Permissions.UIPermission>的應用程式呼叫 <xref:System.Windows.Application.Shutdown%2A>。 獨立 WPF 應用程式一律具有此許可權。 不過，在網際網路區域部分信任安全性沙箱中執行的 Xbap 則不會。

#### <a name="shutdown-mode"></a>程式關閉模式

大多數應用程式會在所有視窗關閉或主視窗關閉時一併關閉。 不過有時候，應用程式關閉的時機可能是由其他應用程式特定條件決定。 您可以使用下列其中一個 <xref:System.Windows.ShutdownMode> 列舉值來設定 <xref:System.Windows.Application.ShutdownMode%2A>，以指定應用程式將關閉的條件：

- <xref:System.Windows.ShutdownMode.OnLastWindowClose>

- <xref:System.Windows.ShutdownMode.OnMainWindowClose>

- <xref:System.Windows.ShutdownMode.OnExplicitShutdown>

<xref:System.Windows.Application.ShutdownMode%2A> 的預設值是 <xref:System.Windows.ShutdownMode.OnLastWindowClose>，這表示當使用者關閉應用程式中的最後一個視窗時，應用程式會自動關閉。 不過，如果您的應用程式應該在主視窗關閉時關閉，WPF 會自動執行這種情況，如果您將 <xref:System.Windows.Application.ShutdownMode%2A> 設定為 <xref:System.Windows.ShutdownMode.OnMainWindowClose>。 下列範例會顯示這一點。

[!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]

當您有應用程式特定的關機狀況時，請將 <xref:System.Windows.Application.ShutdownMode%2A> 設定為 <xref:System.Windows.ShutdownMode.OnExplicitShutdown>。 在這種情況下，您必須藉由明確地呼叫 <xref:System.Windows.Application.Shutdown%2A> 方法來關閉應用程式的責任;否則，即使所有視窗都已關閉，您的應用程式仍會繼續執行。 請注意，當 <xref:System.Windows.Application.ShutdownMode%2A> <xref:System.Windows.ShutdownMode.OnLastWindowClose> 或 <xref:System.Windows.ShutdownMode.OnMainWindowClose>時，會隱含地呼叫 <xref:System.Windows.Application.Shutdown%2A>。

> [!NOTE]
> <xref:System.Windows.Application.ShutdownMode%2A> 可以從 XBAP 設定，但它會被忽略;當 XBAP 在瀏覽器中離開時，或裝載 XBAP 的瀏覽器關閉時，就一律會關閉 XBAP。 如需詳細資訊，請參閱[覽概觀](navigation-overview.md)。

#### <a name="session-ending"></a>工作階段結束

<xref:System.Windows.Application.ShutdownMode%2A> 屬性所描述的關機狀況是應用程式特有的。 不過在某些情況下，應用程式可能會因為外部狀況而關閉。 當使用者透過下列動作結束 Windows 會話時，就會發生最常見的外部狀況：

- 正在登出

- 關機

- 重新啟動中

- 休眠

若要偵測 Windows 會話何時結束，您可以處理 <xref:System.Windows.Application.SessionEnding> 事件，如下列範例所示。

[!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]

[!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
[!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]

在此範例中，程式碼會檢查 <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> 屬性，以判斷 Windows 會話的結束方式。 接著，它會使用這個值對使用者顯示確認訊息。 如果使用者不想要結束會話，程式碼會將 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 設定為 `true`，以防止 Windows 會話結束。

> [!NOTE]
> Xbap 不會引發 <xref:System.Windows.Application.SessionEnding>。

#### <a name="exit"></a>結束

當應用程式關閉時，可能需要執行一些最終處理作業，例如保存應用程式狀態。 在這些情況下，您可以處理 <xref:System.Windows.Application.Exit> 事件，因為 `App_Exit` 事件處理常式會在下列範例中執行。 它會定義為*app.xaml*檔案中的事件處理常式。 它的實*App.xaml.cs*和*app.xaml*檔案中會反白顯示。

[!code-xaml[Defining-the-Exit-event-handler](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]

[!code-csharp[Handling-the-Exit-event](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=42-55)]
[!code-vb[Handling-the-Exit-event](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=34-45)]

如需完整範例，請參閱[跨應用程式會話保存和還原應用程式範圍的屬性](persist-and-restore-application-scope-properties.md)。

獨立應用程式和 Xbap 都可以處理 <xref:System.Windows.Application.Exit>。 若為 Xbap，在下列情況下會引發 <xref:System.Windows.Application.Exit>：

- XBAP 會離開。

- 在 Internet Explorer 中，當裝載 XBAP 的索引標籤已關閉時。

- 關閉瀏覽器時。

#### <a name="exit-code"></a>結束碼

應用程式大部分是由作業系統啟動，以回應使用者要求。 不過，應用程式可由另一個應用程式啟動，以執行某項特定工作。 關閉已啟動的應用程式時，正在啟動的應用程式可能需要知道已啟動之應用程式的關閉條件。 在這些情況下，Windows 可讓應用程式在關機時傳回應用程式結束代碼。 根據預設，WPF 應用程式會傳回結束代碼值0。

> [!NOTE]
> 當您從 Visual Studio 進行調試時，應用程式關閉時，應用程式結束代碼會顯示在 [**輸出**] 視窗中，以如下所示的訊息：
>
> `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`
>
> 按一下 [**視圖**] 功能表上的 [**輸出**]，即可開啟 [**輸出**] 視窗。

若要變更結束代碼，您可以呼叫 <xref:System.Windows.Application.Shutdown%28System.Int32%29> 多載，這會接受整數引數做為結束代碼：

[!code-csharp[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
[!code-vb[ApplicationExitSnippets#AppExitCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]

您可以藉由處理 <xref:System.Windows.Application.Exit> 事件來偵測結束代碼的值，並加以變更。 <xref:System.Windows.Application.Exit> 事件處理常式會傳遞 <xref:System.Windows.ExitEventArgs>，以 <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> 屬性來存取結束代碼。 如需詳細資訊，請參閱 <xref:System.Windows.Application.Exit>。

> [!NOTE]
> 您可以在獨立應用程式和 Xbap 中設定結束代碼。 不過，Xbap 會忽略結束代碼值。

<a name="Unhandled_Exceptions"></a>

### <a name="unhandled-exceptions"></a>未處理的例外狀況

有時候，應用程式可能會在異常情況下關閉，例如擲回非預期的例外狀況時。 在此情況下，應用程式可能沒有可偵測及處理例外狀況的程式碼。 這種類型的例外狀況是未處理的例外狀況；在應用程式關閉之前，會顯示與下圖所示類似的通知。

![顯示未處理之例外狀況通知的螢幕擷取畫面。](./media/application-management-overview/unhandled-exception-notification.png)

從使用者體驗的觀點來看，應用程式最好能夠藉由執行下列部分或所有動作，來避免此預設行為：

- 顯示方便使用的資訊。

- 嘗試繼續執行應用程式。

- 在 Windows 事件記錄檔中記錄詳細、開發人員易記的例外狀況資訊。

執行此支援取決於能夠偵測到未處理的例外狀況，這就是引發 <xref:System.Windows.Application.DispatcherUnhandledException> 事件的情況。

[!code-xaml[detecting-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]

[!code-csharp[code-to-detect-unhandled-exceptions](~/samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs)]
[!code-vb[code-to-detect-unhandled-exceptions](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb)]

<xref:System.Windows.Application.DispatcherUnhandledException> 事件處理常式會傳遞 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> 參數，其中包含與未處理的例外狀況相關的內容資訊，包括例外狀況本身（<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>）。 您可以使用這項資訊來判斷如何處理例外狀況。

當您處理 <xref:System.Windows.Application.DispatcherUnhandledException>時，您應該將 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> 屬性設定為 [`true`]。否則，WPF 仍會將例外狀況視為未處理，並還原成先前所述的預設行為。 如果引發未處理的例外狀況，但未處理 <xref:System.Windows.Application.DispatcherUnhandledException> 事件，或是已處理事件且 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> 設定為 `false`，應用程式會立即關閉。 此外，也不會引發其他 <xref:System.Windows.Application> 事件。 因此，如果您的應用程式具有必須在應用程式關閉之前執行的程式碼，則您需要處理 <xref:System.Windows.Application.DispatcherUnhandledException>。

雖然應用程式可能因為未處理的例外狀況而關閉，但是應用程式通常是為了回應使用者的要求而關閉 (如下節所述)。

<a name="Application_Lifetime_Events"></a>

### <a name="application-lifetime-events"></a>應用程式存留期事件

獨立應用程式和 Xbap 沒有完全相同的存留期。 下圖說明獨立應用程式存留期內的主要事件，並顯示這些事件的引發順序。

![獨立應用&#45;程式物件事件](./media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")

同樣地，下圖說明 XBAP 存留期的主要事件，並顯示其引發的順序。

![XBAP &#45;應用程式物件事件](./media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Application>
- [WPF 視窗概觀](wpf-windows-overview.md)
- [瀏覽概觀](navigation-overview.md)
- [WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)
- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
- [應用程式模型：使用說明主題](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms749013(v=vs.100))
- [應用程式開發](index.md)
