---
title: 在 Win32 和 WPF 之間共用訊息迴圈
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 74055ec3facb7db9145c4c0e969d57da24eccbc8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115072"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>在 Win32 和 WPF 之間共用訊息迴圈
本主題描述如何實作與互通訊息迴圈[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，藉由使用現有的訊息迴圈中的曝光度<xref:System.Windows.Threading.Dispatcher>或建立個別的訊息迴圈上[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]這邊的交互操作的程式碼。  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher 和訊息迴圈  
 互通性和鍵盤事件支援的一般案例是實作<xref:System.Windows.Interop.IKeyboardInputSink>，或從已經實作的類別的子類別<xref:System.Windows.Interop.IKeyboardInputSink>，例如<xref:System.Windows.Interop.HwndSource>或<xref:System.Windows.Interop.HwndHost>。 不過，鍵盤接收支援不會處理傳送和接收跨互通界限的訊息時所發生的所有可能的訊息迴圈需求。 為了定形應用程式訊息迴圈架構[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供<xref:System.Windows.Interop.ComponentDispatcher>類別，定義訊息迴圈，以遵循簡單通訊協定。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 會公開數個成員的靜態類別。 每個方法的範圍會以隱含方式繫結進行呼叫的執行緒。 訊息迴圈必須呼叫其中部分[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]（如在下一節中所定義） 的關鍵時刻。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 提供的其他元件 （例如鍵盤接收中） 可以接聽的事件。 <xref:System.Windows.Threading.Dispatcher>類別會呼叫所有適當<xref:System.Windows.Interop.ComponentDispatcher>適當的序列中的方法。 如果您要實作您自己的訊息迴圈，您的程式碼會負責呼叫<xref:System.Windows.Interop.ComponentDispatcher>方法，以類似的方式。  
  
 呼叫<xref:System.Windows.Interop.ComponentDispatcher>在執行緒上的方法只會叫用該執行緒已註冊的事件處理常式。  
  
## <a name="writing-message-loops"></a>撰寫訊息迴圈  
 以下是一份<xref:System.Windows.Interop.ComponentDispatcher>撰寫您自己的訊息迴圈時，您將使用的成員：  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>： 您的訊息迴圈應該呼叫此選項表示執行緒為強制回應。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>： 您的訊息迴圈應該呼叫此選項表示執行緒已還原成 nonmodal。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>： 您的訊息迴圈呼叫這個方法以指出<xref:System.Windows.Interop.ComponentDispatcher>應該引發<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>事件。 <xref:System.Windows.Interop.ComponentDispatcher> 將不會引發<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>如果<xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>是`true`，但訊息迴圈可以選擇呼叫<xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>即使<xref:System.Windows.Interop.ComponentDispatcher>處於強制回應的狀態而無法回應。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>： 訊息迴圈應該呼叫這表示有新的訊息。 傳回值，表示是否要接聽程式<xref:System.Windows.Interop.ComponentDispatcher>事件已處理該訊息。 如果<xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>傳回`true`（處理），發送器應該執行任何進一步處理訊息。 如果傳回的值是`false`，應該發送器會呼叫[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函式`TranslateMessage`，然後呼叫`DispatchMessage`。  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>使用 ComponentDispatcher 和現有的訊息處理  
 以下是一份<xref:System.Windows.Interop.ComponentDispatcher>如果您依賴固有，您將使用的成員[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]訊息迴圈。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>： 傳回應用程式是否已進入強制回應 （例如，強制回應的訊息迴圈已推送）。 <xref:System.Windows.Interop.ComponentDispatcher> 可以追蹤此狀態，因為該類別會維護的計數<xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>和<xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>訊息迴圈的來電。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 和<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>事件遵循標準的規則，以便委派引動過程。 未指定的順序，會叫用委派，即使第一個會將訊息標示為已處理，會叫用所有的委派。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>： 指出適當且有效的時間進行閒置處理 （沒有其他暫止執行緒的訊息）。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> 將不會引發如果執行緒為強制回應。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>： 訊息幫浦程序的所有訊息時都引發。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>： 期間未處理的所有訊息時都引發<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>。  
  
 訊息會被視為已處理之後，如果<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>事件或<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>事件`handled`事件資料中的參考所傳遞的參數是`true`。 事件處理常式應忽略該訊息，如果`handled`是`true`，因為這表示不同的處理常式會先處理訊息。 這兩個事件的事件處理常式可能會修改訊息。 修改過的訊息而不原始未變更的訊息，應該分派發送器。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 傳遞給所有接聽程式，但架構的目的是只包含的 HWND 處的訊息應該叫用程式碼以回應訊息的最上層視窗。  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource ComponentDispatcher 事件的處理方式  
 如果<xref:System.Windows.Interop.HwndSource>是最上層視窗 （沒有父代 HWND），它會向<xref:System.Windows.Interop.ComponentDispatcher>。 如果<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>就會引發，而且如果訊息專供<xref:System.Windows.Interop.HwndSource>或子視窗<xref:System.Windows.Interop.HwndSource>呼叫其<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>， <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>，<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A>鍵盤接收順序。  
  
 如果<xref:System.Windows.Interop.HwndSource>不是最上層視窗 （有父代 HWND），會有任何處理。 只有最上層視窗被認定要做處理，並那里預計要為任何交互操作案例的一部分的鍵盤接收支援的最上層視窗。  
  
 如果<xref:System.Windows.Interop.HwndHost.WndProc%2A>上<xref:System.Windows.Interop.HwndSource>稱為如果沒有先呼叫適當的鍵盤接收方法後，您的應用程式會收到較高的層級的鍵盤事件這類<xref:System.Windows.UIElement.KeyDown>。 不過，沒有鍵盤接收就會呼叫方法，其規避需要的鍵盤輸入的模型功能，例如存取金鑰的支援。 這可能是因為訊息迴圈未適當地通知相關的執行緒上<xref:System.Windows.Interop.ComponentDispatcher>，或因為父 HWND 未叫用適當的鍵盤接收回應。  
  
 前往鍵盤接收的訊息可能不會傳送至 HWND 如果使用加入該訊息的勾點<xref:System.Windows.Interop.HwndSource.AddHook%2A>方法。 訊息可能已處理訊息層級幫浦直接與不提交至`DispatchMessage`函式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF 和 Win32 互通](wpf-and-win32-interoperation.md)
- [執行緒模型](threading-model.md)
- [輸入概觀](input-overview.md)
