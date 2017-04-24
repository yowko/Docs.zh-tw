---
title: "應用程式開發 | Microsoft Docs"
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
  - "應用程式開發 [WPF], 關於"
  - "WPF, 關於應用程式開發"
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 應用程式開發
<a name="introduction"></a> [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 是一種展示架構，可用來開發下列類型的應用程式：  
  
-   獨立應用程式 \(建置為可執行組件的傳統 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 應用程式，可以安裝到用戶端電腦並從中執行\)。  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] \(以巡覽頁面組成且建置為可執行組件的應用程式，可以由如 [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] 或 Mozilla Firefox 這類的 Web 瀏覽器裝載\)。  
  
-   自訂控制項程式庫 \(非可執行的組件，其中包含可重複使用的控制項\)。  
  
-   類別庫 \(非可執行的組件，其中包含可重複使用的類別\)。  
  
> [!NOTE]
>  我們非常不建議您在 Windows 服務中使用 WPF 型別。  如果您嘗試在 Windows 服務中使用這些功能，它們可能無法如預期般運作。  
  
 為了能夠建置這類應用程式，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會實作多項服務。  本主題將提供這些服務的概觀以及哪裡可以找到詳細資訊。  
  
   
  
<a name="Application_Management"></a>   
## 應用程式管理  
 可執行的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式一般需要一組核心功能，包括下列項目：  
  
-   建立和管理通用應用程式基礎結構 \(包括建立進入點 \(Entry Point\) 方法和 Windows 訊息迴圈，以接收系統和輸入訊息\)。  
  
-   追蹤應用程式的存留期 \(Lifetime\) 並與其互動。  
  
-   擷取和處理命令列參數。  
  
-   共用應用程式範圍屬性和 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 資源。  
  
-   偵測和處理未處理的例外狀況。  
  
-   傳回結束代碼。  
  
-   管理獨立應用程式中的視窗。  
  
-   追蹤 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 中的巡覽，以及獨立應用程式的巡覽視窗和框架 \(Frame\)。  
  
 這些功能都是由 <xref:System.Windows.Application> 類別實作，您可以使用「*應用程式定義*」\(Application Definition\) 將此類別加入到應用程式。  
  
 如需詳細資訊，請參閱[應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)。  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## WPF 應用程式資源、內容和資料檔案  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 擴充了 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 中對內嵌資源的核心支援，能夠支援三種非可執行的資料檔案，包括資源、內容和資料。如需詳細資訊，請參閱 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)。  
  
 支援 WPF 非可執行資料檔案的關鍵之一，就是能夠使用唯一 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 來識別和載入這些資料檔案。如需詳細資訊，請參閱 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)。  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## 視窗和對話方塊  
 使用者是透過視窗與 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 獨立應用程式進行互動的。  視窗的用途是裝載應用程式內容並公開應用程式功能，讓使用者與內容互動。  在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，視窗會由 <xref:System.Windows.Window> 類別封裝，而該類別支援：  
  
-   建立和顯示視窗。  
  
-   建立主控視窗 \(Owner Window\)\/附屬視窗 \(Owned Window\) 的關聯性。  
  
-   設定視窗外觀 \(例如大小、位置、圖示、標題列文字、框線\)。  
  
-   追蹤視窗的存留期並與其互動。  
  
 如需詳細資訊，請參閱 [WPF 視窗概觀](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)。  
  
 <xref:System.Windows.Window> 支援建立一種稱為對話方塊的特殊視窗類型。  您可以建立強制回應 \(Modal\) 和非強制回應 \(Modeless\) 類型的對話方塊。  
  
 為了方便、能重複使用以及跨應用程式提供一致的使用者經驗，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 公開三種常用的 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] 對話方塊，包括 <xref:Microsoft.Win32.OpenFileDialog>、<xref:Microsoft.Win32.SaveFileDialog> 與 <xref:System.Windows.Controls.PrintDialog>。  
  
 訊息方塊是特殊類型的對話方塊，可將重要的文字資訊顯示給使用者，以及詢問簡單的「是」\/「否」\/「確定」\/「取消」問題。  您可以使用 <xref:System.Windows.MessageBox> 類別建立和顯示訊息方塊。  
  
 如需詳細資訊，請參閱[對話方塊概觀](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)。  
  
<a name="Navigation"></a>   
## 巡覽  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支援使用頁面 \(<xref:System.Windows.Controls.Page>\) 和超連結 \(<xref:System.Windows.Documents.Hyperlink>\) 的 Web 樣式巡覽。  巡覽可藉由多種方式實作，包括下列項目：  
  
-   裝載於 Web 瀏覽器中的獨立頁面。  
  
-   編譯為可裝載於 Web 瀏覽器的 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 的頁面。  
  
-   編譯至獨立應用程式並由巡覽視窗 \(<xref:System.Windows.Navigation.NavigationWindow>\) 裝載的頁面。  
  
-   由框架 \(<xref:System.Windows.Controls.Frame>\) 裝載的頁面，可以裝載於獨立頁面，或編譯為 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 或獨立應用程式的頁面。  
  
 為了加速巡覽，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 實作了下列項目：  
  
-   <xref:System.Windows.Navigation.NavigationService>，這是處理巡覽要求的共用巡覽引擎，供 <xref:System.Windows.Controls.Frame>、<xref:System.Windows.Navigation.NavigationWindow> 和 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 用來支援應用程式內的巡覽。  
  
-   起始巡覽的巡覽方法。  
  
-   追蹤巡覽存留期並與其互動的巡覽事件。  
  
-   使用日誌記住向後和向前巡覽，日誌也可以供人檢查和操作。  
  
 如需詳細資訊，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 也支援一種稱為結構化巡覽的特殊巡覽類型。  結構化巡覽可用來呼叫一個或多個頁面，這些頁面會以與呼叫函式一致的結構化且可預期方式傳回資料。  這項功能需要仰賴 <xref:System.Windows.Navigation.PageFunction%601> 類別，這點在[結構化巡覽概觀](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)中有進一步的說明。  <xref:System.Windows.Navigation.PageFunction%601> 也可用來簡化巡覽拓撲的建立，巡覽拓撲說明於[巡覽拓撲概觀](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)。  
  
<a name="Hosting"></a>   
## 裝載  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] 可以裝載於 [!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] 或 Firefox。  每種裝載模型都有各自的考量與限制，[裝載](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)主題中會說明這些事項。  
  
<a name="Build_and_Deploy"></a>   
## 建置和部署  
 雖然從命令提示字元使用命令列編譯器也可以建置簡單的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式，不過將 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 與 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 整合，將可提供更多的支援來簡化開發和建置程序。  如需詳細資訊，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。  
  
 根據您建立的應用程式類型而定，有一個或多個部署選項可供選擇。  如需詳細資訊，請參閱 [部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)。  
  
<a name="related_topics"></a>   
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)|提供 <xref:System.Windows.Application> 類別的概觀，包括管理應用程式留存期、視窗、應用程式資源和巡覽。|  
|[WPF 中的視窗](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|提供有關管理您應用程式中視窗的詳細資訊，包括如何使用 <xref:System.Windows.Window> 類別和對話方塊。|  
|[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)|提供有關管理您應用程式中頁面間巡覽的概觀。|  
|[裝載](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|提供 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 的概觀。|  
|[建置和部署](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|描述如何建置及部署 WPF 應用程式。|  
|[Visual Studio 2015 中的 WPF 簡介](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|描述 WPF 的主要功能。|  
|[逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|逐步解說如何使用頁面巡覽、配置、控制項、影像、樣式和繫結來建立 WPF 應用程式。|