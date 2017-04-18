---
title: "WPF 增益集概觀 | Microsoft Docs"
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
  - ".NET Framework 增益集模型 [WPF]"
  - "增益集 [WPF], 架構"
  - "增益集 [WPF], 好處"
  - "增益集 [WPF], 限制"
  - "增益集 [WPF], 效能"
  - "增益集 [WPF], 使用者介面"
  - "增益集和使用者介面 [WPF]"
  - "增益集和 XAML 瀏覽器應用程式 [WPF]"
  - "增益集概觀 [WPF]"
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
caps.latest.revision: 36
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 35
---
# WPF 增益集概觀
<a name="Introduction"></a> [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 包含的增益集模型可以讓開發人員用來建立支援增益集擴充性的應用程式。  這個增益集模型可以讓建立的增益集與應用程式功能進行整合，並擴充應用程式功能。  在某些案例中，應用程式也需要顯示增益集所提供的 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。  本主題顯示 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 如何擴大 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型以促成這些案例、其背後的架構、所帶來的優點以及限制。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Requirements"></a>   
## 必要條件  
 必須要熟悉 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型。  如需詳細資訊，請參閱 [增益集和擴充性](../../../../ml/index.xml)。  
  
<a name="AddInsOverview"></a>   
## 增益集概觀  
 為了避免在併入新功能時，應用程式的重新編譯和重新部署過於複雜，應用程式會實作擴充性機制讓開發人員 \(不論是第一方或是協力廠商\) 建立要與應用程式進行整合的其他應用程式。  最常用來支援這類型擴充性的方式是使用增益集 \(亦稱為「附加元件」和「外掛程式」\)。  會使用增益集公開擴充性的實際應用程式範例包括：  
  
-   Internet Explorer 附加元件  
  
-   Windows Media Player 外掛程式  
  
-   Visual Studio 增益集  
  
 舉例來說，Windows Media Player 增益集模型可以讓協力廠商開發人員實作以各種方式擴充 Windows Media Player 的「外掛程式」，包括建立 Windows Media Player 本身不支援的媒體格式的解碼器和編碼器 \(例如 DVD、MP3\)、音訊效果和面板。  每個增益集模型是建置來公開應用程式獨一無二的功能，雖然對所有增益集模型來說有許多共通的實體和行為。  
  
 一般的增益集擴充性方案有三個主要實體：「*合約*」\(Contract\)、「*增益集*」\(Add\-in\) 和「*主應用程式*」\(Host application\)。  合約會以兩種方式定義增益集要如何與主應用程式進行整合：  
  
-   增益集整合由主應用程式所實作的功能。  
  
-   主應用程式公開功能讓增益集進行整合。  
  
 為了能夠使用增益集，主應用程式在執行階段需要找出並載入增益集。  因此，支援增益集的應用程式具有下列額外的責任：  
  
-   **探索**：找到符合主應用程式所支援合約的增益集。  
  
-   **啟動**：載入增益集、執行增益集並建立與增益集的通訊。  
  
-   **隔離**：使用應用程式定義域或處理序來建立隔離界限，保護應用程式免於發生與增益集相關的可能安全性和執行問題。  
  
-   **通訊**：藉由呼叫方法和傳遞資料，讓增益集和主應用程式能跨越隔離界限彼此通訊。  
  
-   **存留期管理**：以乾淨的可預測方式載入和卸載應用程式定義域和處理序 \(請參閱[應用程式定義域](../../../../docs/framework/app-domains/application-domains.md)\)。  
  
-   **版本控制**：確保主應用程式和增益集在建立新版本時，仍能互相通訊。  
  
 最後，開發穩固的增益集模型是一項非同小可的作業。  因此，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 提供您用於建置增益集模型的基礎結構。  
  
> [!NOTE]
>  如需增益集的詳細資訊，請參閱[增益集和擴充性](../../../../ml/index.xml)。  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## .NET Framework 增益集模型概觀  
 在 <xref:System.AddIn> 命名空間內可以找到的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型，包含一組設計用來簡化增益集擴充性開發的型別。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型的基本單位是「*合約*」\(Contract\)，用來定義主應用程式和增益集彼此通訊的方式。  合約是使用主應用程式專用的合約「*檢視*」\(View\) 而公開給主應用程式的。  同樣地，增益集專用的合約「*檢視*」\(View\) 會公開給增益集。  「*配接器*」\(Adapter\) 則可以用來讓主應用程式和增益集在相對的合約檢視間進行通訊。  合約、檢視和配接器稱為區段，而一組相關的區段則構成「*管線*」\(Pipeline\)。  管線是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型用來支援下列責任的基礎：探索、啟動、安全性隔離、執行隔離 \(同時使用應用程式定義域和處理序\)、通訊、存留期管理和版本控制。  
  
 這項支援的總合效應可以讓開發人員建置能與主應用程式功能整合的增益集。  然而，某些案例需要主應用程式顯示增益集所提供的 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。  因為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中的每項展示技術都有自己實作 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的模型，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型並不支援任何特定的展示技術。  因而，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 改以增益集的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 支援來擴充 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型。  
  
<a name="WPFAddInModel"></a>   
## WPF 增益集  
 對於需要主應用程式顯示增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的各式各樣案例，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 搭配 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型可以讓您解決這些案例。  特別是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可以使用下列兩種程式設計模型，解決這些案例：  
  
1.  **增益集傳回使用者介面**：  增益集會透過合約所定義的方法呼叫將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 傳回給主應用程式。  這個案例用於下列情況：  
  
    -   增益集所傳回的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 外觀是由僅於執行階段存在的資料或條件來決定的，例如動態產生的報告。  
  
    -   增益集提供給服務的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，與使用增益集的主應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 不同。  
  
    -   增益集主要是執行主應用程式的服務，並以 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 回報狀態給主應用程式。  
  
2.  **增益集是使用者介面**：  增益集是合約所定義的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  這個案例用於下列情況：  
  
    -   增益集不提供顯示以外的服務，例如通告。  
  
    -   增益集提供給服務的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，對於使用增益集的所有主應用程式是通用的，例如計算機或色彩選擇器。  
  
 這些案例需要在主應用程式和增益集應用程式定義域間傳遞 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 物件。  因為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型仰賴應用程式定義域間的遠端通訊，所以兩者間傳遞的物件必須是可遠端處理的。  
  
 可遠端處理的物件是會進行下列一個或多個作業的類別執行個體：  
  
-   衍生自 <xref:System.MarshalByRefObject> 類別。  
  
-   實作 <xref:System.Runtime.Serialization.ISerializable> 介面。  
  
-   有套用 <xref:System.SerializableAttribute> 屬性。  
  
> [!NOTE]
>  如需建立可遠端處理的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件的詳細資訊，請參閱[Making Objects Remotable](http://msdn.microsoft.com/zh-tw/01197253-3f13-43b7-894d-9683e431192a)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 型別無法遠端處理。  為了解決問題，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 擴充的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型，可以讓增益集建立的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 從主應用程式顯示。  這項支援是由 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 藉由兩種型別提供的：<xref:System.AddIn.Contract.INativeHandleContract> 介面，以及由 <xref:System.AddIn.Pipeline.FrameworkElementAdapters> 類別實作的兩個靜態方法：<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。  在較高的層級上，這些型別和方法是以下列方式使用的：  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要求增益集所提供 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的類別是直接或間接衍生自 <xref:System.Windows.FrameworkElement>，例如圖案、控制項、使用者控制項、配置面板和頁面。  
  
2.  在合約宣告要在增益集和主應用程式間傳遞使用者介面時，必須宣告為 <xref:System.AddIn.Contract.INativeHandleContract> \(而非 <xref:System.Windows.FrameworkElement>\)，<xref:System.AddIn.Contract.INativeHandleContract> 是可以跨隔離界限傳遞的增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的可遠端處理表示。  
  
3.  在從增益集的應用程式定義域傳遞出來以前，<xref:System.Windows.FrameworkElement> 是藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 而封裝為 <xref:System.AddIn.Contract.INativeHandleContract>。  
  
4.  在傳遞到主應用程式的應用程式定義域之後，<xref:System.AddIn.Contract.INativeHandleContract> 必須藉由呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 而封裝為 <xref:System.Windows.FrameworkElement>。  
  
 <xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 的使用方式取決於特定的案例。  下列小節提供每種程式設計模型的詳細資訊。  
  
<a name="ReturnUIFromAddInContract"></a>   
## 增益集傳回使用者介面  
 為了讓增益集傳回 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 給主應用程式，需要下列條件：  
  
1.  主應用程式、增益集和管線必須依 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [增益集和擴充性](../../../../ml/index.xml)文件所描述的方式建立。  
  
2.  合約必須實作 <xref:System.AddIn.Contract.IContract> 以傳回 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，合約必須使用型別 <xref:System.AddIn.Contract.INativeHandleContract> 的傳回值來宣告方法。  
  
3.  在增益集和主應用程式間傳遞的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，必須直接或間接衍生自 <xref:System.Windows.FrameworkElement>。  
  
4.  增益集傳回的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 在跨越隔離界限之前，必須從 <xref:System.Windows.FrameworkElement> 轉換為 <xref:System.AddIn.Contract.INativeHandleContract>。  
  
5.  傳回的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 在跨越隔離界限之後，必須從 <xref:System.AddIn.Contract.INativeHandleContract> 轉換為 <xref:System.Windows.FrameworkElement>。  
  
6.  主應用程式顯示傳回的 <xref:System.Windows.FrameworkElement>。  
  
 如需示範如何實作傳回 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 之增益集的範例，請參閱 [建立傳回 UI 的增益集](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)。  
  
<a name="AddInIsAUI"></a>   
## 增益集是使用者介面  
 當增益集是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，需要下列條件：  
  
1.  主應用程式、增益集和管線必須依 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] [增益集和擴充性](../../../../ml/index.xml)文件所描述的方式建立。  
  
2.  增益集的合約介面必須實作 <xref:System.AddIn.Contract.INativeHandleContract>。  
  
3.  傳遞給主應用程式的增益集必須直接或間接衍生自 <xref:System.Windows.FrameworkElement>。  
  
4.  在跨越隔離界限之前，增益集必須從 <xref:System.Windows.FrameworkElement> 轉換為 <xref:System.AddIn.Contract.INativeHandleContract>。  
  
5.  在跨越隔離界限之後，增益集必須從 <xref:System.AddIn.Contract.INativeHandleContract> 轉換為 <xref:System.Windows.FrameworkElement>。  
  
6.  主應用程式顯示傳回的 <xref:System.Windows.FrameworkElement>。  
  
 如需示範如何實作是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 之增益集的範例，請參閱 [建立本身為 UI 的增益集](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md)。  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## 從增益集傳回多個使用者介面  
 增益集通常會提供多個 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 給主應用程式顯示。  舉例來說，請考慮當增益集本身是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，也會提供狀態資訊給主應用程式，也就是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  這樣的增益集可以藉由結合使用[增益集傳回使用者介面](#ReturnUIFromAddInContract)和[增益集是使用者介面](#AddInIsAUI)兩種模型的技術來實作。  
  
<a name="AddInsAndXBAPs"></a>   
## 增益集和 XAML 瀏覽器應用程式  
 在目前為止的範例中，主應用程式是一個獨立安裝的應用程式。  然而，[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 也可以裝載增益集，儘管需要下列額外的建置和實作需求：  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式資訊清單必須特別設定，以將管線 \(資料夾和組件\) 和增益集組件下載到用戶端電腦的 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 應用程式快取，與 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 位於相同資料夾。  
  
-   用於探索和載入增益集的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 程式碼必須使用 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 應用程式快取，做為管線和增益集的位置。  
  
-   如果增益集參考位於來源網站的鬆散檔案時，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 必須將增益集載入到特別的安全性內容中。當增益集是由 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 所裝載時，增益集只能參考位於主應用程式來源網站的鬆散檔案。  
  
 在接下來的小節中會詳細描述這些工作。  
  
### 設定 ClickOnce 部署的管線和增益集  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 是下載到 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 部署快取的安全資料夾中，並從該位置執行的。  為了讓 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 裝載增益集，也必須下載管線和增益集組件到安全資料夾中。  若要達成這項作業，需要設定應用程式資訊清單以包含要下載的管線和增益集組件。  這項作業最容易在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中完成，雖然管線和增益集組件需要位於主應用程式 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案根資料夾中，才能讓 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 偵測到管線組件。  
  
 因此，第一步是將管線和增益集組件建置到 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案根資料夾，方法是設定每個管線組件和增益集組件專案的建置輸出。  下表顯示管線組件專案和增益集組件專案的建置輸出路徑，它們與主應用程式 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案位於相同方案和根資料夾中。  
  
 表格 1：由 XBAP 裝載的管線組件的建置輸出路徑  
  
|管線組件專案|建置輸出路徑|  
|------------|------------|  
|合約|`..  \HostXBAP\Contracts\`|  
|增益集檢視|`..  \HostXBAP\AddInViews\`|  
|增益集端配接器|`..  \HostXBAP\AddInSideAdapters\`|  
|主應用程式端配接器|`..  \HostXBAP\HostSideAdapters\`|  
|增益集|`..  \HostXBAP\AddIns\WPFAddIn1`|  
  
 下一步是指定管線組件和增益集組件做為 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 內容檔，執行的動作如下：  
  
1.  藉由在 \[方案總管\] 中以滑鼠右鍵按一下每個管線資料夾並選擇 \[**加入至專案**\]，將管線和增益集組件包含在專案中。  
  
2.  從 \[**屬性**\] 視窗中，將每個管線組件和增益集組件的 \[**建置動作**\] 設定為 \[**內容**\]。  
  
 最後一個步驟是設定應用程式資訊清單，以包含要下載的管線組件檔和增益集組件檔。  檔案所在的資料夾，應該是 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式所佔有的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 快取中的根資料夾。  藉由在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中進行下列動作，可以完成組態設定：  
  
1.  以滑鼠右鍵按一下 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案，然後依序按一下 \[**屬性**\]、\[**發行**\] 和 \[**應用程式檔案**\] 按鈕。  
  
2.  在 \[**應用程式檔案**\] 對話方塊中，將每個管線和增益集 DLL 的 \[**發行狀態**\] 設定為 \[**包含 \(自動\)**\]，再將每個管線和增益集 DLL 的 \[**下載群組**\] 設定為 \[**\(必要項\)**\]。  
  
### 使用應用程式基底的管線和增益集  
 針對 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 部署設定管線和增益集時，它們會下載到跟 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 相同的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 快取資料夾。  若要使用 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的管線和增益集，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 程式碼必須從應用程式基底取得它們。  使用管線和增益集的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型，具有各種型別和成員，對於這個案例提供特別的支援。  首先，路徑是藉由 <xref:System.AddIn.Hosting.PipelineStoreLocation> 列舉值識別的。  對於使用包含下列項目的管線，您可以搭配相關增益集成員的多載使用這個值：  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
-   [AddInStore.FindAddIns\(Type, PipelineStoreLocation, String\<xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=fullName>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
### 存取主應用程式來源網站  
 為了確保增益集可以參考來源網站的檔案，增益集的載入必須使用相當於主應用程式的安全性隔離。  這個安全性層級是由 <xref:System.AddIn.Hosting.AddInSecurityLevel?displayProperty=fullName> 列舉值識別的，並在增益集啟動時傳遞給 <xref:System.AddIn.Hosting.AddInToken.Activate%2A> 方法。  
  
<a name="WPFAddInModelArchitecture"></a>   
## WPF 增益集架構  
 如同我們先前所看到的，在最高層級上，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可以使用 <xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，讓 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集實作 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] \(直接或間接衍生自 <xref:System.Windows.FrameworkElement>\)。  結果是主應用程式傳回的 <xref:System.Windows.FrameworkElement>，是從主應用程式中 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 顯示的。  
  
 對於簡單的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 增益集案例，這樣已夠詳盡到滿足開發人員的需求。  至於較為複雜的案例，特別是嘗試使用其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 服務 \(例如配置、資源和資料繫結\) 的案例，就需要 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 如何使用 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 支援擴充 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型的更為詳盡的知識，才能了解其優點和限制。  
  
 基本上，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 不會從增益集傳遞 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 給主應用程式，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會改為藉由使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 互通性 \(Interoperability\) 傳遞 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 Win32 視窗控制代碼 \(Window Handle\)。  因此，當增益集的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 傳遞到主應用程式時，會發生下列：  
  
-   在增益集端，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 取得將由主應用程式顯示的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的視窗控制代碼。  視窗控制代碼是由衍生自 <xref:System.Windows.Interop.HwndSource> 並會實作 <xref:System.AddIn.Contract.INativeHandleContract> 的內部 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 類別所封裝的。  <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 會傳回這個類別的執行個體，且該執行個體是從增益集的應用程式定義域封送處理到主應用程式的應用程式定義域。  
  
-   在主應用程式端，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會將 <xref:System.Windows.Interop.HwndSource> 重新封裝為衍生自 <xref:System.Windows.Interop.HwndHost> 並使用 <xref:System.AddIn.Contract.INativeHandleContract> 的內部 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 類別。  <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 會傳回這個類別的執行個體到主應用程式。  
  
 藉由視窗控制代碼識別，<xref:System.Windows.Interop.HwndHost> 的存在可以顯示來自 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。  如需詳細資訊，請參閱 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。  
  
 總結來說，<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 和 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 的存在，可以讓 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的視窗控制代碼從增益集傳遞到主應用程式，它是透過 <xref:System.Windows.Interop.HwndHost> 封裝並會顯示主應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
> [!NOTE]
>  因為主應用程式取得 <xref:System.Windows.Interop.HwndHost>，主應用程式無法將 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 傳回的物件轉換為增益集實作的型別 \(舉例來說，<xref:System.Windows.Controls.UserControl>\)。  
  
 就本質而言，<xref:System.Windows.Interop.HwndHost> 的某些限制會影響主應用程式的使用方式。  然而，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會針對增益集案例以數種功能擴充 <xref:System.Windows.Interop.HwndHost>。  這些優點和限制描述如下。  
  
<a name="WPFAddInModelBenefits"></a>   
## WPF 增益集優點  
 因為 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 是從主應用程式使用衍生自 <xref:System.Windows.Interop.HwndHost> 的內部類別而顯示的，這些 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 是由相對於 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 服務的 <xref:System.Windows.Interop.HwndHost> 功能所約束的，相關服務的範例有配置、轉譯、資料繫結、樣式、樣板和資源。  然而，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會以包含下列項目的額外功能，擴大其內部 <xref:System.Windows.Interop.HwndHost> 子類別：  
  
-   在主應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 和增益集的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 間切換。  請注意，「增益集是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]」程式設計模型需要增益集端配接器覆寫 <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> 以啟用切換，不論增益集是完全信任的或部分信任的。  
  
-   承認從主應用程式 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 顯示的增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的可及性需求。  
  
-   啟用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式以在多種應用程式定義域案例中安全執行。  
  
-   當增益集在安全性隔離環境 \(也就是部分信任的安全性沙箱\) 下執行時，防止對增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 視窗控制代碼的非法存取。  呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 可以確保這個安全性：  
  
    -   對於「增益集傳回 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]」程式設計模型，跨越隔離界限傳遞增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的視窗控制代碼的唯一方式是呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。  
  
    -   對於「增益集是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]」程式設計模型，則需要覆寫增益集端配接器的 <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> 並呼叫 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> \(如前述範例所示\)，就如同從主應用程式端配接器呼叫增益集端配接器的 `QueryContract` 實作。  
  
-   提供多重應用程式定義域執行保護。  由於應用程式定義域的限制，增益集應用程式定義域中擲回的未處理例外狀況會造成整個應用程式毀損，即使有隔離界線存在。  然而，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 和 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型提供簡單的方式，可以解決這個問題並增進應用程式穩定性。  如果主應用程式是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式，顯示 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 增益集會針對應用程式定義執行所在的執行緒建立 <xref:System.Windows.Threading.Dispatcher>。  藉由處理 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 增益集 <xref:System.Windows.Threading.Dispatcher> 的 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 事件，您可以偵測到應用程式定義域中發生的所有未處理例外狀況。  您可以從 <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> 屬性取得 <xref:System.Windows.Threading.Dispatcher>。  
  
<a name="WPFAddInModelLimitations"></a>   
## WPF 增益集限制  
 除了 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 針對 <xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.HwndHost> 和視窗控制代碼提供的預設行為所帶來的優點之外，對於從主應用程式顯示的增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，也有其他限制：  
  
-   從主應用程式顯示的增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，並不會遵從主應用程式的裁剪行為。  
  
-   互通性案例中的「*空間*」\(Airspace\) 概念也適用於增益集 \(請參閱 [技術領域概觀](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)\)。  
  
-   資源繼承、資料繫結和命令使用這類的主應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 服務，並不會自動提供給增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。  若要提供這些服務給增益集，您需要更新管線。  
  
-   增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 無法旋轉、調整大小、扭曲或是經過其他方式的轉換 \(請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)\)。  
  
-   藉由 <xref:System.Drawing> 命名空間的繪製作業轉譯的增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 內的內容，可以包含 Alpha 混色。  然而，包含該內容的增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 和主應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 都必須是 100% 不透明的，換句話說，這兩個的 `Opacity` 屬性都必須設為 1。  
  
-   如果包含增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的主應用程式中視窗的 <xref:System.Windows.Window.AllowsTransparency%2A> 屬性設定為 `true`，就看不見增益集。  即使增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 是 100% 不透明 \(也就是 `Opacity` 屬性值為 1\)，也是如此。  
  
-   增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 必須出現在相同的最上層視窗中的其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 項目上方。  
  
-   增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中沒有任何部分可以使用 <xref:System.Windows.Media.VisualBrush> 轉譯。  但增益集可以快照產生的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，以藉由使用合約所定義的方法，建立可以傳遞給主應用程式的點陣圖。  
  
-   在增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中不能播放 <xref:System.Windows.Controls.MediaElement> 的媒體檔案。  
  
-   增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 產生的滑鼠事件也不能由主應用程式接收或引發，且主應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 `IsMouseOver` 屬性值為 `false`。  
  
-   當焦點在增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的控制項間移動時，`GotFocus` 和 `LostFocus` 事件不能由主應用程式接收或引發。  
  
-   包含增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的主應用程式部分在列印時會顯示為空白。  
  
-   如果主應用程式還在繼續執行的話，增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 建立的所有分派者 \(請參閱 <xref:System.Windows.Threading.Dispatcher>\) 必須在卸載擁有者增益集之前手動關閉。  合約可以實作方法，讓主應用程式在卸載增益集之前發出信號給增益集，因此讓增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 可以關閉其分派者。  
  
-   如果增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 是 <xref:System.Windows.Controls.InkCanvas> 或包含 <xref:System.Windows.Controls.InkCanvas>，就無法卸載增益集。  
  
<a name="PerformanceOptimization"></a>   
## 效能最佳化  
 在使用多個應用程式定義域時，根據預設，每個應用程式所需要的各種 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 組件，都會載入到該應用程式定義域中。  因此，建立新應用程式定義域和啟動當中的應用程式所需要的時間，就可能會影響到效能。  然而，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 提供您一個降低啟動時間的方式，方法是指示應用程式在已經載入組件時，跨越應用程式定義域來共用組件。  藉由使用 <xref:System.LoaderOptimizationAttribute> 屬性就可以達成這項作業，該屬性必須套用到進入點 \(Entry Point\) 方法 \(`Main`\) 上。  在這個情況下，您只能使用程式碼實作應用程式定義 \(請參閱[應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)\)。  
  
## 請參閱  
 <xref:System.LoaderOptimizationAttribute>   
 [增益集和擴充性](../../../../ml/index.xml)   
 [應用程式定義域](../../../../docs/framework/app-domains/application-domains.md)   
 [.NET Framework Remoting Overview](http://msdn.microsoft.com/zh-tw/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)   
 [Making Objects Remotable](http://msdn.microsoft.com/zh-tw/01197253-3f13-43b7-894d-9683e431192a)   
 [HOW TO 主題](../../../../docs/framework/wpf/app-development/how-to-topics.md)