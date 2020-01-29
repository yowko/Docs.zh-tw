---
title: 在 Win32 和 WPF 之間共用訊息迴圈
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: e1b96284d69645876d3e383beb03a2cc540d8b7b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731717"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>在 Win32 和 WPF 之間共用訊息迴圈
本主題描述如何使用 <xref:System.Windows.Threading.Dispatcher> 中的現有訊息迴圈公開，或在交互操作程式碼的 Win32 端上建立個別的訊息迴圈，來執行與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]交互操作的訊息迴圈。  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher 和訊息迴圈  
 互通和鍵盤事件支援的一般案例是執行 <xref:System.Windows.Interop.IKeyboardInputSink>，或從已經實 <xref:System.Windows.Interop.IKeyboardInputSink>的類別（例如 <xref:System.Windows.Interop.HwndSource> 或 <xref:System.Windows.Interop.HwndHost>）進行子類別化。 不過，鍵盤接收支援無法解決您在相交互操作界限之間傳送和接收訊息時，可能會有的所有可能訊息迴圈需求。 為了協助將應用程式訊息迴圈架構正規化，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供 <xref:System.Windows.Interop.ComponentDispatcher> 類別，它會定義簡單的通訊協定，讓訊息迴圈遵循。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 是公開數個成員的靜態類別。 每個方法的範圍會隱含地系結至呼叫執行緒。 訊息迴圈必須在關鍵時間呼叫其中一些 Api （如下一節中所定義）。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 提供其他元件（例如鍵盤接收）可接聽的事件。 <xref:System.Windows.Threading.Dispatcher> 類別會以適當的順序呼叫所有適當的 <xref:System.Windows.Interop.ComponentDispatcher> 方法。 如果您要執行自己的訊息迴圈，您的程式碼會負責以類似的方式呼叫 <xref:System.Windows.Interop.ComponentDispatcher> 方法。  
  
 線上程上呼叫 <xref:System.Windows.Interop.ComponentDispatcher> 方法，只會叫用在該執行緒上註冊的事件處理常式。  
  
## <a name="writing-message-loops"></a>撰寫訊息迴圈  
 以下是您在撰寫自己的訊息迴圈時，將會使用 <xref:System.Windows.Interop.ComponentDispatcher> 成員的檢查清單：  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>：您的訊息迴圈應該呼叫這個來表示執行緒是強制回應的。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>：您的訊息迴圈應該呼叫這個，表示執行緒已還原為 nonmodal。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>：您的訊息迴圈應該呼叫這個，以指出 <xref:System.Windows.Interop.ComponentDispatcher> 應該引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> 事件。 如果 `true`<xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>，則 <xref:System.Windows.Interop.ComponentDispatcher> 不會引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>，但訊息迴圈可能會選擇呼叫 <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>，即使 <xref:System.Windows.Interop.ComponentDispatcher> 無法在處於強制回應狀態時對其進行回應也一樣。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>：您的訊息迴圈應該呼叫這個，以指出有新的訊息可供使用。 傳回值會指出 <xref:System.Windows.Interop.ComponentDispatcher> 事件的接聽程式是否處理訊息。 如果 <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> 傳回 `true` （已處理），發送器應該不會再對訊息執行任何動作。 如果傳回值是 `false`，發送器應該會呼叫 Win32 函數 `TranslateMessage`，然後呼叫 `DispatchMessage`。  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>使用 ComponentDispatcher 和現有的訊息處理  
 以下是當您依賴固有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈時，將會使用 <xref:System.Windows.Interop.ComponentDispatcher> 成員的檢查清單。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>：傳回應用程式是否已通過強制回應（例如已推送強制回應訊息迴圈）。 <xref:System.Windows.Interop.ComponentDispatcher> 可以追蹤這個狀態，因為類別會維護來自訊息迴圈的 <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> 和 <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> 呼叫計數。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 和 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 事件會遵循委派調用的標準規則。 委派是以未指定的順序叫用，而且即使第一個委派將訊息標示為已處理，也會叫用所有委派。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>：表示執行閒置處理的適當且有效率的時間（執行緒沒有其他擱置的訊息）。 如果執行緒為強制回應，則不會引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>：針對訊息抽取處理的所有訊息引發。  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>：針對在 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>期間未處理的所有訊息引發。  
  
 如果在 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 事件或 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 事件之後，就會將訊息視為已處理，`true`會在事件資料中以傳址方式傳遞的 `handled` 參數。 如果 `handled` `true`，事件處理常式應該忽略訊息，因為這表示不同的處理常式會先處理訊息。 這兩個事件的事件處理常式都可以修改訊息。 發送器應分派已修改的訊息，而不是原始的未變更訊息。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 會傳遞至所有接聽程式，但架構的目的是只包含最上層的視窗，而此 HWND 的目標訊息應叫用程式碼來回應訊息。  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource 如何處理 ComponentDispatcher 事件  
 如果 <xref:System.Windows.Interop.HwndSource> 是最上層視窗（沒有父 HWND），它會向 <xref:System.Windows.Interop.ComponentDispatcher>註冊。 如果引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>，而且訊息適用于 <xref:System.Windows.Interop.HwndSource> 或子視窗，<xref:System.Windows.Interop.HwndSource> 會呼叫其 <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>，<xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>，<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> 鍵盤接收序列。  
  
 如果 <xref:System.Windows.Interop.HwndSource> 不是最上層視窗（具有父系 HWND），則不會處理。 只有最上層的視窗才會進行處理，而且預期在任何交互操作案例中，都必須是最上層的視窗，並具有鍵盤接收支援。  
  
 如果在未先呼叫適當的鍵盤接收方法的情況下呼叫 <xref:System.Windows.Interop.HwndSource> 上的 <xref:System.Windows.Interop.HwndHost.WndProc%2A>，您的應用程式將會收到較高層級的鍵盤事件，例如 <xref:System.Windows.UIElement.KeyDown>。 不過，將不會呼叫鍵盤接收方法，這會避開所需的鍵盤輸入模型功能，例如存取金鑰支援。 這可能是因為訊息迴圈未在 <xref:System.Windows.Interop.ComponentDispatcher>上適當地通知相關的執行緒，或父 HWND 並未叫用適當的鍵盤接收回應。  
  
 如果您使用 <xref:System.Windows.Interop.HwndSource.AddHook%2A> 方法來新增該訊息的勾點，則傳送至鍵盤接收的訊息可能不會傳送至 HWND。 訊息可能已直接在訊息抽取層級處理，而未提交至 `DispatchMessage` 函數。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF 和 Win32 交互操作](wpf-and-win32-interoperation.md)
- [執行緒模型](threading-model.md)
- [輸入概觀](input-overview.md)
