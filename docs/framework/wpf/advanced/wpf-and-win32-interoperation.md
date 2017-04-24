---
title: "WPF 和 Win32 互通 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "將 WPF 內容裝載在 Win32 視窗中"
  - "HWND Interop [WPF]"
  - "互通性 [WPF], Win32"
  - "Win32 程式碼, WPF 互通"
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# WPF 和 Win32 互通
此主題會提供如何讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼交互操作的概觀。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用來建立應用程式的豐富環境。  不過，如果已開發了大量的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 程式碼，更有效的方式是重複使用其中部分的程式碼。  
  
   
  
<a name="basics"></a>   
## WPF 和 Win32 互通性基本概念  
 有兩項基本的技巧可以達到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼之間的交互操作。  
  
-   在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容。  您可以運用此技巧，在標準 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗和應用程式的架構中使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的進階圖形功能。  
  
-   在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容中裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗。  您可以運用此技巧，在其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容中使用現有的自訂 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 控制項，並能跨界限傳遞資料。  
  
 本主題將介紹這兩種技巧的概念。  如需在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 中裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的程式碼導向示範，請參閱[逐步解說：在 Win32 中裝載 WPF 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)。  如需在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中裝載 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 的程式碼導向示範，請參閱[逐步解說：在 WPF 中裝載 Win32 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)。  
  
<a name="projects"></a>   
## WPF 互通性專案  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 屬於 Managed 程式碼，但大多數現有的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式都是以 Unmanaged [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] 撰寫的。  您無法從純粹的 Unmanaged 程式呼叫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  不過，您可以使用 [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] 編譯器的 `/clr` 選項，從而建立混合式 Managed\-Unmanaged 程式，完美地混合 Managed 和 Unmanaged [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 呼叫。  
  
 處理專案時會出現的問題是 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案無法編譯到 [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] 專案中。  這可以利用幾個專案層面技巧來解決。  
  
-   將包含所有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面的 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] DLL 建立為已編譯的組件，然後讓 [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] 可執行檔包含該 [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] 當做參考。  
  
-   為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容建立 [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] 可執行檔，然後讓它參考包含 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 內容的 [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]。  
  
-   使用 <xref:System.Windows.Markup.XamlReader.Load%2A> 在執行階段載入任何 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，而不編譯 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
-   完全不使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，而是將所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 撰寫在程式碼中，從 <xref:System.Windows.Application> 建立項目樹狀結構。  
  
 請使用最適合的方法。  
  
