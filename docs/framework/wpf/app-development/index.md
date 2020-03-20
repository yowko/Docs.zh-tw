---
title: 應用程式開發
ms.date: 01/26/2018
helpviewer_keywords:
- WPF [WPF], about application development
- application development [WPF], about
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
ms.openlocfilehash: 5ff9f58b72982f79e70b80f60c10828c3b54e5bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186008"
---
# <a name="application-development"></a>應用程式開發
<a name="introduction"></a>Windows 演示基礎 （WPF） 是一個演示文稿框架，可用於開發以下類型的應用程式：  
  
- 獨立應用程式（傳統樣式 Windows 應用程式，構建為安裝在用戶端電腦並從用戶端電腦運行的可執行程式集）。  
  
- XAML 瀏覽器應用程式 （XBAPs） （由導航頁組成的應用程式，這些頁面構建為可執行程式集，並由 Web 瀏覽器（如 Microsoft Internet Explorer 或 Mozilla Firefox）託管）。  
  
- 自訂控制項程式庫 (非可執行組件，其中包含可重複使用的控制項)。  
  
- 類別庫 (非可執行組件，其中包含可重複使用的類別)。  
  
> [!NOTE]
> 強烈建議不要在 Windows 服務中使用 WPF 類型。 如果您嘗試在 Windows 服務中使用這些功能，它們可能無法如預期般運作。  
  
 要構建這組應用程式，WPF 實現了大量服務。 本主題提供這些服務的概觀，並說明何處可以找到更多資訊。  

<a name="Application_Management"></a>
## <a name="application-management"></a>應用程式管理  
 可執行檔 WPF 應用程式通常需要一組核心功能，其中包括以下內容：  
  
- 建立及管理通用應用程式基礎結構 (包括建立進入點方法和 Windows 訊息迴圈以接收系統和輸入訊息)。  
  
- 追蹤應用程式存留期並與其互動。  
  
- 擷取及處理命令列參數。  
  
- 共用應用程式範圍的屬性和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]資源。  
  
- 偵測及處理未處理的例外狀況。  
  
- 傳回結束代碼。  
  
- 管理獨立應用程式中的視窗。  
  
- 跟蹤 XAML 瀏覽器應用程式 （XBAPs） 中導航，以及具有導航視窗和框架的獨立應用程式。  
  
 這些功能是由 <xref:System.Windows.Application> 類別實作，您可以使用「應用程式定義」** 將此類別新增至應用程式。  
  
 如需詳細資訊，請參閱[應用程式管理概觀](application-management-overview.md)。  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>
## <a name="wpf-application-resource-content-and-data-files"></a>WPF 應用程式資源、內容和資料檔案  
 WPF 擴展了 Microsoft .NET 框架中嵌入式資源的核心支援，支援三種無法執行的資料檔案：資源、內容和資料。 如需詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)。  
  
 支援 WPF 無法執行資料檔案的一個關鍵元件是使用唯一的 URI 識別和載入它們的能力。 有關詳細資訊，請參閱[WPF 中的打包 URI。](pack-uris-in-wpf.md)  
  
<a name="Windows_and_Dialog_Boxes"></a>
## <a name="windows-and-dialog-boxes"></a>視窗和對話方塊  
 使用者通過視窗與 WPF 獨立應用程式進行交互。 視窗的用途是裝載應用程式內容，以及公開通常可讓使用者與內容互動的應用程式功能。 在 WPF 中，視窗由<xref:System.Windows.Window>類封裝，該類支援：  
  
- 建立及顯示視窗。  
  
- 建立主控視窗/附屬視窗的關聯性。  
  
- 設定視窗外觀 (例如大小、位置、圖示、標題列文字、框線)。  
  
- 追蹤視窗存留期並與其互動。  
  
 如需詳細資訊，請參閱 [WPF 視窗概觀](wpf-windows-overview.md)。  
  
 <xref:System.Windows.Window> 可建立一種特殊的視窗類型，稱為對話方塊。 您可以建立強制回應和非強制回應類型的對話方塊。  
  
 為了方便，以及再使用性和跨應用程式一致的使用者體驗的好處，WPF 公開了三個常見的 Windows 對話方塊： <xref:Microsoft.Win32.OpenFileDialog>、<xref:Microsoft.Win32.SaveFileDialog>和<xref:System.Windows.Controls.PrintDialog>。  
  
 訊息方塊是一種特殊的對話方塊類型，可將重要的文字資訊顯示給使用者，以及詢問簡單的「是/否/確定/取消」問題。 您可以使用 <xref:System.Windows.MessageBox> 類別來建立及顯示訊息方塊。  
  
 如需詳細資訊，請參閱[對話方塊概觀](dialog-boxes-overview.md)。  
  
