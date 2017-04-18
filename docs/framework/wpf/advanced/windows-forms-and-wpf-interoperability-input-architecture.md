---
title: "Windows Form 和 WPF 互通性輸入架構 | Microsoft Docs"
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
  - "ElementHost 鍵盤和訊息"
  - "輸入架構 [WPF 互通性]"
  - "互通性 [WPF], Windows Form"
  - "鍵盤互通 [WPF]"
  - "訊息 [WPF]"
  - "非強制回應對話方塊 [WPF]"
  - "非強制回應表單"
  - "Windows Form [WPF], 互通性"
  - "Windows Form, WPF 互通"
  - "WindowsFormsHost 鍵盤和訊息"
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Windows Form 和 WPF 互通性輸入架構
若要讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 與 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 兩者之間互通，這兩項技術都必須具有適當的鍵盤輸入處理。  本主題說明這些技術如何實作鍵盤與訊息處理，以在混合應用程式中順利達到互通性。  
  
 本主題包含下列子章節：  
  
-   非強制回應表單與對話方塊  
  
-   WindowsFormsHost 鍵盤與訊息處理  
  
-   ElementHost 鍵盤與訊息處理  
  
## 非強制回應表單與對話方塊  
 呼叫 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 項目的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> 方法，以從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式開啟非強制回應 \(Modeless\) 表單或對話方塊。  
  
 呼叫 <xref:System.Windows.Forms.Integration.ElementHost> 控制項的 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> 方法，以在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 架構應用程式中開啟非強制回應 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面。  
  