> [!NOTE]
>  如果您未使用 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 過，您可能會發現一些「新的」關鍵字 \(例如 `gcnew` 和 `nullptr` 在互通性程式碼範例。這些關鍵字取代了舊有的雙底線語法 \(`__gc`\) 並在 [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)]的 Managed 程式碼提供更自然的語法。  如需深入了解 [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] 的 Managed 功能，請參閱[執行階段平台的元件擴充功能](../Topic/Component%20Extensions%20for%20Runtime%20Platforms.md)和[認識 C\+\+\/CLI](http://go.microsoft.com/fwlink/?LinkId=98739) \(英文\)。  
  
<a name="hwnds"></a>   
## WPF 如何使用 Hwnd  
 為充分利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 "HWND Interop"，您需要了解 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 如何使用 HWND。  針對任何 HWND，您都不能將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 轉譯與 [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] 轉譯或 [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] \/ [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] 轉譯混合。  原因有幾個，  主要的原因是，若真要混合這些轉譯模型，必須建立互通性方案，然後針對每個選擇使用的轉譯模型，使用指定的互通性區段。  此外，轉譯行為會建立「空間」\(Airspace\) 限制，可供互通性方案達到。  「空間」概念將在 [技術領域概觀](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)中進一步說明。  
  
 畫面上的所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目最終都是由 HWND 所支援。  當您建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> 時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會建立最上層的 HWND，然後使用 <xref:System.Windows.Interop.HwndSource> 將 <xref:System.Windows.Window> 及其 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容放入 HWND。  應用程式中的其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容都共用該單一 HWND。  不過功能表、下拉式方塊下拉式清單和其他快顯視窗則為例外。  這些項目會自行建立最上層視窗，這就是為什麼 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能表可能會超過包含它的視窗 HWND 邊緣。  當您使用 <xref:System.Windows.Interop.HwndHost> 將 HWND 放入 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 時， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會指示 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 如何將新的子 HWND 放到相對於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND 的位置。  
  
 HWND 的另一個相關概念是每個 HWND 內部以及之間的透明度。  這也會在 [技術領域概觀](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)主題中說明。  
  
<a name="hosting_a_wpf_page"></a>   
## 將 WPF 內容裝載在 Microsoft Win32 視窗中  
 將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 裝載在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗上的關鍵在於 <xref:System.Windows.Interop.HwndSource> 類別。  這個類別會將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容包裝在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗中，讓您可以將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容當做子視窗加入 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中。  下列方法會將 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 合併在單一應用程式中。  
  
1.  將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容 \(內容根項目\) 實作成 Managed 類別。  一般來說，這個類別繼承自可包含多個子項目和\/或當做根項目使用的其中一個類別，例如 <xref:System.Windows.Controls.DockPanel> 或 <xref:System.Windows.Controls.Page>。  在接下來的步驟中，這個類別稱為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別，而類別的執行個體稱為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件。  
  
2.  使用 [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)] 實作 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式。  如果要啟動現有的 Unmanaged [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] 應用程式，一般可以變更專案設定來加入 `/clr` 編譯器旗標 \(本主題不提供支援 `/clr` 編譯所需項目的完整範圍說明\)，讓該應用程式呼叫 Managed 程式碼。  
  
3.  將執行緒模型設定為單一執行緒 Apartment \(STA\)。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 會使用這個執行緒模型。  
  
4.  在視窗程序中處理 WM\_CREATE 通知。  
  
5.  在處理常式 \(或處理常式呼叫的函式\) 中，執行下列動作：  
  
    1.  建立新的 <xref:System.Windows.Interop.HwndSource> 物件，並將父視窗 HWND 設為其 `parent` 參數。  
  
    2.  建立 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別的執行個體。  
  
    3.  將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件的參考指派給 <xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.RootVisual%2A> 屬性。  
  
    4.  <xref:System.Windows.Interop.HwndSource> 物件的 <xref:System.Windows.Interop.HwndSource.Handle%2A> 屬性包含視窗控制代碼 \(HWND\)。  若要取得 HWND 以用於應用程式的 Unmanaged 部分，請將 `Handle.ToPointer()` 轉換成 HWND。  
  
6.  實作 Managed 類別，該類別包含存放 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件參考的靜態欄位。  這個類別可讓您從 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 程式碼取得 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件的參考，但更重要的是，它可以防止 <xref:System.Windows.Interop.HwndSource> 的記憶體意外回收。  
  
7.  藉由將處理常式附加至一個或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件事件，從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容物件接收通知。  
  
8.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與內容物件通訊會使用儲存在靜態欄位中設定屬性、呼叫方法等.  
  
> [!NOTE]
>  如果您另外產生一個組件並參考它，使用內容類別的預設部分類別，您可以將部分或所有第一個步驟中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容類別定義在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。雖然您通常包含 <xref:System.Windows.Application> 物件做為編譯 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 一部分的組件，做為互通性的一部分，而不使用。 <xref:System.Windows.Application> ，該應用程式所參考之 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案所使用的一個或多個根類別並參考其部分類別。  其他步驟基本上就類似上述程序。  
>   
>  [逐步解說：在 Win32 中裝載 WPF 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)主題會以程式碼示範上述每一個步驟。  
  
<a name="hosting_an_hwnd"></a>   
## 將 Microsoft Win32 視窗裝載在 WPF 中  
 將 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 視窗裝載在其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容中的關鍵在於 <xref:System.Windows.Interop.HwndHost> 類別。  這個類別會將視窗包裝到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目中，該項目可加入至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目樹狀結構。  <xref:System.Windows.Interop.HwndHost> 同樣支援 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，可讓您執行一些工作，像是處理所裝載視窗的訊息。  基本的程序如下：  
  
