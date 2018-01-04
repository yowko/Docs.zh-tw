---
title: "Windows Form 和 WPF 互通性輸入架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a246a3297d212eabc31bf2ac9d000aeb56329d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Windows Form 和 WPF 互通性輸入架構
互通性之間[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]需要這兩種技術有適當的鍵盤輸入的處理。 本主題會說明這些技術的實作方式鍵盤和訊息處理，以達到混合式應用程式中的平順互通性。  
  
 本主題包含下列子章節：  
  
-   非強制回應表單和對話方塊  
  
-   WindowsFormsHost 鍵盤和訊息處理  
  
-   ElementHost 鍵盤和訊息處理  
  
## <a name="modeless-forms-and-dialog-boxes"></a>非強制回應表單和對話方塊  
 呼叫<xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>方法<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素以封閉從非強制回應表單或對話方塊方塊[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的應用程式。  
  
 呼叫<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法<xref:System.Windows.Forms.Integration.ElementHost>要開啟的非強制回應控制項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]頁面[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-應用程式。  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost 鍵盤和訊息處理  
 當裝載[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-應用程式，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]鍵盤和訊息處理包含下列項目：  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>類別取得訊息從[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]訊息迴圈，而藉由<xref:System.Windows.Interop.ComponentDispatcher>類別。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>類別會建立代理[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]訊息迴圈，以確保該一般[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]鍵盤處理，就會發生。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>類別會實作<xref:System.Windows.Interop.IKeyboardInputSink>介面來協調與焦點管理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項自行註冊並啟動它的訊息迴圈。  
  
 下列章節將更詳細的程序中的這些部分。  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>取得訊息，從 WPF 訊息迴圈  
 <xref:System.Windows.Interop.ComponentDispatcher>類別實作的訊息迴圈管理員[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 <xref:System.Windows.Interop.ComponentDispatcher>類別會提供可讓外部用戶端篩選器之前的訊息勾點[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]加以處理。  
  
 互通性實作控點<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>事件，可讓[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項來處理訊息之前[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制項。  
  
### <a name="surrogate-windows-forms-message-loop"></a>Surrogate Windows Form 訊息迴圈  
 根據預設，<xref:System.Windows.Forms.Application?displayProperty=nameWithType>類別包含的主要訊息迴圈[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]應用程式。 互通性，期間[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]訊息迴圈不處理訊息。 因此，必須重新產生這個邏輯。 處理常式<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>事件執行下列步驟：  
  
1.  訊息使用篩選<xref:System.Windows.Forms.IMessageFilter>介面。  
  
2.  呼叫<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>方法。  
  
3.  將轉譯和分派訊息，如有必要。  
  
4.  如果沒有其他控制項可以處理訊息，請將訊息傳遞至裝載的控制項。  
  
### <a name="ikeyboardinputsink-implementation"></a>IKeyboardInputSink 實作  
 代理訊息迴圈處理鍵盤管理。 因此，<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>方法是唯一<xref:System.Windows.Interop.IKeyboardInputSink>成員需要在實作<xref:System.Windows.Forms.Integration.WindowsFormsHost>類別。  
  
 根據預設，<xref:System.Windows.Interop.HwndHost>類別會傳回`false`針對其<xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>實作。 這可防止從按下 tab 鍵[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]控制權傳輸至[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控制項。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>實作<xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType>方法會執行下列步驟：  
  
1.  尋找第一個或最後一個[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]所包含的控制項<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項，可以接收焦點。 控制項的選擇取決於周遊資訊。  
  
2.  將焦點設定為控制項，並傳回`true`。  
  
3.  如果沒有控制項可以接收焦點，就會傳回`false`。  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost 註冊  
 當視窗的控制代碼<xref:System.Windows.Forms.Integration.WindowsFormsHost>建立控制項時，<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項便會呼叫註冊其目前狀態的訊息迴圈內部的靜態方法。  
  
 在註冊期間，<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制會檢查訊息迴圈。 如果尚未啟動訊息迴圈，<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>建立事件處理常式。 訊息迴圈會被視為在執行時<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>附加事件處理常式。  
  
 終結視窗控制代碼時，<xref:System.Windows.Forms.Integration.WindowsFormsHost>控制項則會從登錄移除本身。  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost 鍵盤和訊息處理  
 當裝載[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]應用程式，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]鍵盤和訊息處理包含下列項目：  
  
-   <xref:System.Windows.Interop.HwndSource><xref:System.Windows.Interop.IKeyboardInputSink>，和<xref:System.Windows.Interop.IKeyboardInputSite>介面實作。  
  
-   按下 tab 鍵和箭號索引鍵。  
  
-   命令的索引鍵與對話方塊按鍵。  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]對應處理程序。  
  
 下列章節將更多詳細資料中的這些組件。  
  
### <a name="interface-implementations"></a>介面實作  
 在[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]，鍵盤訊息會路由傳送至具有焦點的控制項的視窗控制代碼。 在<xref:System.Windows.Forms.Integration.ElementHost>控制項，這些訊息會路由傳送至裝載的項目。 若要達成此目的，<xref:System.Windows.Forms.Integration.ElementHost>控制項提供<xref:System.Windows.Interop.HwndSource>執行個體。 如果<xref:System.Windows.Forms.Integration.ElementHost>控制項有焦點，<xref:System.Windows.Interop.HwndSource>執行路由傳送的輸入，因此可處理的大部分鍵盤[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.InputManager>類別。  
  
 <xref:System.Windows.Interop.HwndSource>類別會實作<xref:System.Windows.Interop.IKeyboardInputSink>和<xref:System.Windows.Interop.IKeyboardInputSite>介面。  
  
 實作依賴鍵盤互通<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A>方法，以控制代碼 TAB 鍵和方向鍵索引鍵將焦點從裝載的項目移的輸入。  
  
### <a name="tabbing-and-arrow-keys"></a>Tab 切換和方向鍵  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]選取邏輯會對應至<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>和<xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A>方法來實作 TAB 和方向鍵索引鍵巡覽。 覆寫<xref:System.Windows.Forms.Integration.ElementHost.Select%2A>方法會完成這項對應。  
  
### <a name="command-keys-and-dialog-box-keys"></a>命令索引鍵和索引鍵對話方塊  
 若要讓[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]第一個有機會處理命令和對話方塊金鑰，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]命令前置處理已連線到<xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>方法。 覆寫<xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType>方法連接這兩項技術。  
  
 與<xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>方法中，裝載項目可以處理任何索引鍵的訊息，例如 WM_KEYUP WM_KEYDOWN、 WM_SYSKEYDOWN、 或 WM_SYSKEYUP，包括命令的按鍵，例如 TAB、 ENTER、 esc 鍵和方向鍵。 如果未處理按鍵訊息，就會傳送[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]處理的上階階層。  
  
### <a name="accelerator-processing"></a>快速鍵處理  
 正確地處理加速器，[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]快速鍵處理必須連接到[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.AccessKeyManager>類別。 此外，所有的 WM_CHAR 訊息必須正確地路由傳送至裝載的項目。  
  
 因為預設<xref:System.Windows.Interop.HwndSource>實作<xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>方法會傳回`false`，WM_CHAR 訊息將會使用處理下列邏輯：  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType>以確保所有的 WM_CHAR 訊息會轉寄至裝載的項目會覆寫方法。  
  
-   如果按下 ALT 鍵時，訊息就會 WM_SYSCHAR。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]不會透過此訊息前置處理<xref:System.Windows.Forms.Control.IsInputChar%2A>方法。 因此，<xref:System.Windows.Forms.Control.ProcessMnemonic%2A>會覆寫方法來查詢[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Input.AccessKeyManager>的已註冊的快速鍵。 如果找到已註冊的 accelerator，<xref:System.Windows.Input.AccessKeyManager>加以處理。  
  
-   如果未按下 ALT 鍵， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>類別處理未處理的輸入。 如果輸入是快速鍵，<xref:System.Windows.Input.AccessKeyManager>加以處理。 <xref:System.Windows.Input.InputManager.PostProcessInput>未處理的 WM_CHAR 訊息處理事件。  
  
 當使用者按下 ALT 鍵時，整個表單會顯示快速鍵視覺提示。 若要支援此行為，所有<xref:System.Windows.Forms.Integration.ElementHost>作用中的表單上控制項接收 WM_SYSKEYDOWN 訊息，不論哪個控制項具有焦點。  
  
 訊息傳送至<xref:System.Windows.Forms.Integration.ElementHost>現用表單中的控制項。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [逐步解說：在 WPF 中裝載 Windows Forms 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [逐步解說：在 Windows Forms 中裝載 WPF 複合控制項](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