<a name="Navigation"></a>
## <a name="navigation"></a>導覽  
 WPF 支援使用頁面 （<xref:System.Windows.Controls.Page>） 和超連結 （<xref:System.Windows.Documents.Hyperlink>. . 您可以透過各種方式來實作瀏覽，包括：  
  
- 裝載於網頁瀏覽器的獨立頁面。  
  
- 編譯到 Web 瀏覽器中託管的 XBAP 的頁面。  
  
- 編譯成獨立應用程式並由瀏覽視窗 (<xref:System.Windows.Navigation.NavigationWindow>) 裝載的頁面。  
  
- 由框架 （） 承載的<xref:System.Windows.Controls.Frame>頁面（）可以託管在獨立頁面中，也可以託管到 XBAP 或獨立應用程式中的頁面。  
  
 為了便於導航，WPF 實現了以下操作：  
  
- <xref:System.Windows.Navigation.NavigationService>用於處理 的共用導航引擎，用於處理 的導航<xref:System.Windows.Controls.Frame>請求<xref:System.Windows.Navigation.NavigationWindow>，這些請求用於支援應用程式內部導航。  
  
- 要啟始瀏覽的瀏覽方法。  
  
- 要追蹤瀏覽存留期並與其互動的瀏覽事件。  
  
- 使用日誌記住向後和向前瀏覽，該日誌也可供檢查和操作。  
  
 如需相關資訊，請參閱[瀏覽概觀](navigation-overview.md)。  
  
 WPF 還支援稱為結構化導航的特殊類型的導航。 結構化瀏覽可用來呼叫一或多個頁面，這些頁面會以與呼叫函式一致的結構化且可預期方式傳回資料。 此功能相依於 <xref:System.Windows.Navigation.PageFunction%601> 類別，這在[結構化巡覽概觀](structured-navigation-overview.md)中將進一步說明。 <xref:System.Windows.Navigation.PageFunction%601> 也可用來簡化複雜瀏覽拓撲的建立，這在[巡覽拓撲概觀](navigation-topologies-overview.md)中將進行說明。  
  
<a name="Hosting"></a>
## <a name="hosting"></a>裝載  
 XBAPs 可以託管在微軟 Internet 資源管理器或 Firefox 中。 每個裝載模型有各自的一組考量和條件約束，[裝載](hosting-wpf-applications.md)中將進行說明。  
  
<a name="Build_and_Deploy"></a>
## <a name="build-and-deploy"></a>建置和部署  
 儘管可以使用命令列編譯器從命令提示符構建簡單的 WPF 應用程式，但 WPF 與 Visual Studio 集成，以提供簡化開發和構建過程的其他支援。 如需詳細資訊，請參閱[建置 WPF 應用程式](building-a-wpf-application-wpf.md)。  
  
 根據您建置的應用程式類型，有一或多個部署選項可供選擇。 如需詳細資訊，請參閱[部署 WPF 應用程式](deploying-a-wpf-application-wpf.md)。  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>相關主題  
  
|Title|描述|  
|-----------|-----------------|  
|[應用程式管理概觀](application-management-overview.md)|提供 <xref:System.Windows.Application> 類別的概觀，包括管理應用程式存留期、視窗、應用程式資源和瀏覽。|  
|[WPF 中的視窗](windows-in-wpf-applications.md)|提供在應用程式中管理視窗的詳細資料，包括如何使用 <xref:System.Windows.Window> 類別和對話方塊。|  
|[瀏覽概觀](navigation-overview.md)|提供有關管理在應用程式頁面之間瀏覽的概觀。|  
|[裝載](hosting-wpf-applications.md)|提供 XAML 瀏覽器應用程式 （XBAP） 的概述。|  
|[生成和部署](building-and-deploying-wpf-applications.md)|描述如何建置及部署 WPF 應用程式。|  
|[Visual Studio 中的 WPF 簡介](../getting-started/introduction-to-wpf-in-vs.md)|描述 WPF 的主要功能。|  
|[逐步解說：我的第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)|示範如何建立使用頁面瀏覽、配置、控制項、影像、樣式和繫結之 WPF 應用程式的逐步解說。|