## WindowsFormsHost 鍵盤與訊息處理  
 當由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構應用程式裝載時，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 鍵盤與訊息處理包含下列步驟：  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別會從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈取得訊息，而該訊息迴圈是由 <xref:System.Windows.Interop.ComponentDispatcher> 類別所實作。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別會建立 Surrogate [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈，以確定已執行一般的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 鍵盤處理。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別會實作 <xref:System.Windows.Interop.IKeyboardInputSink> 介面，以便與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 協調焦點 \(Focus\) 的管理。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項自行註冊，並啟動其訊息迴圈。  
  
 下列章節將進一步說明程序中的這些部分。  
  
### 從 WPF 訊息迴圈取得訊息  
 <xref:System.Windows.Interop.ComponentDispatcher> 類別會實作 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的訊息迴圈管理員。  <xref:System.Windows.Interop.ComponentDispatcher> 類別會提供攔截 \(Hook\)，讓外部用戶端可在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 處理訊息前先篩選訊息。  
  
 互通性實作 \(Implementation\) 會處理 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> 事件，讓 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項可在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之前處理訊息。  
  
### Surrogate Windows Form 訊息迴圈  
 根據預設，<xref:System.Windows.Forms.Application?displayProperty=fullName> 類別包含 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式的主要訊息迴圈。  在互通期間，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 訊息迴圈不會處理訊息。  因此，必須重現這個邏輯。  <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> 事件的處理常式會執行下列步驟：  
  
1.  使用 <xref:System.Windows.Forms.IMessageFilter> 介面篩選訊息。  
  
2.  呼叫 <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=fullName> 方法。  
  
3.  視需要轉譯和分派訊息。  
  
4.  將訊息傳送至裝載控制項 \(若無其他控制項可以處理訊息\)。  
  
### IKeyboardInputSink 實作  
 Surrogate 訊息迴圈會負責處理鍵盤管理。  因此，<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=fullName> 方法是唯一需要在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別中實作的 <xref:System.Windows.Interop.IKeyboardInputSink> 成員。  
  
 根據預設，<xref:System.Windows.Interop.HwndHost> 類別會針對其 <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> 實作傳回 `false`。  如此可防止透過 Tab 鍵從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項移至 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=fullName> 方法的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 實作會執行下列步驟：  
  
1.  尋找 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項所包含且可接收焦點的第一個或最後一個 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 控制項。  控制項的選擇是根據周遊資訊而定。  
  
2.  將焦點設到控制項上，並傳回 `true`。  
  
3.  如果沒有控制項可接收焦點，則傳回 `false`。  
  
### WindowsFormsHost 註冊  
 當建立 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的視窗控制代碼 \(Window Handle\) 時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會呼叫可以將自己註冊到訊息迴圈中的內部靜態方法。  
  
 在註冊期間，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會檢查訊息迴圈。  如果訊息迴圈尚未啟動，則會建立 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> 事件處理常式。  附加 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=fullName> 事件處理常式後，訊息迴圈會被視為執行中。  
  
 當視窗控制代碼被終結時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項即會將自己從註冊中移除。  
  
## ElementHost 鍵盤與訊息處理  
 當由 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 應用程式裝載時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 鍵盤與訊息處理包含下列項目：  
  
-   <xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.IKeyboardInputSink> 與 <xref:System.Windows.Interop.IKeyboardInputSite> 介面實作。  
  
-   Tab 鍵切換與方向鍵。  
  
-   命令鍵與對話方塊按鍵。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 快速鍵處理。  
  
 下列章節將進一步說明這些部分。  
  
### 介面實作  
 在 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 中，鍵盤訊息會傳送至具有焦點之控制項的視窗控制代碼。  在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中，這些訊息會傳送至裝載的項目。  為了完成這項作業，<xref:System.Windows.Forms.Integration.ElementHost> 控制項會提供 <xref:System.Windows.Interop.HwndSource> 執行個體。  如果 <xref:System.Windows.Forms.Integration.ElementHost> 控制項具有焦點，<xref:System.Windows.Interop.HwndSource> 執行個體即會傳送大部分的鍵盤輸入，使其可由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> 類別處理。  
  
 <xref:System.Windows.Interop.HwndSource> 類別會實作 <xref:System.Windows.Interop.IKeyboardInputSink> 與 <xref:System.Windows.Interop.IKeyboardInputSite> 介面。  
  
 若要與鍵盤互通，必須實作 <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> 方法，以處理可以將焦點移出裝載的項目的 TAB 鍵與方向鍵。  
  
### Tab 切換與方向鍵  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 選取邏輯會對應至 <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> 與 <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> 方法，以實作 TAB 鍵與方向鍵巡覽。  覆寫 <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> 方法即可達成此對應。  
  
### 命令鍵與對話方塊按鍵  
 為了提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 先處理命令鍵與對話方塊按鍵的機會，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 命令處理已連接至 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> 方法。  覆寫 <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=fullName> 方法即可連接至這兩項技術。  
  
 透過 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> 方法，受裝的載項目可以處理任何按鍵訊息，如 WM\_KEYDOWN、WM\_KEYUP、WM\_SYSKEYDOWN 或 WM\_SYSKEYUP，包括 TAB、ENTER、ESC 與方向鍵等命令鍵。  如果沒有處理按鍵訊息，則會將其傳送至 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 祖系階層以進行處理。  
  
### 快速鍵處理  
 若要正確處理快速鍵，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 快速鍵處理必須已連接至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> 類別。  此外，所有 WM\_CHAR 訊息也都必須正確傳送至裝載的項目。  
  
 由於 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> 方法的 <xref:System.Windows.Interop.HwndSource> 預設實作會傳回 `false`，因此 WM\_CHAR 訊息會以下列邏輯進行處理：  
  
-   覆寫 <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=fullName> 方法，以確保所有 WM\_CHAR 訊息都會轉寄至裝載的項目。  
  
-   如果按下 ALT 鍵，則訊息為 WM\_SYSCHAR。  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 不會透過 <xref:System.Windows.Forms.Control.IsInputChar%2A> 方法前置處理這個訊息。  因此，<xref:System.Windows.Forms.Control.ProcessMnemonic%2A> 方法會被覆寫，以向 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> 查詢已註冊的快速鍵。  如果找到已註冊的快速鍵，則 <xref:System.Windows.Input.AccessKeyManager> 會加以處理。  
  
-   如果未按 ALT 鍵，則 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> 類別會處理未處理的輸入。  如果輸入的是快速鍵，則 <xref:System.Windows.Input.AccessKeyManager> 會加以處理。  如果是未處理的 WM\_CHAR 訊息，則會處理 <xref:System.Windows.Input.InputManager.PostProcessInput> 事件。  
  
 當使用者按 ALT 鍵時，整個表單上都會顯示快速鍵視覺提示。  為了支援這項行為，無論哪個控制項具有焦點，作用中表單上所有的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會接收 WM\_SYSKEYDOWN 訊息。  
  
 訊息只會傳送至作用中表單內的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
## 請參閱  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>   
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>   
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [逐步解說：在 WPF 中裝載 Windows Form 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)   
 [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)   
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)