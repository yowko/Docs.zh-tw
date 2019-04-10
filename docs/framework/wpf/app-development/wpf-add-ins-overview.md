---
title: WPF 增益集概觀
ms.date: 03/30/2017
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
ms.openlocfilehash: 7c02ddca01260a68880630bcb014c5cc4dc4370b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304801"
---
# <a name="wpf-add-ins-overview"></a>WPF 增益集概觀
<a name="Introduction"></a> .NET Framework 包含開發人員可用來建立支援增益集擴充性的應用程式增益集模型。 此增益集模型可讓您建立增益集，整合並擴充應用程式的功能。 在某些情況下，應用程式也需要顯示增益集所提供的使用者介面。本主題說明 WPF 擴大.NET Framework 增益集模型以啟用這些案例、 架構、 其優點，以及其限制背後的方式。  

<a name="Requirements"></a>   
## <a name="prerequisites"></a>必要條件  
 需要熟悉.NET Framework 增益集模型。 如需詳細資訊，請參閱[增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。  
  
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
  
-   **探索**:尋找增益集遵守主應用程式所支援的合約。  
  
-   **啟用**:正在載入、 執行及建立與增益集的通訊。  
  
-   **隔離**:若要建立隔離界限，防範潛在的安全性和增益集的執行問題的應用程式中使用應用程式定義域或處理程序。  
  
-   **通訊**:讓增益集和主應用程式之間的通訊方式跨越隔離界限呼叫方法，並將資料傳送。  
  
-   **存留期管理**:載入和卸載應用程式定義域和處理程序簡潔、 可預測的方式 (請參閱[應用程式定義域](../../app-domains/application-domains.md))。  
  
-   **版本控制**:確保，主應用程式和增益集仍可進行通訊時，會建立為新版本。  
  
 最後，開發強固的增益集模型是重要的工作。 基於這個理由，.NET Framework 提供基礎結構建置增益集模型。  
  
> [!NOTE]
>  如需增益集的詳細資訊，請參閱[增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))。  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>.NET Framework 增益集模型概觀  
 在中找到.NET Framework 增益集模型，<xref:System.AddIn>命名空間，包含一組專為簡化增益集擴充性的開發工作的類型。 .NET Framework 增益集模型的基本單位是*合約*、 定義如何主應用程式和增益集彼此通訊。 合約會向使用合約主應用程式特定「檢視」的主應用程式公開。 同樣地，合約的增益集專用「檢視」也會向增益集公開。 「配接器」用以讓主應用程式和增益集在其各自的合約檢視間進行通訊。 合約、檢視和配接器稱為區段，一組相關的區段構成「管線」。 管線是在其.NET Framework 增益集模型支援探索、 啟用、 安全性隔離、 執行隔離 （使用應用程式定義域和處理程序）、 通訊、 生命週期管理和版本控制的基礎。  
  
 這項支援的要點是讓開發人員建置增益集，整合主應用程式的功能。 不過，某些情況下需要主應用程式顯示增益集所提供的使用者介面。因為.NET Framework 中的每種簡報技術都有自己的模型，來實作使用者介面，.NET Framework 增益集模型不支援任何特定的簡報技術。 相反地，WPF 會擴充.NET Framework 增益集模型與增益集的 UI 支援。  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>WPF 增益集  
 WPF 中，搭配.NET Framework 增益集模型，可讓您解決各種需要主應用程式顯示使用者介面增益集的案例。特別是，這些案例中討論的 wpf 使用下列兩種程式設計模型：  
  
1. **增益集傳回 UI**。 增益集傳回 UI 主應用程式透過方法呼叫，如合約所定義。 此案例用於下列情況︰  
  
    -   UI 的增益集所傳回的外觀取決於資料，或已存在的條件只會在執行階段，例如動態產生的報告。  
  
    -   可以使用增益集主應用程式的 UI 與不同的 UI 的增益集所提供的服務。  
  
    -   增益集主要執行主應用程式的服務，並將狀態回報給主應用程式 ui。  
  
2. **增益集為 UI**。 增益集為 UI 中，合約所定義。 此案例用於下列情況︰  
  
    -   增益集不提供顯示以外的服務，例如廣告。  
  
    -   UI 的增益集所提供的服務是通用於所有的裝載應用程式可以使用該增益集，例如計算機或色彩選擇器。  
  
 這些案例需要 UI 物件，可以在主應用程式和增益集應用程式定義域之間傳遞。 .NET Framework 增益集模型仰賴的遠端應用程式定義域之間通訊的情況下，因為它們之間傳遞的物件必須可遠端處理。  
  
 可在遠端處理的物件是執行下列一或多個工作的類別執行個體︰  
  