1.  為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式建立項目樹狀結構 \(可以透過程式碼或標記\)。  在項目樹狀結構中尋找適當且可允許的點，以將 <xref:System.Windows.Interop.HwndHost> 實作當做子項目加入。  在接下來的步驟中，這個項目會稱為保留項目。  
  
2.  從 <xref:System.Windows.Interop.HwndHost> 衍生來建立存放 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 內容的物件。  
  
3.  在該裝載類別中，覆寫 <xref:System.Windows.Interop.HwndHost> 方法 <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>。  傳回所裝載視窗的 HWND。  您可以將實際控制項包裝成所傳回視窗的子視窗；將控制項包裝在裝載視窗中，可以很容易讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 內容接收來自控制項的通知。  這有助於解決在所裝載控制項範圍內處理訊息會發生的一些 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 問題。  
  
4.  覆寫 <xref:System.Windows.Interop.HwndHost> 方法 <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> 和 <xref:System.Windows.Interop.HwndHost.WndProc%2A>。  這是要清除和移除所裝載內容的參考，特別是如果您建立了 Unmanaged 物件的參考。  
  
5.  在程式碼後置 \(Code\-Behind\) 的檔案，建立裝載類別之控制項的執行個體，並將它設為保留項目的子項。  通常，您會使用如 <xref:System.Windows.FrameworkElement.Loaded> 的事件處理常式，或使用部分類別建構函式。  不過，您也可以透過執行階段行為加入互通性內容。  
  
6.  處理選取的視窗訊息，例如控制項通知。  處理的方法有兩種。  這兩種方法存取訊息資料流的方式完全相同，因此要使用哪一種就視程式設計的方便性而定。  
  
    -   在 <xref:System.Windows.Interop.HwndHost> 方法 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 的覆寫中，實作所有訊息 \(而不只是關機訊息\) 的訊息處理。  
  
    -   藉由處理 <xref:System.Windows.Interop.HwndHost.MessageHook> 事件，讓裝載 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目處理訊息。  只要有訊息傳送到所裝載視窗的主視窗程序，就會引發此事件。  
  
    -   您無法使用 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 處理來自跨處理序之視窗的訊息。  
  
7.  藉由使用平台叫用來呼叫 Unmanaged `SendMessage` 函式，以便與所裝載的視窗通訊。  
  
 完成上述步驟之後，會建立使用滑鼠輸入的應用程式。  您可以藉由實作 <xref:System.Windows.Interop.IKeyboardInputSink> 介面，在所裝載的視窗加入定位停駐支援。  
  
 [逐步解說：在 WPF 中裝載 Win32 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)主題會以程式碼示範上述每一個步驟。  
  
### WPF 中的 Hwnd  
 您可以將 <xref:System.Windows.Interop.HwndHost> 視為特殊的控制項   \(雖然在技術上，<xref:System.Windows.Interop.HwndHost> 是 <xref:System.Windows.FrameworkElement> 衍生的類別，不是 <xref:System.Windows.Controls.Control> 衍生的類別，但是基於交互操作目的，可以視為控制項\)。<xref:System.Windows.Interop.HwndHost> 會抽取裝載內容的基礎 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 性質，使得 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的剩餘部分將裝載內容視為另一種類似控制項的物件，而應該要負責轉譯並處理輸入。  <xref:System.Windows.Interop.HwndHost> 的行為通常就像是任何其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>，不過視基礎 HWND 可提供的支援所限，在輸出 \(繪圖和圖形\) 和輸入 \(滑鼠和鍵盤\) 方面有一些重大的差異。  
  
#### 輸出行為的顯著差異  
  
