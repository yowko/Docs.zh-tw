---
title: "應用程式管理概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式管理 [WPF]"
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
caps.latest.revision: 56
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 52
---
# 應用程式管理概觀
所有的應用程式會共用常見的一組適用於應用程式實作和管理的功能。  本主題提供的功能，在<xref:System.Windows.Application>來建立和管理應用程式的類別。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Application 類別  
 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，應用程式範圍的一般功能封裝在<xref:System.Windows.Application>類別。  <xref:System.Windows.Application>類別還包含下列功能：  
  
-   追蹤應用程式的存留期 \(Lifetime\) 並與其互動。  
  
-   擷取和處理命令列參數。  
  
-   偵測及回應未處理的例外狀況 \(Exception\)。  
  
-   共用應用程式範圍屬性和資源。  
  
-   管理獨立應用程式中的視窗。  
  
-   追蹤和管理功能。  
  
<a name="The_Application_Class"></a>   
## 如何使用應用程式類別的一般工作  
 如果您不感興趣的詳細資料的所有<xref:System.Windows.Application>類別下, 表列出一些常見工作，如<xref:System.Windows.Application> ，以及如何完成這些。  檢視相關的 API 和主題，您可以找到更多的資訊和範例程式碼。  
  
|工作|處理方式|  
|--------|----------|  
|取得物件，表示目前的應用程式|使用 <xref:System.Windows.Application.Current%2A?displayProperty=fullName> 屬性。|  
|加入至應用程式的啟動畫面|請參閱 [在 WPF 應用程式中加入啟動顯示畫面](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)。|  
|啟動應用程式|請使用 <xref:System.Windows.Application.Run%2A?displayProperty=fullName> 方法。|  
|停止應用程式|請使用 <xref:System.Windows.Application.Current%2A> 物件的 <xref:System.Windows.Application.Shutdown%2A?displayProperty=fullName> 方法。|  
|取得從命令列的引數|處理<xref:System.Windows.Application.Startup?displayProperty=fullName>事件，並使用<xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=fullName>屬性。  如需範例，請參閱<xref:System.Windows.Application.Startup?displayProperty=fullName>事件。|  
|取得和設定應用程式的結束代碼|設定<xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=fullName>屬性在<xref:System.Windows.Application.Exit?displayProperty=fullName>事件處理常式或呼叫<xref:System.Windows.Application.Shutdown%2A>方法，並傳入整數。|  
|偵測及回應未處理的例外狀況|處理 <xref:System.Windows.Application.DispatcherUnhandledException> 事件。|  
|取得和設定應用程式範圍資源|使用 <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> 屬性。|  
|使用應用程式範圍資源字典|請參閱 [使用應用程式範圍的資源字典](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md)。|  
|取得和設定應用程式範圍的屬性|使用 <xref:System.Windows.Application.Properties%2A?displayProperty=fullName> 屬性。|  
|取得和儲存應用程式的狀態|請參閱 [跨應用程式工作階段保存和還原應用程式範圍的屬性](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md)。|  
|管理非程式碼資料檔案，包括資源檔、 內容檔和來源網站檔。|請參閱 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。|  
|管理獨立應用程式中的視窗|請參閱 [WPF 視窗概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)。|  
|追蹤和管理功能|請參閱 [巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。|  
  
<a name="The_Application_Definition"></a>   
## 應用程式定義  
 若要使用的功能<xref:System.Windows.Application>類別，您必須實作應用程式定義。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式定義是衍生自 <xref:System.Windows.Application> 而且已經設定特殊 [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] 設定的類別。  
  
### 實作應用程式定義  
 一般的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式定義都是同時使用標記和程式碼後置 \(Code\-Behind\) 來實作。  這種實作方式可以讓您使用標記，以宣告方式設定應用程式屬性、資源和註冊事件，同時在程式碼後置中處理事件並實作應用程式特有的行為。  
  
 下列範例示範如何同時使用標記和程式碼後置來實作應用程式定義：  
  
 [!code-xml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 若要讓標記檔案和程式碼後置的檔案一起運作，必須符合下列條件：  
  
-   標記中的 `Application` 項目必須包含 `x:Class` 屬性 \(Attribute\)。  建置應用程式時，標記檔案中若存在 `x:Class` 會造成 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 建立衍生自 <xref:System.Windows.Application> 且具有 `x:Class` 屬性指定之名稱的 `partial` 類別。  這需要加入 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 結構描述的 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 命名空間宣告 \(`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`\)。  
  
-   程式碼後置中的類別必須是 `partial` 類別，並具有標記中 `x:Class` 屬性所指定的相同名稱，且必須衍生自 <xref:System.Windows.Application>。  允許程式碼後置的檔案與 `partial` 類別產生關聯，這個類別是在建置應用程式時根據標記產生的 \(請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)\)。  
  
> [!NOTE]
>  當您使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 建立新的 WPF 應用程式專案或 WPF 瀏覽器應用程式專案時，預設會包含應用程式定義，並同時使用標記和程式碼後置加以定義。  
  
 這個程式碼是實作應用程式定義所需的最基本程式碼。  不過，建置 \(Build\) 及執行應用程式之前，您還必須對應用程式定義進行一項額外的 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 組態設定。  
  
### 設定 MSBuild 的應用程式定義  
 獨立應用程式和 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 必須實作特定層級的基礎結構之後才能執行。  這個基礎結構最重要的部分是進入點 \(Entry Point\)。  當使用者啟動應用程式時，作業系統會呼叫進入點，也就是用來啟動應用程式的已知功能。  
  
 依照慣例，開發人員必須自行撰寫這個程式碼的某些部分或全部 \(依技術而定\)。  不過，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會在將應用程式定義的標記檔案設定為 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` 項目時自動產生這個程式碼，如下列 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 專案檔所示。  
  
```  
<Project   
  DefaultTargets="Build"  
  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 因為程式碼後置的檔案包含程式碼，所以如同一般情況，這個檔案會標記為 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` 項目。  
  
 將這些 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 組態套用至應用程式定義的標記和程式碼後置檔案將會使 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 產生如下的程式碼：  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 產生的程式碼會以額外的基礎架構程式碼 \(包括進入點方法 `Main`\) 來擴充您的應用程式定義。  <xref:System.STAThreadAttribute> 屬性會套用至 `Main` 方法，以指出 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的主要 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 執行緒是 STA 執行緒 \(此為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 之所需\)。呼叫 `Main` 時，它會在呼叫 `InitializeComponent` 方法以註冊事件並設定標記中實作的屬性之前，建立 `App` 的新執行個體。  因為 `InitializeComponent` 是自動產生的，所以您不需要像實作 <xref:System.Windows.Controls.Page> 和 <xref:System.Windows.Window> 時一樣，從應用程式定義明確呼叫 `InitializeComponent`。  最後，此程式碼會呼叫 <xref:System.Windows.Application.Run%2A> 方法來啟動應用程式。  
  
<a name="Getting_the_Current_Application"></a>   
## 取得目前的應用程式  
 因為功能的<xref:System.Windows.Application>類別跨應用程式共用 」，可以是只有一個執行個體<xref:System.Windows.Application>類別每個<xref:System.AppDomain>。  為強制施行此原則，<xref:System.Windows.Application> 類別會實作成單一類別 \(請參閱[在 C\# 中實作單一類別](http://msdn2.microsoft.com/zh-tw/library/ms998558.aspx)\)；此類別可建立本身的單一執行個體，並使用 `static` <xref:System.Windows.Application.Current%2A> 屬性提供其共用存取權。  
  
 下列程式碼顯示如何取得目前 <xref:System.AppDomain> 之 <xref:System.Windows.Application> 物件的參考。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> 會傳回 <xref:System.Windows.Application> 類別執行個體的參考。  如果需要 <xref:System.Windows.Application> 衍生類別 \(Derived Class\) 的參考，必須轉換 <xref:System.Windows.Application.Current%2A> 屬性的值，如下列範例所示。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 您可以在 <xref:System.Windows.Application> 物件存留期的任何時間點檢查 <xref:System.Windows.Application.Current%2A> 的值。  不過，您應該小心。  在 <xref:System.Windows.Application> 類別具現化 \(Instantiated\) 之後，有一段時間 <xref:System.Windows.Application> 物件的狀態並不一致。  在這段時間，<xref:System.Windows.Application> 會執行執行程式碼所需的各種初始設定工作，包括建立應用程式基礎結構、設定屬性和註冊事件。  如果您在這段時間嘗試使用 <xref:System.Windows.Application> 物件，程式碼可能會產生無法預期的結果，尤其是當程式碼相依於正在設定的各種 <xref:System.Windows.Application> 屬性時。  
  
 在 <xref:System.Windows.Application> 完成初始設定工作時，其存留期才會正式開始。  
  
<a name="Application_Lifetime"></a>   
## 應用程式存留期  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式的存留期是由 <xref:System.Windows.Application> 引發的幾個事件標記，讓您知道應用程式何時啟動、何時啟用並停用，以及何時關閉。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Splash_Screen"></a>   
### 開頭顯示畫面  
 在 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 中進行啟動時，您可以指定要在啟動視窗或「*啟動顯示畫面*」\(Splash Screen\) 中使用影像。  <xref:System.Windows.SplashScreen> 類別讓您可以輕易在應用程式載入時，顯示啟動視窗。  會建立 <xref:System.Windows.SplashScreen> 視窗，並在呼叫 <xref:System.Windows.Application.Run%2A> 前顯示這個視窗。  如需詳細資訊，請參閱 [應用程式啟動時間](../../../../docs/framework/wpf/advanced/application-startup-time.md) 和 [在 WPF 應用程式中加入啟動顯示畫面](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)。  
  
<a name="Starting_an_Application"></a>   
### 啟動應用程式  
 呼叫 <xref:System.Windows.Application.Run%2A> 並初始化應用程式之後，執行應用程式的準備工作便已完成。  這個時間點是以引發 <xref:System.Windows.Application.Startup> 事件來表示：  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 在應用程式存留期的這個階段，最常執行的工作是顯示 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
<a name="Showing_a_User_Interface"></a>   
### 顯示使用者介面  
 大部分的獨立 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 應用程式在開始執行時都會開啟 <xref:System.Windows.Window>。  如下列程式碼所示範，<xref:System.Windows.Application.Startup> 事件處理常式是可以執行這項工作的其中一個位置。  
  
 [!code-xml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  根據預設，獨立應用程式中所要具現化的第一個 <xref:System.Windows.Window> 會成為主應用程式視窗。  這個 <xref:System.Windows.Window> 物件是由 <xref:System.Windows.Application.MainWindow%2A?displayProperty=fullName> 屬性所參考。  如果主視窗應該是第一個具現化之 <xref:System.Windows.Window> 以外的其他視窗，可以透過程式設計的方式變更 <xref:System.Windows.Application.MainWindow%2A> 屬性的值。  
  
 在 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 第一次啟動時，它最有可能會巡覽至 <xref:System.Windows.Controls.Page>。  請參考下列程式碼中的示範。  
  
 [!code-xml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 如果您將 <xref:System.Windows.Application.Startup> 處理成只開啟 <xref:System.Windows.Window> 或巡覽至 <xref:System.Windows.Controls.Page>，可以改為設定標記中的 `StartupUri` 屬性。  
  
 下列範例示範如何從獨立應用程式使用 <xref:System.Windows.Application.StartupUri%2A> 開啟 <xref:System.Windows.Window>。  
  
 [!code-xml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 下列範例示範如何使用 <xref:System.Windows.Application.StartupUri%2A> 從 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 巡覽至 <xref:System.Windows.Controls.Page>。  
  
 [!code-xml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 這個標記的效果與前述用來開啟視窗的程式碼相同。  
  
> [!NOTE]
>  如需巡覽的詳細資訊，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
 在下列情況下，您必須處理 <xref:System.Windows.Application.Startup> 事件來開啟 <xref:System.Windows.Window>：需要使用非預設建構函式 \(Constructor\) 將它具現化、需要在顯示它之前設定其屬性或訂閱其事件，或是需要處理啟動應用程式時所提供的任何命令列引數。  
  
<a name="Processing_Command_Line_Arguments"></a>   
### 處理命令列引數  
 在 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 中，獨立應用程式可以從命令提示字元或桌面啟動。  在這兩種情況下，都可以將命令列引數傳遞至應用程式。下列範例顯示以單一命令列引數 "\/StartMinimized" 啟動應用程式：  
  
 `wpfapplication.exe /StartMinimized`  
  
 在應用程式初始設定期間，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會從作業系統擷取命令列引數，並透過 <xref:System.Windows.StartupEventArgs> 參數的 <xref:System.Windows.StartupEventArgs.Args%2A> 屬性，將它們傳遞至 <xref:System.Windows.Application.Startup> 事件處理常式。  您可以使用如下的程式碼擷取及儲存命令列引數。  
  
 [!code-xml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 這個程式碼會處理 <xref:System.Windows.Application.Startup>，檢查是否已提供 **\/StartMinimized** 命令列引數；如果已提供，它會使用 <xref:System.Windows.WindowState> 的 <xref:System.Windows.WindowState> 開啟主視窗。  請注意，因為 <xref:System.Windows.Window.WindowState%2A> 屬性必須以程式設計方式設定，所以必須在程式碼中明確開啟主 <xref:System.Windows.Window>。  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 無法擷取及處理命令列引數，因為它們是使用 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 部署來啟動 \(請參閱[部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)\)。  不過，可以從啟動 URL 中擷取和處理查詢字串參數。  
  
<a name="Application_Activation_and_Deactivation"></a>   
### 應用程式啟動和停用  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 也允許使用者在應用程式之間進行切換。最常用的方式是使用 ALT\+TAB 按鍵組合。  只有在應用程式具有使用者可以選取的可見 <xref:System.Windows.Window> 時，使用者才能切換到該應用程式。  目前選取的 <xref:System.Windows.Window> 是「*使用中視窗*」\(Active Window\)，又稱為「*前景視窗*」\(Foreground Window\)，也是用來接收使用者輸入的 <xref:System.Windows.Window>。具有使用者視窗的應用程式是「*作用中應用程式*」\(Active Application\)，也稱為「*前景應用程式*」\(Foreground Application\)。在下列情況中，應用程式會變成作用中應用程式：  
  
-   應用程式已啟動並顯示 <xref:System.Windows.Window>。  
  
-   使用者透過在應用程式中選取 <xref:System.Windows.Window> 從其他應用程式進行切換。  
  
 您可藉由處理 <xref:System.Windows.Application.Activated?displayProperty=fullName> 事件，偵測應用程式變成作用中的時間。  
  
 同樣地，在下列情況中，應用程式會變成非作用中：  
  
-   使用者從目前的應用程式切換到其他應用程式。  
  
-   應用程式關閉時。  
  
 您可藉由處理 <xref:System.Windows.Application.Deactivated?displayProperty=fullName> 事件，偵測應用程式變成非作用中的時間。  
  
 下列程式碼顯示如何處理 <xref:System.Windows.Application.Activated> 和 <xref:System.Windows.Application.Deactivated> 事件，以判斷應用程式是否正在作用。  
  
 [!code-xml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 <xref:System.Windows.Window> 也可以啟動及停用。  如需詳細資訊，請參閱 <xref:System.Windows.Window.Activated?displayProperty=fullName> 和 <xref:System.Windows.Window.Deactivated?displayProperty=fullName>。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 既不會引發 <xref:System.Windows.Application.Activated?displayProperty=fullName> 也不會引發 <xref:System.Windows.Application.Deactivated?displayProperty=fullName>。  
  
<a name="Application_Shutdown"></a>   
### 應用程式關閉  
 應用程式一旦關閉，其存留期間便告結束，而應用程式關閉的可能原因包括：  
  
-   使用者關閉每個 <xref:System.Windows.Window>。  
  
-   使用者關閉主 <xref:System.Windows.Window>。  
  
-   使用者透過登出或關機結束 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 工作階段 \(Session\)。  
  
-   已符合應用程式特定條件。  
  
 為了協助您管理應用程式關閉作業，<xref:System.Windows.Application> 提供了 <xref:System.Windows.Application.Shutdown%2A> 方法、<xref:System.Windows.Application.ShutdownMode%2A> 屬性，以及 <xref:System.Windows.Application.SessionEnding> 和 <xref:System.Windows.Application.Exit> 事件。  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> 只能從擁有 <xref:System.Security.Permissions.UIPermission> 的應用程式呼叫。  獨立的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式全都擁有這種使用權限。  不過，執行於網際網路區域部分信任安全性沙箱的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 並無這種使用權限。  
  
#### 程式關閉模式  
 大部分的應用程式都是在所有視窗關閉或主視窗關閉時便會關閉。  不過，有時候應用程式關閉的時機可能是由其他應用程式特定條件決定。  您可以使用下列其中一個 <xref:System.Windows.ShutdownMode> 列舉值設定 <xref:System.Windows.Application.ShutdownMode%2A>，藉以指定應用程式關閉的條件：  
  
-   <xref:System.Windows.ShutdownMode>  
  
-   <xref:System.Windows.ShutdownMode>  
  
-   <xref:System.Windows.ShutdownMode>  
  
 <xref:System.Windows.Application.ShutdownMode%2A> 的預設值是 <xref:System.Windows.ShutdownMode>，這個值表示應用程式會在使用者關閉應用程式的最後一個視窗時自動關閉。  不過，如果應用程式應該在主視窗時關閉，如果您將 <xref:System.Windows.Application.ShutdownMode%2A> 設定為 <xref:System.Windows.ShutdownMode>，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 便會自動執行該項動作。  這在下列範例中顯示。  
  
 [!code-xml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 當您擁有應用程式特定關閉條件時，您會將 <xref:System.Windows.Application.ShutdownMode%2A> 設定為 <xref:System.Windows.ShutdownMode>。  在這種情況下，您必須負責透過明確呼叫 <xref:System.Windows.Application.Shutdown%2A> 方法來關閉應用程式；否則，即使所有視窗都已關閉，應用程式仍會繼續執行。  請注意，當 <xref:System.Windows.Application.ShutdownMode%2A> 是 <xref:System.Windows.ShutdownMode> 或 <xref:System.Windows.ShutdownMode> 時，則會以隱含方式呼叫 <xref:System.Windows.Application.Shutdown%2A>。  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> 可以從 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 設定，但是系統會忽略它；每次從瀏覽器離開時，或是裝載 \(Host\)  [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的瀏覽器關閉時，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 一定都會關閉。  如需詳細資訊，請參閱 [巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
#### 工作階段結束  
 <xref:System.Windows.Application.ShutdownMode%2A> 屬性所描述的關閉條件是應用程式專屬條件。  不過在某些情況下，應用程式可能會因為外部條件而關閉。  最常見的外部條件是當使用者透過下列動作結束 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 工作階段時：  
  
-   登出  
  
-   關機  
  
-   重新開機  
  
-   休眠  
  
 若要偵測 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 工作階段何時結束，您可以處理 <xref:System.Windows.Application.SessionEnding> 事件，如同下列範例所示。  
  
 [!code-xml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 在這個範例中，程式碼會檢查 <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> 屬性，以判斷 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 工作階段結束的方式。  接著，它會使用這個值對使用者顯示確認訊息。  如果使用者不想結束工作階段，程式碼會將 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 設定為 `true`，以避免結束 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 工作階段。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 不會引發 <xref:System.Windows.Application.SessionEnding>。  
  
#### Exit  
 當應用程式關閉時，可能需要執行某些最終處理作業，例如保存應用程式狀態。  針對這種情況，您可以處理 <xref:System.Windows.Application.Exit> 事件。  
  
 [!code-xml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 如需完整的範例，請參閱 [跨應用程式工作階段保存和還原應用程式範圍的屬性](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md)。  
  
 獨立應用程式和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 都可以處理 <xref:System.Windows.Application.Exit>。  [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 會在發生下列情況時引發 <xref:System.Windows.Application.Exit>：  
  
-   離開 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 時。  
  
-   在 [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] 中關閉裝載 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的索引標籤時。  
  
-   關閉瀏覽器時。  
  
#### 結束代碼  
 應用程式大多由作業系統啟動以回應使用者的要求。  不過，其他應用程式也可以啟動應用程式來執行某項特定工作。  在被啟動的應用程式關閉時，啟動端的應用程式可能需要知道被啟動之應用程式是在什麼狀況下關閉的。  在這種情況下，[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 可以讓應用程式在關閉時傳回應用程式結束代碼 \(Exit Code\)。  根據預設，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式會傳回結束代碼值 0。  
  
> [!NOTE]
>  當您從 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 進行偵錯時，應用程式結束代碼會在應用程式關閉時顯示在 \[**輸出**\] 視窗中類似下面的訊息中：  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  您可以按一下 \[**檢視**\] 功能表上的 \[**輸出**\]，開啟 \[**輸出**\] 視窗。  
  
 若要變更結束代碼，可以呼叫 <xref:System.Windows.Application.Shutdown%28System.Int32%29> 多載；此多載可接受整數引數做為結束代碼：  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 您可以透過處理 <xref:System.Windows.Application.Exit> 事件偵測及變更結束代碼的值。  <xref:System.Windows.Application.Exit> 事件處理常式會收到傳入的 <xref:System.Windows.ExitEventArgs>，其透過 <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> 屬性提供結束代碼的存取權。  如需詳細資訊，請參閱 <xref:System.Windows.Application.Exit>。  
  
> [!NOTE]
>  您可以同時在獨立應用程式和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 中設定結束代碼。  不過，[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 會忽略結束代碼值。  
  
<a name="Unhandled_Exceptions"></a>   
### 未處理的例外狀況  
 有時候，應用程式可能會在異常的狀況下關閉，例如擲回無法預期的例外狀況時。  在這種情況下，應用程式可能沒有程式碼可以偵測及處理例外狀況。  這種類型的例外狀況是未處理的例外狀況；在應用程式關閉之前，將會顯示與下圖所示類似的通知訊息。  
  
 ![未處理的例外狀況通知](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 從使用者經驗的觀點來看，應用程式最好能夠採取以下部分或所有措施，以避免這種預設行為：  
  
-   顯示使用者容易理解的資訊。  
  
-   嘗試讓應用程式繼續執行。  
  
-   在 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 中記錄詳細、方便開發者參考的例外狀況資訊。  
  
 這項支援的實作需視是否能夠偵測未處理的例外狀況而定，而這也是引發 <xref:System.Windows.Application.DispatcherUnhandledException> 的原因。  
  
 [!code-xml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> 事件處理常式會收到傳入的 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> 參數，其中包含關於未處理之例外狀況的內容資訊，包括例外狀況本身 \(<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=fullName>\)。  您可以使用這項資訊決定處理例外狀況的方式。  
  
 處理 <xref:System.Windows.Application.DispatcherUnhandledException> 時，您應該將 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=fullName> 屬性設定為 `true`，否則 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 仍會將例外狀況視為未處理，並還原成前述的預設行為。  如果已引發未處理的例外狀況，而且沒有處理 <xref:System.Windows.Application.DispatcherUnhandledException> 事件，或是已處理事件且 <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> 已設定為 `false`，應用程式會立即關閉。  此外，也不會引發其他任何 <xref:System.Windows.Application> 事件。  因此，如果應用程式包含必須在應用程式關閉之前執行的程式碼，您就必須處理 <xref:System.Windows.Application.DispatcherUnhandledException>。  
  
 雖然應用程式可能因為未處理的例外狀況而關閉，但是如下節所述，應用程式通常是為了回應使用者的要求而關閉。  
  
<a name="Application_Lifetime_Events"></a>   
### 應用程式存留期事件  
 獨立應用程式和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 並無完全相同的存留期。下圖說明獨立應用程式存留期的重要事件，並顯示這些事件的引發順序。  
  
 ![獨立應用程式 &#45; 應用程式物件事件](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview\_ApplicationObjectEvents")  
  
 同樣地，下圖也說明 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 存留期的重要事件，並顯示其引發順序。  
  
 ![XBAP &#45; 應用程式物件事件](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview\_ApplicationObjectEvents\_xbap")  
  
## 請參閱  
 <xref:System.Windows.Application>   
 [WPF 視窗概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)   
 [巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)   
 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)   
 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [Application Model: How\-to Topics](http://msdn.microsoft.com/zh-tw/76771b09-3688-4d1c-8818-9b3f4cf39a30)   
 [應用程式開發](../../../../docs/framework/wpf/app-development/index.md)