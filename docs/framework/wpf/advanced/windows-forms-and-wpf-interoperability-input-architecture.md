---
title: Windows Forms 和 WPF interop 輸入架構
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
ms.openlocfilehash: 1c7027947d24c847ee298022344e02ce0bbff764
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794085"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Form 和 WPF 互通性輸入架構
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 Windows Forms 之間的互通性需要這兩種技術都具有適當的鍵盤輸入處理。 本主題描述這些技術如何實行鍵盤和訊息處理，以在混合式應用程式中啟用順暢的互通性。  
  
 本主題包含下列各小節：  
  
- 非模式表單和對話方塊  
  
- WindowsFormsHost 鍵盤和訊息處理  
  
- ElementHost 鍵盤和訊息處理  
  
## <a name="modeless-forms-and-dialog-boxes"></a>非模式表單和對話方塊  
 呼叫 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 元素上的 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> 方法，從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式開啟非模式表單或對話方塊。  
  
 在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項上呼叫 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> 方法，以在以 Windows Forms 為基礎的應用程式中開啟非強制回應的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 頁面。  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost 鍵盤和訊息處理  
 由以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式裝載時，Windows Forms 鍵盤和訊息處理是由下列各項所組成：  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別會從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈取得訊息，這是由 <xref:System.Windows.Interop.ComponentDispatcher> 類別所執行。  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別會建立代理 Windows Forms 訊息迴圈，以確保發生一般的 Windows Forms 鍵盤處理。  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別會執行 <xref:System.Windows.Interop.IKeyboardInputSink> 介面，以協調 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的焦點管理。  
  
- <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會自行註冊並啟動其訊息迴圈。  
  
 下列各節會更詳細地說明這些部分的程式。  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>從 WPF 訊息迴圈取得訊息  
 <xref:System.Windows.Interop.ComponentDispatcher> 類別會針對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]執行訊息迴圈管理員。 <xref:System.Windows.Interop.ComponentDispatcher> 類別會提供攔截，讓外部用戶端在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 處理訊息之前，先進行篩選。  
  
 互通執行會處理 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> 事件，這可讓 Windows Forms 控制項在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項之前處理訊息。  
  
### <a name="surrogate-windows-forms-message-loop"></a>代理 Windows Forms 訊息迴圈  
 根據預設，<xref:System.Windows.Forms.Application?displayProperty=nameWithType> 類別包含 Windows Forms 應用程式的主要訊息迴圈。 在交互操作期間，Windows Forms 訊息迴圈不會處理訊息。 因此，必須重現此邏輯。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> 事件的處理常式會執行下列步驟：  
  
1. 使用 <xref:System.Windows.Forms.IMessageFilter> 介面來篩選訊息。  
  
2. 呼叫 <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> 方法。  
  
3. 轉譯並分派訊息（如有需要）。  
  
4. 如果沒有其他控制項處理訊息，則將訊息傳遞至裝載控制項。  
  
### <a name="ikeyboardinputsink-implementation"></a>System.windows.interop.ikeyboardinputsink> 執行  
 代理訊息迴圈會處理鍵盤管理。 因此，<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> 方法是唯一需要在 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 類別中執行的 <xref:System.Windows.Interop.IKeyboardInputSink> 成員。  
  
 根據預設，<xref:System.Windows.Interop.HwndHost> 類別會傳回其 <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> 執行的 `false`。 這可防止從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項到 Windows Forms 控制項的 tab 鍵。  
  
 <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> 方法的 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 實作為執行下列步驟：  
  
1. 尋找 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項所包含的第一個或最後一個 Windows Forms 控制項，而且可以接收焦點。 控制項選擇取決於「遍歷」資訊。  
  
2. 將焦點設定為控制項，並傳回 `true`。  
  
3. 如果沒有控制項可以獲得焦點，則會傳回 `false`。  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost 註冊  
 建立 <xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項的視窗控制碼時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會呼叫內部靜態方法，以註冊訊息迴圈的目前狀態。  
  
 在註冊期間，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會檢查訊息迴圈。 如果尚未啟動訊息迴圈，就會建立 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> 事件處理常式。 附加 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> 事件處理常式時，會將訊息迴圈視為正在執行。  
  
 當視窗控制碼損毀時，<xref:System.Windows.Forms.Integration.WindowsFormsHost> 控制項會從註冊中移除本身。  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost 鍵盤和訊息處理  
 由 Windows Forms 應用程式託管時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 鍵盤和訊息處理包含下列各項：  
  
