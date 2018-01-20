---
title: "WPF 增益集概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffd45957b41cdfd8488aedd865aa70ef5b2634b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="wpf-add-ins-overview"></a>WPF 增益集概觀
<a name="Introduction"></a>[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 包含開發人員可用來建立支援增益集擴充性的應用程式增益集模型。 此增益集模型可讓您建立增益集，整合並擴充應用程式的功能。 在某些情況下，應用程式也需要顯示增益集提供的 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。本主題說明 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 如何擴大 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型來啟用這些案例、其背後的架構、其優點及其限制。  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>必要條件  
 熟悉 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型是必要的。 如需詳細資訊，請參閱[增益集和擴充性](../../../../docs/framework/add-ins/index.md)。  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>增益集概觀  
 為避免新功能包含複雜的應用程式重新編譯和重新部署，應用程式會實作擴充性機制，讓開發人員 (第一方和第三方) 建立整合它們的其他應用程式。 支援此擴充性類型最常見的方式是使用增益集 (也稱為「附加元件」和「外掛程式」)。 公開增益集擴充性的真實世界應用程式範例包括︰  
  
-   Internet Explorer 附加元件。  
  
-   Windows Media Player 外掛程式。  
  
-   Visual Studio 增益集。  
  
 例如，Windows Media Player 增益集模型讓協力廠商開發人員實作以各種方式擴充 Windows Media Player 的「外掛程式」，包括建立適用於 Windows Media Player 原本不支援之媒體格式的解碼器和編碼器 (例如 DVD、MP3)、音訊效果和面板。 每個增益集模型都是建置來公開對應用程式的獨特功能，雖然有幾個實體和行為通用所有的增益集模型。  
  
 一般增益集擴充性解決方案的三個主要實體是「合約」、「增益集」和「主應用程式」。 合約定義增益集與主應用程式整合的兩種方式︰  
  
-   增益集整合主應用程式所實作的功能。  
  
-   主應用程式公開要整合的增益集功能。  
  
 為能使用增益集，主應用程式需要在執行階段找到並載入它們。 因此，支援增益集的應用程式有下列額外的責任︰  
  
-   **探索**︰尋找遵守主應用程式所支援合約的增益集。  
  
-   **啟用**︰載入、執行及建立與增益集的通訊。  
  
-   **隔離**︰使用應用程式定義域或處理程序來建立隔離界限，保護應用程式不受增益集的潛在安全性和執行問題影響。  
  
-   **通訊**︰透過呼叫方法及傳送資料，讓增益集及主應用程式跨越隔離界限互相通訊。  
  
-   **存留期管理**︰以簡潔、可預測的方式載入和卸載應用程式定義域和處理程序 (請參閱[應用程式定義域](../../../../docs/framework/app-domains/application-domains.md))。  
  
-   **版本控制**︰確保建立任一新版本時，主應用程式和增益集仍可通訊。  
  
 最後，開發強固的增益集模型是重要的工作。 因此，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 提供基礎結構以建置增益集模型。  
  
> [!NOTE]
>  如需增益集的詳細資訊，請參閱[增益集和擴充性](../../../../docs/framework/add-ins/index.md)。  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>.NET Framework 增益集模型概觀  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集模型中找到<xref:System.AddIn>命名空間，包含一組專為簡化開發的增益集擴充性的型別。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型的基本單位是「合約」，它會定義主應用程式和增益集彼此如何通訊。 合約會向使用合約主應用程式特定「檢視」的主應用程式公開。 同樣地，合約的增益集專用「檢視」也會向增益集公開。 「配接器」用以讓主應用程式和增益集在其各自的合約檢視間進行通訊。 合約、檢視和配接器稱為區段，一組相關的區段構成「管線」。 管線是 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型支援探索、啟動、安全性隔離、執行隔離 (使用應用程式定義域和處理程序)、通訊、生命週期管理和版本控制的基礎。  
  
 這項支援的要點是讓開發人員建置增益集，整合主應用程式的功能。 不過，某些情況下需要主應用程式顯示增益集所提供的 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。因為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中每種簡報技術都有用以實作 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的自有模型，所以 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型不支援任何特定的簡報技術。 而是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會擴充 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型與增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]支援。  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>WPF 增益集  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 聯合 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型，可讓您處理需要主應用程式從增益集顯示 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的各種情況。特別是，這些案例是由 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 與下面兩個程式設計模型所解決︰  
  