-   衍生自<xref:System.MarshalByRefObject>類別。  
  
-   實作 <xref:System.Runtime.Serialization.ISerializable> 介面。  
  
-   具有<xref:System.SerializableAttribute>套用的屬性。  
  
> [!NOTE]
>  如需建立可遠端處理.NET Framework 物件的詳細資訊，請參閱[讓物件變成可遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))。  
  
 WPF UI 型別不是可遠端處理。 若要解決此問題，WPF 會擴充.NET Framework 增益集模型可讓 WPF UI 增益集所建立要顯示從主應用程式。 這項支援由兩種類型的 WPF 所提供：<xref:System.AddIn.Contract.INativeHandleContract>介面和實作的兩個靜態方法<xref:System.AddIn.Pipeline.FrameworkElementAdapters>類別：<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>和<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。 概括而言，這些類型和方法的使用方式如下︰  
  
1. WPF 可讓您需要增益集所提供的使用者介面會直接或間接衍生自的類別<xref:System.Windows.FrameworkElement>，例如圖形、 控制項、 使用者控制項、 版面配置面板和頁面。  
  
2. 只要合約宣告 UI，將增益集與主應用程式之間傳遞，它必須宣告為<xref:System.AddIn.Contract.INativeHandleContract>(不<xref:System.Windows.FrameworkElement>);<xref:System.AddIn.Contract.INativeHandleContract>是可以跨隔離界限傳遞增益集 UI 可從遠端表示。  
  
3. 從增益集的應用程式定義域中，在傳遞之前<xref:System.Windows.FrameworkElement>會封裝成<xref:System.AddIn.Contract.INativeHandleContract>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。  
  
4. 傳遞至主應用程式的應用程式定義域之後,<xref:System.AddIn.Contract.INativeHandleContract>必須重新封裝為<xref:System.Windows.FrameworkElement>藉由呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>。  
  
 如何<xref:System.AddIn.Contract.INativeHandleContract>， <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>，和<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>使用取決於特定案例。 下列各節提供每個程式設計模型的詳細資料。  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>增益集傳回使用者介面  
 增益集來傳回主應用程式的 UI，需要下列條件：  
  
1. 主應用程式、 增益集和管線必須建立，由.NET Framework 所述[增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))文件。  
  
2. 合約必須實作<xref:System.AddIn.Contract.IContract>，返回 UI，合約必須宣告具有型別的傳回值的方法<xref:System.AddIn.Contract.INativeHandleContract>。  
  
3. UI 的增益集與主應用程式之間傳遞必須直接或間接衍生自<xref:System.Windows.FrameworkElement>。  
  
4. 必須從轉換由增益集 UI<xref:System.Windows.FrameworkElement>至<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限之前。  
  
5. 必須從轉換的 UI 中，會傳回<xref:System.AddIn.Contract.INativeHandleContract>至<xref:System.Windows.FrameworkElement>跨越隔離界限之後。  
  
6. 主應用程式會顯示傳回<xref:System.Windows.FrameworkElement>。  
  
 如需示範如何實作傳回 UI 的增益集的範例，請參閱 <<c0> [ 建立增益集傳回 UI](how-to-create-an-add-in-that-returns-a-ui.md)。  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>增益集是使用者介面  
 當增益集 UI，需要下列條件：  
  
1. 主應用程式、 增益集和管線必須建立，由.NET Framework 所述[增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))文件。  
  
2. 增益集的合約介面必須實作<xref:System.AddIn.Contract.INativeHandleContract>。  
  
3. 傳遞至主應用程式增益集必須直接或間接衍生自<xref:System.Windows.FrameworkElement>。  
  
4. 增益集必須從轉換<xref:System.Windows.FrameworkElement>至<xref:System.AddIn.Contract.INativeHandleContract>跨越隔離界限之前。  
  
5. 增益集必須從轉換<xref:System.AddIn.Contract.INativeHandleContract>至<xref:System.Windows.FrameworkElement>跨越隔離界限之後。  
  