- <xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.IKeyboardInputSink>和 <xref:System.Windows.Interop.IKeyboardInputSite> 介面實現。  
  
- Tab 鍵和方向鍵。  
  
- 命令鍵和對話方塊鍵。  
  
- Windows Forms 加速器處理。  
  
 下列各節會更詳細地說明這些部分。  
  
### <a name="interface-implementations"></a>介面實現  
 在 Windows Forms 中，鍵盤訊息會路由至具有焦點之控制項的視窗控制碼。 在 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中，這些訊息會路由傳送至裝載的元素。 為了達成此目的，<xref:System.Windows.Forms.Integration.ElementHost> 控制項會提供 <xref:System.Windows.Interop.HwndSource> 實例。 如果 <xref:System.Windows.Forms.Integration.ElementHost> 控制項有焦點，<xref:System.Windows.Interop.HwndSource> 實例會路由大部分的鍵盤輸入，讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> 類別可以處理它。  
  
 <xref:System.Windows.Interop.HwndSource> 類別會執行 <xref:System.Windows.Interop.IKeyboardInputSink> 和 <xref:System.Windows.Interop.IKeyboardInputSite> 介面。  
  
 鍵盤互通依賴執行 <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> 方法來處理 TAB 鍵和方向鍵輸入，將焦點移出裝載的元素。  
  
### <a name="tabbing-and-arrow-keys"></a>Tab 鍵和箭號按鍵  
 Windows Forms 選取邏輯會對應至 <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>，並 <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> 方法來執行 TAB 鍵和箭號按鍵導覽。 覆寫 <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> 方法會完成此對應。  
  
### <a name="command-keys-and-dialog-box-keys"></a>命令鍵和對話方塊索引鍵  
 為了讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 第一個處理命令索引鍵和對話方塊索引鍵的機會，Windows Forms 命令前置處理已連接到 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> 方法。 覆寫 <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> 方法會連接這兩個技術。  
  
 使用 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> 方法，裝載的專案可以處理任何按鍵訊息，例如 WM_KEYDOWN、WM_KEYUP、WM_SYSKEYDOWN 或 WM_SYSKEYUP，包括命令索引鍵，例如 TAB、ENTER、ESC 和方向鍵。 如果未處理金鑰訊息，則會傳送 Windows Forms 上階階層以進行處理。  
  
### <a name="accelerator-processing"></a>加速器處理  
 若要正確處理加速器，Windows Forms 加速器處理必須連接至 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> 類別。 此外，所有 WM_CHAR 訊息都必須正確地路由至裝載的元素。  
  
 因為 <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> 方法的預設 <xref:System.Windows.Interop.HwndSource> 實值會傳回 `false`，所以會使用下列邏輯來處理 WM_CHAR 訊息：  
  
- 會覆寫 <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> 方法，以確保所有 WM_CHAR 訊息都會轉送至裝載的元素。  
  
- 如果按下 ALT 鍵，則會 WM_SYSCHAR 訊息。 Windows Forms 不會透過 <xref:System.Windows.Forms.Control.IsInputChar%2A> 方法來前置處理此訊息。 因此，會覆寫 <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> 方法，以查詢已註冊加速器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager>。 如果找到已註冊的加速器，<xref:System.Windows.Input.AccessKeyManager> 會加以處理。  
  
- 如果未按下 ALT 鍵，則 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> 類別會處理未處理的輸入。 如果輸入是快速鍵，<xref:System.Windows.Input.AccessKeyManager> 會處理它。 <xref:System.Windows.Input.InputManager.PostProcessInput> 事件會針對未處理的 WM_CHAR 訊息進行處理。  
  
 當使用者按下 ALT 鍵時，會在整個表單上顯示快速鍵視覺提示。 為了支援此行為，使用中表單上的所有 <xref:System.Windows.Forms.Integration.ElementHost> 控制項都會收到 WM_SYSKEYDOWN 訊息，不論哪個控制項有焦點。  
  
 訊息只會傳送至使用中表單中的 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：在 Windows Form 中裝載 WPF 複合控制項](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