1.  **增益集傳回 UI**。 增益集透過方法呼叫將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 傳回主應用程式，如合約所定義。 此案例用於下列情況︰  
  
    -   增益集傳回的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 外觀相依於只存在於執行階段的資料或條件，例如動態產生的報表。  
  
    -   增益集所提供服務的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 不同於可使用增益集之主應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
    -   增益集主要執行主應用程式服務，並向具有 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的主應用程式報告狀態。  
  
2.  **增益集為 UI**。 增益集是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，如合約所定義。 此案例用於下列情況︰  
  
    -   增益集不提供顯示以外的服務，例如廣告。  
  
    -   增益集所提供服務的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 對可以使用該增益集的主應用程式而言很普通，例如計算機或色彩選擇器。  
  
 這些案例需要 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 物件能在主應用程式和增益集應用程式定義域之間傳遞。 因為 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型仰賴應用程式定義域之間的遠端通訊，所以在它們之間傳遞的物件必須可遠端處理。  
  
 可在遠端處理的物件是執行下列一或多個工作的類別執行個體︰  
  
-   衍生自<xref:System.MarshalByRefObject>類別。  
  
-   實作 <xref:System.Runtime.Serialization.ISerializable> 介面。  
  
-   具有<xref:System.SerializableAttribute>套用的屬性。  
  
> [!NOTE]
>  如需建立可遠端處理之 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件的詳細資訊，請參閱[讓物件變成可遠端處理](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 類型不能從遠端處理。 為解決此問題，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會擴充 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型，從主應用程式顯示增益集建立的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 這項支援係由[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]依兩種類型：<xref:System.AddIn.Contract.INativeHandleContract>介面和實作的兩個靜態方法<xref:System.AddIn.Pipeline.FrameworkElementAdapters>類別：<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>和<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。 概括而言，這些類型和方法的使用方式如下︰  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]要求[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]提供增益集是直接或間接衍生自的類別<xref:System.Windows.FrameworkElement>、 圖形、 控制項、 使用者控制項、 版面配置面板和頁面等。  
  
2.  只要合約宣告會在增益集與主應用程式之間傳遞給 UI，它必須宣告為<xref:System.AddIn.Contract.INativeHandleContract>(不<xref:System.Windows.FrameworkElement>);<xref:System.AddIn.Contract.INativeHandleContract>是增益集的遠端執行表示法[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可以跨隔離界限傳遞。  
  
3.  從增益集應用程式定義域中，在傳遞之前<xref:System.Windows.FrameworkElement>封裝為<xref:System.AddIn.Contract.INativeHandleContract>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。  
  
4.  傳遞至主應用程式的應用程式定義域之後,<xref:System.AddIn.Contract.INativeHandleContract>必須重新封裝為<xref:System.Windows.FrameworkElement>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>。  
  
 如何<xref:System.AddIn.Contract.INativeHandleContract>， <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，和<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>可用取決於特定案例。 下列各節提供每個程式設計模型的詳細資料。  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>增益集傳回使用者介面  
 為使增益集將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 傳回至主應用程式，需要︰  
  
1.  您必須建立主應用程式、增益集和管線，如[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)][增益集和擴充性](../../../../docs/framework/add-ins/index.md)一文所述。  
  
2.  必須實作合約<xref:System.AddIn.Contract.IContract>並返回[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，合約必須宣告具有傳回型別值的方法<xref:System.AddIn.Contract.INativeHandleContract>。  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]傳遞增益集與主機之間的應用程式必須直接或間接衍生自<xref:System.Windows.FrameworkElement>。  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]所傳回的增益集必須從轉換<xref:System.Windows.FrameworkElement>至<xref:System.AddIn.Contract.INativeHandleContract>之前跨越隔離界限。  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]傳回必須從轉換<xref:System.AddIn.Contract.INativeHandleContract>至<xref:System.Windows.FrameworkElement>之後跨越隔離界限。  
  
6.  主應用程式會顯示傳回<xref:System.Windows.FrameworkElement>。  
  
 如需示範如何實作會傳回 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的增益集範例，請參閱[建立傳回 UI 的增益集](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)。  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>增益集是使用者介面  
 當增益集是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 時，需要︰  
  
1.  您必須建立主應用程式、增益集和管線，如[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)][增益集和擴充性](../../../../docs/framework/add-ins/index.md)一文所述。  
  
2.  必須實作增益集的合約介面<xref:System.AddIn.Contract.INativeHandleContract>。  
  
