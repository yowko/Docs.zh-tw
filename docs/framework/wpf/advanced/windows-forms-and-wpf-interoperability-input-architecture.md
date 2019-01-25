---
title: Windows Form 和 WPF 互通性輸入架構
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
ms.openlocfilehash: 9c19e09d1b72bbee48f101904647146a467cc8d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736230"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Form 和 WPF 互通性輸入架構
互通性之間[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]需要這兩種技術都有適當的鍵盤輸入的處理。 本主題會說明這些技術的實作方式鍵盤和訊息處理，以達到在混合式應用程式中的平順互通性。  
  
 本主題包含下列子章節：  
  
-   非強制回應表單和對話方塊  
  
-   WindowsFormsHost 鍵盤和訊息處理  
  
-   ElementHost 鍵盤和訊息處理  
  
## <a name="modeless-forms-and-dialog-boxes"></a>非強制回應表單和對話方塊  
 呼叫<xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>以開啟從非強制回應表單或對話方塊中的項目[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式。  
  
 呼叫<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法<xref:System.Windows.Forms.Integration.ElementHost>控制項，以開啟非強制回應[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-應用程式。  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost 鍵盤和訊息處理  
 當所裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式使用，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]鍵盤和訊息處理包含下列：  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>類別會取得來自[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]訊息迴圈，藉由<xref:System.Windows.Interop.ComponentDispatcher>類別。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>類別會建立代理[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]訊息迴圈，以確保該一般[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]鍵盤處理，就會發生。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>類別會實作<xref:System.Windows.Interop.IKeyboardInputSink>介面，以協調與焦點管理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項自行註冊，並啟動其訊息迴圈。  
  
 下列各節說明這些部分的更多詳細資料中的程序。  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>取得從 WPF 訊息迴圈的訊息  
 <xref:System.Windows.Interop.ComponentDispatcher>類別會實作的訊息迴圈管理員[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 <xref:System.Windows.Interop.ComponentDispatcher>類別提供攔截程序來啟用外部的用戶端，來篩選訊息之前[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]處理它們。  
  
 交互操作的實作會處理<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>事件，可讓[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項來處理訊息之前[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項。  
  
### <a name="surrogate-windows-forms-message-loop"></a>Surrogate Windows Form 訊息迴圈  
 根據預設，<xref:System.Windows.Forms.Application?displayProperty=nameWithType>類別包含的主要訊息迴圈[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]應用程式。 交互操作，期間[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]迴圈不會處理訊息的訊息。 因此，必須重新產生此邏輯。 處理常式<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>事件執行下列步驟：  
  
1.  篩選訊息使用<xref:System.Windows.Forms.IMessageFilter>介面。  
  
2.  呼叫<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>方法。  
  
3.  平移，並視需要分派訊息。  
  
4.  如果沒有任何其他控制項處理訊息，請將訊息傳遞至裝載的控制項。  
  
### <a name="ikeyboardinputsink-implementation"></a>IKeyboardInputSink 實作  
 代理訊息迴圈處理鍵盤管理。 因此，<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>方法是唯一<xref:System.Windows.Interop.IKeyboardInputSink>需要在實作的成員<xref:System.Windows.Forms.Integration.WindowsFormsHost>類別。  
  
 根據預設，<xref:System.Windows.Interop.HwndHost>類別會傳回`false`針對其<xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>實作。 這可防止從定位停駐[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制對[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>實作<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>方法會執行下列步驟：  
  
1.  找尋第一個或最後一個[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]所包含的控制項<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項，可以接收焦點。 控制項的選擇取決於周遊資訊。  
  
2.  將焦點設定至控制項，並傳回`true`。  
  
3.  如果沒有控制項可以接收焦點，則會傳回`false`。  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost 註冊  
 當視窗的控制代碼<xref:System.Windows.Forms.Integration.WindowsFormsHost>建立控制項時，<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制呼叫註冊的訊息迴圈其目前狀態的內部靜態方法。  
  
 在註冊期間，<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制會檢查訊息迴圈。 如果尚未啟動的訊息迴圈，<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>建立事件處理常式。 執行時的訊息迴圈會被視為<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>附加事件處理常式。  
  
 終結視窗控制代碼時,<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制會將本身移除註冊。  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost 鍵盤和訊息處理  
 當所裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]應用程式，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]鍵盤和訊息處理包含下列：  
  
-   <xref:System.Windows.Interop.HwndSource><xref:System.Windows.Interop.IKeyboardInputSink>，和<xref:System.Windows.Interop.IKeyboardInputSite>介面實作。  
  
-   按下 tab 鍵和鍵。  
  
-   命令的索引鍵與對話方塊按鍵。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 快速鍵對應處理程序。  
  
 下列各節說明這些組件都更多詳細資料。  
  
### <a name="interface-implementations"></a>介面實作  
 在  [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]，鍵盤訊息會路由傳送至具有焦點之控制項的視窗控制代碼。 在 <xref:System.Windows.Forms.Integration.ElementHost>控制項，這些訊息會路由傳送至裝載的項目。 若要這麼做，<xref:System.Windows.Forms.Integration.ElementHost>控制項提供<xref:System.Windows.Interop.HwndSource>執行個體。 如果<xref:System.Windows.Forms.Integration.ElementHost>控制項有焦點，<xref:System.Windows.Interop.HwndSource>執行個體將路由傳送的大多數鍵盤輸入，以便它可以處理由[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.InputManager>類別。  
  
 <xref:System.Windows.Interop.HwndSource>類別會實作<xref:System.Windows.Interop.IKeyboardInputSink>和<xref:System.Windows.Interop.IKeyboardInputSite>介面。  
  
 實作依賴鍵盤互通<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A>方法來處理 TAB 鍵和箭號索引鍵將焦點從裝載的項目移的輸入。  
  
### <a name="tabbing-and-arrow-keys"></a>Tab 切換和方向鍵  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]選取邏輯會對應至<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>和<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A>方法來實作 索引標籤和箭號索引鍵巡覽。 覆寫<xref:System.Windows.Forms.Integration.ElementHost.Select%2A>方法會完成這項對應。  
  
### <a name="command-keys-and-dialog-box-keys"></a>命令索引鍵和索引鍵對話方塊  
 提供給[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]來處理命令鍵以及對話方塊的索引鍵，第一次的機會[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命令前置處理已連線到<xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>方法。 覆寫<xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType>方法連接這兩項技術。  
  
 使用<xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>方法中，裝載的項目可以處理任何索引鍵的訊息，例如 WM_KEYDOWN、 WM_KEYUP、 WM_SYSKEYDOWN、 或 WM_SYSKEYUP，包括命令按鍵，例如 TAB、 ENTER、 esc 鍵和方向鍵。 如果未處理按鍵訊息，它會傳送[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]祖系階層處理。  
  
### <a name="accelerator-processing"></a>快速鍵處理  
 若要正確地處理加速器[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]加速器處理必須連接到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.AccessKeyManager>類別。 此外，所有的 WM_CHAR 訊息必須正確地路由至裝載的項目。  
  
 因為預設值<xref:System.Windows.Interop.HwndSource>實作<xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>方法會傳回`false`，使用下列邏輯處理 WM_CHAR 訊息：  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType>方法會覆寫以確保所有的 WM_CHAR 訊息會轉送至裝載的項目。  
  
-   如果按下 ALT 鍵時，訊息就會是 WM_SYSCHAR。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 不會前置處理此訊息透過<xref:System.Windows.Forms.Control.IsInputChar%2A>方法。 因此，<xref:System.Windows.Forms.Control.ProcessMnemonic%2A>會覆寫方法來查詢[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.AccessKeyManager>的已註冊的快速鍵。 如果找到已註冊的快速鍵，<xref:System.Windows.Input.AccessKeyManager>加以處理。  
  
-   如果未按下 ALT 鍵時， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>類別處理未處理的輸入。 如果輸入是加速器，<xref:System.Windows.Input.AccessKeyManager>加以處理。 <xref:System.Windows.Input.InputManager.PostProcessInput>的未處理的 WM_CHAR 訊息處理事件。  
  
 當使用者按下 ALT 鍵時，則加速器視覺提示會顯示整個表單上。 若要支援此行為，所有<xref:System.Windows.Forms.Integration.ElementHost>作用中的表單上的控制項接收 WM_SYSKEYDOWN 訊息，不論哪個控制項具有焦點。  
  
 訊息傳送至<xref:System.Windows.Forms.Integration.ElementHost>作用中的表單中的控制項。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [逐步解說：裝載在 WPF 中的 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [逐步解說：裝載 Windows Forms 中的 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