6. 主應用程式會顯示傳回<xref:System.Windows.FrameworkElement>。  
  
 如需示範如何實作本身為 UI 的增益集的範例，請參閱 <<c0> [ 增益集也就是建立 UI](how-to-create-an-add-in-that-is-a-ui.md)。  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>從增益集傳回多個 UI  
 增益集通常會提供多個主應用程式顯示使用者介面。 例如，請考慮為也會提供裝載應用程式的狀態資訊也做為 UI 的 UI 的增益集。 像這樣的增益集的實作方法是，使用[增益集傳回使用者介面](#ReturnUIFromAddInContract)和[增益集是使用者介面](#AddInIsAUI)模型這兩種技術的組合。  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>增益集和 XAML 瀏覽器應用程式  
 在到目前為止的範例中，主應用程式一直是已安裝的獨立應用程式。 但是 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 也可以裝載增益集，儘管有下列額外組建和實作需求︰  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式資訊清單必須特別設定為將管線 (資料夾和組件) 和增益集組件下載至用戶端電腦的 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 應用程式快取，和 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 在相同的資料夾中。  
  
-   探索及載入增益集的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 程式碼必須使用 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 應用程式快取作為管線和增益集位置。  
  
-   如果增益集參考位於原始網站的鬆散式檔案，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 必須將增益集載入特殊的安全性內容；為 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 所裝載時，增益集只能參考位於主應用程式原始網站的鬆散式檔案。  
  
 下列各小節將詳細說明這些工作。  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>設定 ClickOnce 部署的管線和增益集  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 若要下載並從安全資料夾中執行[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]部署快取。 為了讓 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 裝載增益集，管線和增益集組件必須也下載到安全資料夾。 為達到此目的，您需要設定應用程式資訊清單包含管線和增益集組件以供下載。 這在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 最容易完成，雖然管線和增益集組件需要位在裝載 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案的根資料夾中，才能讓 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 偵測管線組件。  
  
 因此，第一個步驟是設定每個管線組件和增益集組件專案的組建輸出，組建 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案根目錄的管線和增益集組件。 下表顯示管線組件專案及增益集組件專案的組建輸出路徑，這些專案和裝載 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案位在相同的解決方案和根資料夾中。  
  
 表 1:Xbap 裝載之管線組件建置輸出路徑  
  
|管線組件專案|建置輸出路徑|  
|-------------------------------|-----------------------|  
|合約|`..\HostXBAP\Contracts\`|  
|增益集檢視|`..\HostXBAP\AddInViews\`|  
|增益集端配接器|`..\HostXBAP\AddInSideAdapters\`|  
|主控件端配接器|`..\HostXBAP\HostSideAdapters\`|  
|增益集|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 下一步是執行下列步驟，將管線組件和增益集組件指定為 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 的 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 內容檔案︰  
  
1. 以滑鼠右鍵按一下方案總管中每個管線資料夾，然後選擇 [加入至專案]，在專案中包含管線和增益集組件。  
  
2. 從 [屬性] 視窗將每個管線組件和增益集組件的 [建置動作] 設定為 [內容]。  
  
 最後一個步驟，是設定應用程式資訊清單包含管線組件檔和增益集組件檔以供下載。 這些檔案應該位於 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 應用程式佔用的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 快取根資料夾的資料夾中。 執行下列作業可 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 達成設定：  
  
1. 以滑鼠右鍵按一下 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 專案，再依序按一下 [屬性]、[發佈] 和 [應用程式檔案] 按鈕。  
  
2. 在 [應用程式檔案] 對話方塊中，將每個管線和增益集 DLL 的 [發行狀態] 設成 [Include (Auto)] (包含 (自動))，並將每個管線和增益集 DLL 的 [下載群組] 設成 [(必要項)]。  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>使用來自應用程式基底的管線和增益集  
 針對 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]部署設定管線和增益集時，它們會下載到和 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 相同的 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 快取資料夾。 若要使用來自 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的管線和增益集，[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 程式碼必須從應用程式基底取得它們。 不同的類型和成員的.NET Framework 增益集模型使用管線和增益集提供特殊支援此案例中。 首先，會識別路徑<xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase>列舉值。 您使用此值與相關增益集成員的多載處理使用包含下列各項的管線︰  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>存取裝載的原始網站  
 為確保增益集能參考原始網站的檔案，必須使用相當於主應用程式的安全性隔離載入增益集。 此安全性層級由<xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType>列舉值，並傳遞至<xref:System.AddIn.Hosting.AddInToken.Activate%2A>增益集啟動時的方法。  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>WPF 增益集架構  
 在最高的層級，如我們所見，WPF 會讓.NET Framework 增益集來實作使用者介面 (直接或間接衍生自<xref:System.Windows.FrameworkElement>) 使用<xref:System.AddIn.Contract.INativeHandleContract>，<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>和<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>。 結果是主應用程式會傳回<xref:System.Windows.FrameworkElement>所顯示從 UI 的主應用程式。  
  
 簡單 UI 增益集的情況下，這是開發人員需要盡可能詳細的資料。 更複雜的情況下，特別是嘗試使用其他的 WPF 服務，例如版面配置、 資源和資料繫結，更深入了解 WPF 如何擴充.NET Framework 增益集模型與 UI 支援，才能了解它的優點和限制。  
  
 基本上，WPF 未通過 UI 的增益集主應用程式;相反地，WPF 會將傳遞的 Win32 視窗控制代碼的 ui 使用 WPF 互通性。 因此，UI 的增益集從傳遞至主應用程式時，會發生下列情況：  
  
-   在增益集端，WPF 會將顯示在主應用程式的 ui 取得視窗控制代碼。 視窗控制代碼會封裝由內部的 WPF 類別衍生自<xref:System.Windows.Interop.HwndSource>並實作<xref:System.AddIn.Contract.INativeHandleContract>。 此類別的執行個體由<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>並且從增益集的應用程式定義域中主應用程式的應用程式定義域來封送處理。  
  
-   在主機應用程式端，WPF repackages<xref:System.Windows.Interop.HwndSource>做為內部的 WPF 類別衍生自<xref:System.Windows.Interop.HwndHost>，並取用<xref:System.AddIn.Contract.INativeHandleContract>。 此類別的執行個體由<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>主應用程式。  
  
 <xref:System.Windows.Interop.HwndHost> 用以顯示視窗控制代碼，WPF 使用者介面中所識別的使用者介面。 如需詳細資訊，請參閱 [WPF 和 Win32 互通](../advanced/wpf-and-win32-interoperation.md)。  
  
 在 [摘要] <xref:System.AddIn.Contract.INativeHandleContract>， <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>，並<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>存在以允許從傳遞的增益集主應用程式，它會封裝由 WPF UI 的視窗控制代碼<xref:System.Windows.Interop.HwndHost>並顯示主應用程式的 UI。  
  
> [!NOTE]
>  因為主應用程式取得<xref:System.Windows.Interop.HwndHost>，主應用程式無法轉換所傳回的物件<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>型別實作藉由增益集 (比方說， <xref:System.Windows.Controls.UserControl>)。  
  
 本質上，<xref:System.Windows.Interop.HwndHost>有某些限制，會影響主應用程式如何使用它們。 不過，WPF 擴充<xref:System.Windows.Interop.HwndHost>與增益集案例的幾項功能。 下文說明這些優點與限制。  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF 增益集的優點  
 因為 WPF 增益集使用者介面會顯示從主應用程式使用的內部類別衍生自<xref:System.Windows.Interop.HwndHost>，這些使用者介面會受限於各種<xref:System.Windows.Interop.HwndHost>對於 WPF UI 服務，例如版面配置，轉譯、 資料繫結、 樣式、 範本和資源。 不過，WPF 擴大其內部<xref:System.Windows.Interop.HwndHost>子類別與其他功能，包括下列：  
  
-   主應用程式的 UI 和增益集 UI 之間使用 tab 鍵。 請注意，「 增益 」 UI 的程式設計模型需使用增益集端配接器，來覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>以啟用定位處理，無論增益集是完全受信任或部分信任的。  
  
-   接受主機應用程式使用者介面中顯示的增益集使用者介面的協助工具需求。  
  
-   啟用 WPF 應用程式安全地在執行多個應用程式網域的案例。  
  
-   防止不合法存取增益集 UI 視窗控制代碼時使用安全性隔離 （也就是部分信任安全性沙箱） 中執行增益集。 呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>可確保此安全性：  
  
    -   「 增益集傳回 UI 」 程式設計模型，跨越隔離界限傳遞增益集 UI 的視窗控制代碼的唯一方式是呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>。  
  
    -   「 增益 」 UI 程式設計模型，覆寫<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>上為增益集端配接器並呼叫<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>（如上述範例所示） 是必要的因為呼叫增益集端配接器的`QueryContract`實作主應用程式端配接器。  
  
-   提供多個應用程式定義域執行保護。 由於應用程式定義域的限制，增益集應用程式定義域中擲回的未處理例外狀況會導致整個應用程式當機，即使有隔離界限。 不過，WPF 和.NET Framework 增益集模型提供簡單的方式來解決這個問題，並改善應用程式穩定性。 顯示使用者介面的 WPF 增益集建立<xref:System.Windows.Threading.Dispatcher>執行緒上，如果主應用程式是 WPF 應用程式執行的應用程式定義域。 您可以偵測應用程式定義域處理會發生的所有未處理例外狀況<xref:System.Windows.Threading.Dispatcher.UnhandledException>WPF 增益集的事件<xref:System.Windows.Threading.Dispatcher>。 您可以取得<xref:System.Windows.Threading.Dispatcher>從<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>屬性。  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF 增益集限制  
 WPF 會將所提供的預設行為的優點之外<xref:System.Windows.Interop.HwndSource>， <xref:System.Windows.Interop.HwndHost>，和視窗控制代碼，也會顯示從主應用程式的增益集使用者介面的限制：  
  
-   從主應用程式中顯示的增益集使用者介面不遵守主應用程式的裁剪行為。  
  
-   互通性案例中的「空間」概念也適用於增益集 (請參閱[技術領域概觀](../advanced/technology-regions-overview.md))。  
  
-   主應用程式的 UI 服務，例如資源繼承、 資料繫結和命令，不會自動提供給增益集使用者介面。 若要向增益集提供這些服務，您需要更新管線。  
  
-   增益集 UI 無法旋轉、 縮放、 扭曲，或會受到轉換 (請參閱[轉換概觀](../graphics-multimedia/transforms-overview.md))。  
  
-   藉由繪製作業轉譯的增益集使用者介面內的內容<xref:System.Drawing>命名空間可以包含 alpha 混色。 不過，增益集 UI 和主應用程式 UI，其中包含它必須是 100%透明的。換句話說，`Opacity`屬性都必須設定為 1。  
  
-   如果<xref:System.Windows.Window.AllowsTransparency%2A>主應用程式，其中包含增益集 UI 視窗的屬性設定為`true`，增益集是不可見。 這是 true，即使此增益集 UI 是 100%不透明 (也就是`Opacity`屬性具有值為 1)。  
  
-   增益集 UI 必須出現在 WPF 中其他項目相同的最上層視窗之上。  
  
-   可以使用轉譯的增益集 UI 沒有部分<xref:System.Windows.Media.VisualBrush>。 相反地，增益集可能需要建立點陣圖，可以傳遞至主應用程式使用合約所定義的方法產生的 UI 的快照集。  
  
-   無法從播放媒體檔案<xref:System.Windows.Controls.MediaElement>增益集的 UI 中。  
  
-   增益集 ui 所產生的滑鼠事件會不接收也不引發主應用程式，而`IsMouseOver`主應用程式 UI 屬性的值為`false`。  
  
-   當焦點在增益集 UI 的控制項之間移動`GotFocus`和`LostFocus`事件不是接收也不引發由主應用程式。  
  
-   包含增益集 UI 的主應用程式的部分會出現白色列印時。  
  
-   所有 dispatcher (請參閱<xref:System.Windows.Threading.Dispatcher>) 建立的增益集 UI 必須手動關閉的擁有者增益集卸載之前如果主應用程式會繼續執行。 合約可以實作方法，可讓主應用程式，以表示增益集，增益集卸載之前，藉此讓增益集 UI 關閉其 dispatcher。  
  
-   如果增益集 UI <xref:System.Windows.Controls.InkCanvas> ，或包含<xref:System.Windows.Controls.InkCanvas>，您不能卸載增益集。  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>效能最佳化  
 根據預設，當使用多個應用程式定義域時，每個應用程式所需的各種.NET Framework 組件全部載入該應用程式定義域。 如此一來，建立新應用程式定義域以及從其中啟動應用程式所需的時間，可能會影響效能。 不過，.NET Framework 可讓您降低啟動時間，指示應用程式定義域間共用組件，如果已載入的應用程式。 您可以使用<xref:System.LoaderOptimizationAttribute>屬性，它必須套用至進入點方法 (`Main`)。 在此情況下，您必須只使用程式碼實作您的應用程式定義 (請參閱[應用程式管理概觀](application-management-overview.md))。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.LoaderOptimizationAttribute>
- [增益集和擴充性](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [應用程式定義域](../../app-domains/application-domains.md)
- [NET Framework 遠端處理概觀](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [讓物件變成可遠端處理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [HOW TO 主題](how-to-topics.md)