3.  傳遞至主應用程式增益集必須直接或間接衍生自<xref:System.Windows.FrameworkElement>。  
  
4.  增益集必須從轉換<xref:System.Windows.FrameworkElement>至<xref:System.AddIn.Contract.INativeHandleContract>之前跨越隔離界限。  
  
5.  增益集必須從轉換<xref:System.AddIn.Contract.INativeHandleContract>至<xref:System.Windows.FrameworkElement>之後跨越隔離界限。  
  
6.  主應用程式會顯示傳回<xref:System.Windows.FrameworkElement>。  
  
 如需示範如何實作本身即為 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的增益集範例，請參閱[建立本身為 UI 的增益集](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md)。  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>從增益集傳回多個 UI  
 增益集通常會提供多個 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 供主應用程式顯示。 例如，增益集是向主應用程式提供狀態資訊的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，也是 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 像這樣的增益集的實作方法是，使用[增益集傳回使用者介面](#ReturnUIFromAddInContract)和[增益集是使用者介面](#AddInIsAUI)模型這兩種技術的組合。  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>增益集和 XAML 瀏覽器應用程式  
 在到目前為止的範例中，主應用程式一直是已安裝的獨立應用程式。 但是 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 也可以裝載增益集，儘管有下列額外組建和實作需求︰  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式資訊清單必須特別設定為將管線 (資料夾和組件) 和增益集組件下載至用戶端電腦的 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 應用程式快取，和 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 在相同的資料夾中。  
  
-   探索及載入增益集的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 程式碼必須使用 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 應用程式快取作為管線和增益集位置。  
  
-   如果增益集參考位於原始網站的鬆散式檔案，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 必須將增益集載入特殊的安全性內容；為 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 所裝載時，增益集只能參考位於主應用程式原始網站的鬆散式檔案。  
  
 下列各小節將詳細說明這些工作。  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>設定 ClickOnce 部署的管線和增益集  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 會下載到 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 部署快取的安全資料夾中並執行。 為了讓 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 裝載增益集，管線和增益集組件必須也下載到安全資料夾。 為達到此目的，您需要設定應用程式資訊清單包含管線和增益集組件以供下載。 這在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 最容易完成，雖然管線和增益集組件需要位在裝載 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案的根資料夾中，才能讓 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 偵測管線組件。  
  
 因此，第一個步驟是設定每個管線組件和增益集組件專案的組建輸出，組建 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案根目錄的管線和增益集組件。 下表顯示管線組件專案及增益集組件專案的組建輸出路徑，這些專案和裝載 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案位在相同的解決方案和根資料夾中。  
  
 表 1：XBAP 裝載之管線組件的組建輸出路徑  
  
|管線組件專案|建置輸出路徑|  
|-------------------------------|-----------------------|  
|合約|`..\HostXBAP\Contracts\`|  
|增益集檢視|`..\HostXBAP\AddInViews\`|  
|增益集端配接器|`..\HostXBAP\AddInSideAdapters\`|  
|主控件端配接器|`..\HostXBAP\HostSideAdapters\`|  
|增益集|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 下一步是執行下列步驟，將管線組件和增益集組件指定為 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 內容檔案︰  
  
1.  以滑鼠右鍵按一下方案總管中每個管線資料夾，然後選擇 [加入至專案]，在專案中包含管線和增益集組件。  
  
2.  從 [屬性] 視窗將每個管線組件和增益集組件的 [建置動作] 設定為 [內容]。  
  
 最後一個步驟，是設定應用程式資訊清單包含管線組件檔和增益集組件檔以供下載。 這些檔案應該位於 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式佔用的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 快取根資料夾的資料夾中。 執行下列作業可 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 達成設定：  
  
1.  以滑鼠右鍵按一下 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案，再依序按一下 [屬性]、[發佈] 和 [應用程式檔案] 按鈕。  
  
2.  在 [應用程式檔案] 對話方塊中，將每個管線和增益集 DLL 的 [發行狀態] 設成 [Include (Auto)] (包含 (自動))，並將每個管線和增益集 DLL 的 [下載群組] 設成 [(必要項)]。  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>使用來自應用程式基底的管線和增益集  
 針對 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]部署設定管線和增益集時，它們會下載到和 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 相同的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 快取資料夾。 若要使用來自 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的管線和增益集，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 程式碼必須從應用程式基底取得它們。 使用管線和增益集的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型各種類型和成員為此狀況提供特殊支援。 首先，路徑識別<xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase>列舉值。 您使用此值與相關增益集成員的多載處理使用包含下列各項的管線︰  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>存取裝載的原始網站  
 為確保增益集能參考原始網站的檔案，必須使用相當於主應用程式的安全性隔離載入增益集。 此安全性層級由<xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType>列舉值，並傳遞給<xref:System.AddIn.Hosting.AddInToken.Activate%2A>增益集啟動時的方法。  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>WPF 增益集架構  
 在最高的層級，如我們所見，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]啟用[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]增益集來實作[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)](直接或間接衍生自<xref:System.Windows.FrameworkElement>) 使用<xref:System.AddIn.Contract.INativeHandleContract>，<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>和<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>。 結果是主應用程式會傳回<xref:System.Windows.FrameworkElement>，系統會從顯示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]主應用程式中。  
  
 若為簡單的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 增益集案例，這是開發人員需要的最詳細資料。 若為更複雜的案例，特別是嘗試使用其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 服務，例如版面配置、資源及資料繫結，需要更深入瞭解 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 如何擴充 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型與 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 支援，以瞭解其優點和限制。  
  
 基本上，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 不會從增益集將 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 傳送到主應用程式；而是 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 互通性傳送 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 Win32 視窗控制代碼。 因此，當 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 從增益集傳遞至主應用程式時，會發生下列情況︰  
  
-   在增益集端，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 取得主應用程式會顯示之 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的視窗控制代碼。 視窗控制代碼封裝內部[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]類別衍生自<xref:System.Windows.Interop.HwndSource>並實作<xref:System.AddIn.Contract.INativeHandleContract>。 這個類別的執行個體由<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>並且從增益集應用程式定義域中主應用程式的應用程式定義域來封送處理。  
  
-   在主機應用程式端， [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] repackages<xref:System.Windows.Interop.HwndSource>為內部[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]類別衍生自<xref:System.Windows.Interop.HwndHost>並取用<xref:System.AddIn.Contract.INativeHandleContract>。 這個類別的執行個體由<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>主應用程式。  
  
 <xref:System.Windows.Interop.HwndHost>顯示存在於[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，從視窗控制代碼，由識別[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。 如需詳細資訊，請參閱 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)。  
  
 在 [摘要] <xref:System.AddIn.Contract.INativeHandleContract>， <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，和<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>存在允許的視窗控制代碼[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]從增益集傳遞至主應用程式，其中由封裝<xref:System.Windows.Interop.HwndHost>和顯示主機應用程式的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
> [!NOTE]
>  因為主應用程式取得<xref:System.Windows.Interop.HwndHost>，主應用程式無法將傳回的物件轉換<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>類型就藉由為增益集 (例如， <xref:System.Windows.Controls.UserControl>)。  
  
 本質上，<xref:System.Windows.Interop.HwndHost>有某些限制，會影響主應用程式如何使用它們。 不過，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]擴充<xref:System.Windows.Interop.HwndHost>與增益集的案例數項功能。 下文說明這些優點與限制。  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF 增益集的優點  
 因為[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]增益集[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]會顯示主機使用的應用程式的內部類別衍生自<xref:System.Windows.Interop.HwndHost>、 those[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]的功能都會受到<xref:System.Windows.Interop.HwndHost>相對於[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]服務，例如版面配置、 轉譯、 資料繫結、 樣式、 範本和資源。 不過，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]擴大其內部<xref:System.Windows.Interop.HwndHost>子類別具有其他功能，包括下列：  
  
-   切換主應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 和增益集的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 請注意，「 增益集是[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]」 程式設計模型需使用增益集端配接器，來覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>啟用按下 tab 鍵，增益集是完全受信任或部分信任的。  
  
-   接受從主應用程式 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 顯示的增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 的協助工具需求。  
  
-   讓 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式在多個應用程式定義域情況下安全執行。  
  
-   在增益集使用安全性隔離執行時 (即部分信任安全性沙箱)，防止不合法存取增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 視窗控制代碼。 呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>可確保此安全性：  
  
    -   針對 「 增益集傳回[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]」 程式設計模型、 傳遞的增益集的視窗控制代碼的唯一方式[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]跨隔離界限，是呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。  
  
    -   「 增益集是[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]」 程式設計模型，覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>呼叫端的新增配接器等<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>（如上述範例所示） 是必要的因為呼叫端的新增配接器的`QueryContract`實作從主應用程式端配接器。  
  
-   提供多個應用程式定義域執行保護。 由於應用程式定義域的限制，增益集應用程式定義域中擲回的未處理例外狀況會導致整個應用程式當機，即使有隔離界限。 不過，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 和 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 增益集模型提供簡單的方式來解決這個問題，並改善應用程式穩定性。 A[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]增益集，顯示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]建立<xref:System.Windows.Threading.Dispatcher>之執行緒上，如果主應用程式執行的應用程式定義域的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式。 您可以偵測所有未處理的例外狀況所處理之應用程式定義域發生<xref:System.Windows.Threading.Dispatcher.UnhandledException>事件[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]增益集的<xref:System.Windows.Threading.Dispatcher>。 您可以取得<xref:System.Windows.Threading.Dispatcher>從<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>屬性。  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF 增益集限制  
 優點之外，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]將加入至所提供的預設行為<xref:System.Windows.Interop.HwndSource>， <xref:System.Windows.Interop.HwndHost>，和視窗控制代碼，也有一些限制 add-in [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] ，會顯示從主應用程式：  
  
-   從主應用程式顯示的增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 不遵守主應用程式的裁剪行為。  
  
-   互通性案例中的「空間」概念也適用於增益集 (請參閱[技術領域概觀](../../../../docs/framework/wpf/advanced/technology-regions-overview.md))。  
  
-   主應用程式的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 服務，例如資源繼承、資料繫結和命令，不會自動提供給增益集 [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]。 若要向增益集提供這些服務，您需要更新管線。  
  
-   增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 不能進行旋轉、縮放、扭曲，也不會受到轉換影響 (請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md))。  
  
-   增益集的內部內容[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]，藉由繪製作業中的從轉譯<xref:System.Drawing>命名空間可以包含透明混色。 不過，包含它的增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 和主應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，兩者都必須是 100% 不透明；換句話說，兩者的 `Opacity` 屬性都必須設為 1。  
  
-   如果<xref:System.Windows.Window.AllowsTransparency%2A>屬性中包含的增益集的主應用程式視窗的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]設`true`，增益集是不可見。 即使增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 是 100% 不透明 (也就是 `Opacity` 屬性值為 1) 也一樣。  
  
-   增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 必須出現在相同最上層視窗中其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 項目的上方。  
  
-   增益集的任何部分[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]使用轉譯<xref:System.Windows.Media.VisualBrush>。 增益集反倒可能採用所產生之 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的快照集建立點陣圖，它可以傳遞至使用合約所定義方法的主應用程式。  
  
-   無法從播放媒體檔案<xref:System.Windows.Controls.MediaElement>增益集中[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  
  
-   主應用程式不接收也不引發針對增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 產生的滑鼠事件，而主應用程式 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的 `IsMouseOver` 屬性有值 `false`。  
  
-   當焦點在增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的控制項之間移動時，主應用程式不接收也不引發 `GotFocus` 和 `LostFocus` 事件。  
  
-   包含增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的主應用程式在列印時有部分會出現白色。  
  
-   所有發送器 (請參閱<xref:System.Windows.Threading.Dispatcher>) 建立的增益集[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]必須關閉手動擁有者增益集卸載之前如果主應用程式會繼續執行。 合約可以實作讓主應用程式先通知增益集再卸載增益集的方法，藉此讓增益集 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 關閉其 Dispatcher。  
  
-   如果增益集[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]是<xref:System.Windows.Controls.InkCanvas>或包含<xref:System.Windows.Controls.InkCanvas>，您不能卸載增益集。  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>效能最佳化  
 根據預設，當使用多個應用程式定義域時，每個應用程式需要的各種 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 組件都會載入該應用程式定義域。 如此一來，建立新應用程式定義域以及從其中啟動應用程式所需的時間，可能會影響效能。 不過，[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 會提供方法讓您降低啟動時間，如已載入，指示應用程式在各應用程式定義域間共用組件。 您可以使用<xref:System.LoaderOptimizationAttribute>屬性必須套用至進入點方法 (`Main`)。 在此情況下，您必須只使用程式碼實作您的應用程式定義 (請參閱[應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md))。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.LoaderOptimizationAttribute>  
 [增益集和擴充性](../../../../docs/framework/add-ins/index.md)  
 [應用程式定義域](../../../../docs/framework/app-domains/application-domains.md)  
 [.NET framework 遠端處理概觀](http://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [讓物件可遠端處理](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [HOW-TO 主題](../../../../docs/framework/wpf/app-development/how-to-topics.md)
