---
title: 在 Win32 和 WPF 之間共用訊息迴圈
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 35a908cc26e6b70c9acd8732521837f2b20eaf5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>在 Win32 和 WPF 之間共用訊息迴圈
本主題描述如何實作與互通的訊息迴圈[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，藉由使用現有訊息中的迴圈曝光<xref:System.Windows.Threading.Dispatcher>或藉由建立個別的訊息迴圈上[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]這邊的交互操作的程式碼。  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher 和訊息迴圈  
 要實作的互通性和鍵盤事件支援一般案例是<xref:System.Windows.Interop.IKeyboardInputSink>，或從已經實作的類別的子類別化<xref:System.Windows.Interop.IKeyboardInputSink>，例如<xref:System.Windows.Interop.HwndSource>或<xref:System.Windows.Interop.HwndHost>。 不過，鍵盤接收器支援不會處理所有的訊息迴圈需求，您可能必須傳送和接收訊息跨互通界限時。 若要協助擬定應用程式訊息迴圈架構，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供<xref:System.Windows.Interop.ComponentDispatcher>類別，定義訊息迴圈，以遵循簡單的通訊協定。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 是靜態類別會公開數個成員。 每個方法的範圍會隱含地繫結呼叫執行緒。 訊息迴圈必須呼叫部分[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]在關鍵時刻 （如 下一節中所定義）。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 提供的其他元件 （例如鍵盤接收器） 可以接聽的事件。 <xref:System.Windows.Threading.Dispatcher>類別會呼叫所有適當<xref:System.Windows.Interop.ComponentDispatcher>中適當的順序的方法。 如果您要實作您自己的訊息迴圈，您的程式碼會負責呼叫<xref:System.Windows.Interop.ComponentDispatcher>方法，以類似的方式。  
  
 呼叫<xref:System.Windows.Interop.ComponentDispatcher>執行緒上的方法只會叫用該執行緒已註冊的事件處理常式。  
  
## <a name="writing-message-loops"></a>撰寫訊息迴圈  
 下列是檢查清單<xref:System.Windows.Interop.ComponentDispatcher>如果您要撰寫您自己的訊息迴圈，您將使用的成員：  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>： 呼叫這個方法來表示執行緒為強制回應訊息迴圈。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>： 呼叫這個方法來表示執行緒已還原成 nonmodal 訊息迴圈。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>： 呼叫這個方法，表示訊息迴圈<xref:System.Windows.Interop.ComponentDispatcher>應該引發<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>事件。 <xref:System.Windows.Interop.ComponentDispatcher> 將不會引發<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>如果<xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>是`true`，但呼叫可能會選擇訊息迴圈<xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>即使<xref:System.Windows.Interop.ComponentDispatcher>它處於強制回應狀態時無法回應。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>： 呼叫這個方法以指出新的訊息是使用訊息迴圈。 傳回值會指出是否要接聽程式<xref:System.Windows.Interop.ComponentDispatcher>處理訊息的事件。 如果<xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>傳回`true`（處理），發送器應該執行任何進一步處理訊息。 如果傳回值是`false`，發送器應該如何呼叫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式`TranslateMessage`，然後呼叫`DispatchMessage`。  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>使用 ComponentDispatcher 」 和 「 現有訊息處理  
 下列是檢查清單<xref:System.Windows.Interop.ComponentDispatcher>成員，您將使用如果您依賴固有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]訊息迴圈。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>： 傳回應用程式是否已進入強制回應 （例如，強制訊息迴圈已排除）。 <xref:System.Windows.Interop.ComponentDispatcher> 可以追蹤此狀態，因為該類別會維護的計數<xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>和<xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>於訊息迴圈的呼叫。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 和<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>事件遵循標準的規則，以便委派引動過程。 未指定的順序，會叫用委派，即使第一個會將訊息標示為已處理，會叫用所有的委派。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>： 表示適當且有效率的時間，以執行閒置處理 （沒有其他擱置中訊息的執行緒）。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> 系統不會引發如果執行緒為強制回應。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>： 在訊息幫浦內處理的所有訊息時都引發。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>： 所有期間未處理的訊息時引發<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>。  
  
 訊息會被視為已處理之後如果<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>事件或<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>事件，`handled`事件資料的參考所傳遞的參數是`true`。 如果事件處理常式應忽略該訊息`handled`是`true`，因為這表示不同的處理常式已處理訊息第一次。 這兩個事件的事件處理常式可能會修改訊息。 發送器應該分派已修改的訊息而不原始未變更的訊息。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 傳遞至所有接聽程式，但是架構設計用意在於只包含的 HWND 的目標訊息應叫用程式碼以回應訊息的最上層視窗。  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource 如何處理 ComponentDispatcher 事件  
 如果<xref:System.Windows.Interop.HwndSource>是最上層的視窗 （沒有父代 HWND），它會向<xref:System.Windows.Interop.ComponentDispatcher>。 如果<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>引發時，如果訊息專供<xref:System.Windows.Interop.HwndSource>或子視窗<xref:System.Windows.Interop.HwndSource>呼叫其<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>， <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>，<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A>鍵盤接收器的順序。  
  
 如果<xref:System.Windows.Interop.HwndSource>不是最上層視窗 （具有父 HWND），會有任何處理。 只有最上層視窗是需要進行處理，但那里預計要做為任何互通性案例的一部分的鍵盤接收器支援的最上層視窗。  
  
 如果<xref:System.Windows.Interop.HwndHost.WndProc%2A>上<xref:System.Windows.Interop.HwndSource>呼叫沒有先呼叫適當的鍵盤接收器方法，您的應用程式會收到較高的層級的鍵盤事件諸如<xref:System.Windows.UIElement.KeyDown>。 不過，沒有任何的鍵盤接收器方法會呼叫，其中規避理想的鍵盤輸入的模型功能，例如存取金鑰的支援。 這可能是因為訊息迴圈沒有適當地通知相關的執行緒上<xref:System.Windows.Interop.ComponentDispatcher>，或因為父 HWND 未叫用適當的鍵盤接收器回應。  
  
 移至的鍵盤接收器的訊息可能不會傳送到 HWND 如果使用加入的訊息勾點<xref:System.Windows.Interop.HwndSource.AddHook%2A>方法。 訊息可能已經直接而不提交至訊息幫浦層級處理`DispatchMessage`函式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Interop.ComponentDispatcher>  
 <xref:System.Windows.Interop.IKeyboardInputSink>  
 [WPF 和 Win32 交互操作](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [執行緒模型](../../../../docs/framework/wpf/advanced/threading-model.md)  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)
