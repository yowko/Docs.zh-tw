---
title: "WPF XAML 瀏覽器應用程式概觀 | Microsoft Docs"
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
  - "瀏覽器裝載應用程式 [WPF]"
  - "WPF XAML 瀏覽器應用程式 (XBAP)"
  - "XAML 瀏覽器應用程式 (XBAP)"
  - "XBAP, XAML 瀏覽器應用程式"
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
caps.latest.revision: 47
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 47
---
# WPF XAML 瀏覽器應用程式概觀
<a name="introduction"></a> [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 結合了 Web 應用程式和豐富型用戶端 \(Rich Client\) 應用程式兩者的功能。  如同 Web 應用程式，XBAP 可以部署到網頁伺服器並從 Internet Explorer 或 Firefox 啟動。  而如同豐富型用戶端應用程式一樣，XBAP 可以利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的功能。  開發 XBAP 也和豐富型用戶端開發非常類似。  本主題提供 XBAP 開發的高階簡介，並說明 XBAP 開發與標準豐富型用戶端開發的不同之處。  
  
 此主題包括下列章節：  
  
-   [建立新的 XAML 瀏覽器應用程式 \(XBAP\)](#creating_a_new_xaml_browser_application_xbap)  
  
-   [部署 XBAP](#deploying_a_xbap)  
  
-   [與裝載網頁通訊](#communicating_with_the_host_web_page)  
  
-   [XBAP 安全性考量](#xbap_security_considerations)  
  
-   [XBAP 開始時間效能考量](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## 建立新的 XAML 瀏覽器應用程式 \(XBAP\)  
 建立新 XBAP 專案最簡單的方式是使用 [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]。  建立新專案時，從範本清單選取 \[**WPF 瀏覽器應用程式**\]。  如需詳細資訊，請參閱 [HOW TO：建立新的 WPF 瀏覽器應用程式專案](http://msdn.microsoft.com/zh-tw/72ef4d90-e163-42a1-8df0-ea7ccfd1901f)。  
  
 執行 XBAP 時，它會在瀏覽器視窗而非獨立視窗中開啟。  當您從 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 對 XBAP 進行偵錯時，應用程式會以網際網路區域權限執行，因此會在超出這些權限時，擲回安全性例外狀況。  如需詳細資訊，請參閱 [安全性](../../../../docs/framework/wpf/security-wpf.md)和 [WPF 部分信任安全性](../../../../docs/framework/wpf/wpf-partial-trust-security.md)。  
  
> [!NOTE]
>  如果您不要使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 進行開發，或是想要進一步了解專案檔，請參閱[建置 WPF 應用程式](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)。  
  
<a name="deploying_a_xbap"></a>   
## 部署 XBAP  
 當您建置 XBAP 時，輸出會包含下列三個檔案：  
  
|檔案|描述|  
|--------|--------|  
|可執行檔 \(.exe\)|這個檔案包含編譯過的程式碼，且其副檔名為 .exe。|  
|應用程式資訊清單 \(.manifest\)|這份資訊清單包含與應用程式關聯的中繼資料 \(Metadata\)，且其副檔名為 .manifest。|  
|部署資訊清單 \(.xbap\)|這個檔案包含 [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 用來部署應用程式的資訊，且其副檔名為 .xbap。|  
  
 您會將 XBAP 部署至網頁伺服器，例如 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] \(含\) 以後版本。  您不需要在網頁伺服器上安裝 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)]，但是必須註冊 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] 類型和副檔名。  如需詳細資訊，請參閱 [設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md)。  
  
 若要準備 XBAP 以進行部署，請將 .exe 和相關資訊清單複製到網頁伺服器。  建立包含超連結的 HTML 網頁以開啟部署資訊清單，這個檔案的副檔名是 .xbap。  當使用者按一下 .xbap 檔案的連結時，[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 會自動處理下載及啟動應用程式的機制。  下列範例程式碼顯示包含指向 XBAP 之超連結的 HTML 網頁。  
  
```  
<html>   
  <head></head>  
  <body>   
    <a href="XbapEx.xbap">Click this link to launch the application</a>  
  </body>   
</html>  
  
```  
  
 您也可以在網頁的框架中裝載 XBAP。  建立擁有一個或多個框架的網頁。  將框架的來源屬性設定為部署資訊清單檔案。  如果您要在裝載網頁和 XBAP 之間使用內建的機制進行通訊，則必須在框架中裝載應用程式。  下列範例程式碼顯示擁有兩個框架的 HTML 網頁，其中第二個框架的來源設為 XBAP。  
  
```  
<html>   
  <head>A page with frames.</head>  
    <frameset cols="50%,50%">   
      <frame src="introduction.htm" >   
      <frame src="XbapEx.xbap" >   
  </frameset>   
</html>  
```  
  
### 清除快取 XBAP  
 在某些情況下，重新建置並啟動 XBAP 之後，可能會發現開啟的是舊版 XBAP。  例如，當 XBAP 組件版本號碼是靜態的，而您從命令列啟動 XBAP 時，此行為就會發生。  在這種情況下，由於快取版本 \(之前啟動的版本\) 和新版本的版本號碼相同，因此不會下載新版本的 XBAP，  而是下載快取版本。  
  
 在這些情況下，您可以在命令提示字元中使用 **Mage** 命令 \(隨 Visual Studio 或 [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] 一併安裝\) 移除快取的版本。  下列命令會清除應用程式快取。  
  
 `Mage.exe -cc`  
  
 這個命令會保證啟動的是最新版的 XBAP。  當您在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中偵錯應用程式時，應該會啟動您最新版的 XBAP。一般而言，您應該隨著每個組建而更新部署版本號碼。  如需 Mage 的詳細資訊，請參閱 [Mage.exe \(資訊清單產生和編輯工具\)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)。  
  
<a name="communicating_with_the_host_web_page"></a>   
## 與裝載網頁通訊  
 在 HTML 框架中裝載應用程式時，可以與包含 XBAP 的網頁進行通訊。  您可以透過擷取 <xref:System.Windows.Interop.BrowserInteropHelper> 的 <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> 屬性達成此目的。  這個屬性會傳回代表 HTML 視窗的指令碼物件。  接著您可以使用一般點語法 \(Dot Syntax\) 存取 [Window 物件](http://go.microsoft.com/fwlink/?LinkId=160274) \(英文\) 上的屬性、方法和事件。  您也可以存取指令碼方法和全域變數。  下列範例顯示如何擷取指令碼物件和關閉瀏覽器。  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### 對使用 HostScript 的 XBAP 進行偵錯  
 如果您的 XBAP 使用 <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> 物件與 HTML 視窗進行通訊，您必須指定兩項設定才能在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中執行應用程式並且進行偵錯。  應用程式必須能夠存取其來源網站，而且您必須以包含 XBAP 的 HTML 網頁啟動應用程式。  下列步驟說明如何檢查這兩項設定：  
  
1.  在 Visual Studio 中開啟專案屬性。  
  
2.  在 \[**安全性**\] 索引標籤上按一下 \[**進階**\]。  
  
     \[進階安全性設定\] 對話方塊隨即出現。  
  
3.  確定已核取 \[**允許應用程式存取它的來源網站**\] 核取方塊，然後按一下 \[**確定**\]。  
  
4.  在 \[**偵錯**\] 索引標籤上選取 \[**瀏覽器起始 URL**\] 選項，並且為包含 XBAP 的 HTML 網頁指定 URL。  
  
5.  在 Internet Explorer 中按一下 \[**工具**\] 按鈕，然後選取 \[**網際網路選項**\]。  
  
     \[網際網路選項\] 對話方塊隨即出現。  
  
6.  按一下 \[**進階**\] 索引標籤。  
  
7.  在 \[**設定**\] 清單的 \[**安全性**\] 底下，核取 \[**允許主動式內容在我電腦上的檔案中執行**\] 核取方塊。  
  
8.  按一下 \[**確定**\]。  
  
     變更將在您重新啟動 Internet Explorer 之後生效。  
  
> [!CAUTION]
>  在 Internet Explorer 啟用主動式內容可能讓電腦暴露於風險中。  如需詳細資訊，請參閱 [Internet Explorer 中的安全性與隱私權功能](http://go.microsoft.com/fwlink/?LinkId=179286)。  如果您不想要變更 Internet Explorer 安全性設定，可以從伺服器啟動 HTML 網頁，並將 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 偵錯工具附加至處理序。  
  
<a name="xbap_security_considerations"></a>   
## XBAP 安全性考量  
 XBAP 通常會在受限於網際網路區域權限集合的部分信任安全性沙箱中執行。  因此，您的實作必須支援網際網路區域所支援的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目子集，或者您必須提高應用程式的權限。  如需詳細資訊，請參閱 [安全性](../../../../docs/framework/wpf/security-wpf.md)。  
  
 當您在應用程式中使用 <xref:System.Windows.Controls.WebBrowser> 控制項時，WPF 會在內部執行個體化原生 WebBrowser ActiveX 控制項。  如果您的應用程式是在 Internet Explorer 中執行的部分信任 XBAP，則 ActiveX 控制項會在 Internet Explorer 處理序專屬的執行緒中執行。  因此適用下列限制：  
  
-   <xref:System.Windows.Controls.WebBrowser> 控制項應該提供與裝載瀏覽器相似的行為，包括安全性限制。  其中部分安全性限制可以透過 Internet Explorer 安全性設定控制。  如需詳細資訊，請參閱 [安全性](../../../../docs/framework/wpf/security-wpf.md)。  
  
-   當 XBAP 跨網域載入 HTML 網頁中時，會擲回例外狀況。  
  
-   輸入是與 WPF <xref:System.Windows.Controls.WebBrowser> 不同的執行緒，因此鍵盤輸入無法攔截且 IME 狀態不會共用。  
  
-   巡覽的時機和順序可能因為另一個執行緒上執行的 ActiveX 控制項而有所不同。  例如，只要啟動另一個巡覽要求，就會取消巡覽至頁面。  
  
-   自訂 ActiveX 控制項的通訊可能會出現問題，因為 WPF 應用程式是在不同的執行緒中執行。  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook> 不會引發，因為 <xref:System.Windows.Interop.HwndHost> 無法將另一個執行緒或處理序中執行的視窗設為子類別。  
  
### 建立完全信任的 XBAP  
 如果您的 XBAP 要求完全信任，您可以變更專案來啟用這項權限。  下列步驟將描述如何啟用完全信任：  
  
1.  在 Visual Studio 中開啟專案屬性。  
  
2.  在 \[**安全性**\] 索引標籤上選取 \[**這是完全信任的應用程式**\] 選項。  
  
 這個設定會進行下列變更：  
  
-   在專案檔中，`<TargetZone>` 項目值會變更為 `Custom`。  
  
-   在應用程式資訊清單 \(app.manifest\) 中，`Unrestricted="true"` 屬性會加入至 `PermissionSet` 項目。  
  
    ```  
    <PermissionSet class="System.Security.PermissionSet"   
        version="1"   
        ID="Custom"   
        SameSite="site"   
        Unrestricted="true"   
    />  
    ```  
  
### 部署完全信任的 XBAP  
 當您部署未遵循 ClickOnce 信任部署模型的完全信任 XBAP 時，使用者執行應用程式時的行為將取決於安全性區域。  在某些情況下，使用者會在嘗試安裝此程式碼時收到警告。  使用者可以選擇繼續或取消安裝。  下表說明應用程式在每個安全性區域的行為，以及您要怎麼做才能讓應用程式獲得完全信任。  
  
|安全性區域|行為|取得完全信任|  
|-----------|--------|------------|  
|本機電腦|自動完全信任|不需任何動作。|  
|內部網路和限制的網站|提示需有完全信任|使用憑證簽署 XBAP，以便使用者在提示中看見來源。|  
|網際網路|失敗並顯示「未授與信任」|使用憑證簽署 XBAP。|  
  
> [!NOTE]
>  上表中說明的行為適用於未遵循 ClickOnce 信任部署模型的完全信任 XBAP。  
  
 建議您使用 ClickOnce 信任部署模型部署完全信任的 XBAP。  這個模型可讓您的 XBAP 自動獲得完全信任 \(無論安全性區域為何\)，如此就不會提示使用者。  這個模型會要求您使用來自信任發行者的憑證簽署應用程式。  如需詳細資訊，請參閱[受信任的應用程式部署概觀](../Topic/Trusted%20Application%20Deployment%20Overview.md)和[程式碼簽署簡介](http://go.microsoft.com/fwlink/?LinkId=166327) \(英文\)。  
  
<a name="xbap_start_time_performance_considerations"></a>   
## XBAP 開始時間效能考量  
 XBAP 效能的一個重要面向在於其開始時間。  如果 XBAP 是第一個要載入的 WPF 應用程式，則「*冷啟動*」\(Cold Start\) 時間可能為 10 秒鐘或更久。  這是因為進度頁是由 WPF 呈現，且必須 CLR 和 WPF 都已冷啟動才能顯示應用程式。  
  
 從 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 開始，XBAP 冷啟動時間已經藉由在部署循環早期顯示 Unmanaged 進度頁而降低。此進度頁幾乎在應用程式啟動後就會立即顯示，因為它是以原生裝載程式碼顯示並以 HTML 呈現。  
  
 此外，[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 下載序列的並行也已改良，讓開始時間的效能提升百分之十。  [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 下載並驗證資訊清單之後，應用程式下載隨即開始，進度列也會開始更新。  
  
## 請參閱  
 [設定 Visual Studio 來偵錯 XAML 瀏覽器應用程式以呼叫 Web 服務](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)   
 [部署 WPF 應用程式](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)