-   <xref:System.Windows.FrameworkElement> 是 <xref:System.Windows.Interop.HwndHost> 基底類別，包含一些會變更 UI 的屬性，  像是 <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=fullName> 屬性，會變更父項目中的項目版面配置。  不過，即使這些對應項實際存在，大多數的屬性都不會對應到可能的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 對應項。  這些屬性及其意義多半偏重於轉譯技術，對應起來並不實際。  因此，在 <xref:System.Windows.Interop.HwndHost> 上設定如 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 等屬性並沒有作用。  
  
-   <xref:System.Windows.Interop.HwndHost> 無法旋轉、縮放、傾斜或受轉換影響。  
  
-   <xref:System.Windows.Interop.HwndHost> 不支援 <xref:System.Windows.UIElement.Opacity%2A> 屬性 \(Alpha 混色\)。  如果 <xref:System.Windows.Interop.HwndHost> 中的內容執行包含 Alpha 資訊的 <xref:System.Drawing> 作業，其本身並未違規，但整個 <xref:System.Windows.Interop.HwndHost> 只支援 Opacity \= 1.0 \(100%\)。  
  
-   <xref:System.Windows.Interop.HwndHost> 會出現在相同最上層視窗中的其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目之上。  不過，<xref:System.Windows.Controls.ToolTip> 或 <xref:System.Windows.Controls.ContextMenu> 產生的功能表是一個獨立的最上層視窗，因此可與 <xref:System.Windows.Interop.HwndHost> 正常互動。  
  
-   <xref:System.Windows.Interop.HwndHost> 不一定會限制在其父 <xref:System.Windows.UIElement> 的裁剪區域內。  如果您嘗試將 <xref:System.Windows.Interop.HwndHost> 類別放入捲動區域或 <xref:System.Windows.Controls.Canvas>，可能會發生問題。  
  
#### 輸入行為的顯著差異  
  
-   一般來說，當輸入裝置的範圍在 <xref:System.Windows.Interop.HwndHost> 裝載的 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 區域內，輸入事件會直接傳送到 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]。  
  
-   當滑鼠停留在 <xref:System.Windows.Interop.HwndHost> 上時，應用程式不會收到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 滑鼠事件，而 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性 <xref:System.Windows.UIElement.IsMouseOver%2A> 的值會是 `false`。  
  
-   當 <xref:System.Windows.Interop.HwndHost> 具有鍵盤焦點時，應用程式不會收到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 鍵盤事件，而 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> 屬性值會是 `false`。  
  
-   當焦點在 <xref:System.Windows.Interop.HwndHost> 中且切換到 <xref:System.Windows.Interop.HwndHost> 內的另一個控制項時，應用程式不會收到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件 <xref:System.Windows.UIElement.GotFocus> 或 <xref:System.Windows.UIElement.LostFocus>。  
  
-   相關手寫筆屬性及事件與上述內容類似，當手寫筆停留在 <xref:System.Windows.Interop.HwndHost> 時，一樣不會回報資訊。  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## 定位停駐、助憶鍵和快速鍵  
 <xref:System.Windows.Interop.IKeyboardInputSink> 和 <xref:System.Windows.Interop.IKeyboardInputSite> 介面可讓您針對混合式 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 應用程式建立整合緊密的鍵盤操作：  
  
-   [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 元件之間的定位停駐  
  
-   無論焦點在 Win32 元件或在 WPF 元件，助憶鍵和快速鍵都有作用。  
  
 <xref:System.Windows.Interop.HwndHost> 和 <xref:System.Windows.Interop.HwndSource> 類別都提供 <xref:System.Windows.Interop.IKeyboardInputSink> 的實作，但在更進階的案例中，可能無法處理所有的輸入訊息。  請覆寫適當的方法，以獲得所需要的鍵盤行為。  
  
 這些介面只支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 區域之間的轉換操作。  在 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 區域中，定位停駐行為完全是由 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 實作的定位停駐邏輯 \(如果有的話\) 所控制。  
  
## 請參閱  
 <xref:System.Windows.Interop.HwndHost>   
 <xref:System.Windows.Interop.HwndSource>   
 <xref:System.Windows.Interop>   
 [逐步解說：在 WPF 中裝載 Win32 控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)   
 [逐步解說：在 Win32 中裝載 WPF 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)