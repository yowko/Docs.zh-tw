---
title: "在 Win32 和 WPF 之間共用訊息迴圈 | Microsoft Docs"
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
  - "互通性 [WPF], Win32"
  - "訊息迴圈 [WPF]"
  - "共用訊息迴圈"
  - "Win32 程式碼, 共用訊息迴圈"
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 在 Win32 和 WPF 之間共用訊息迴圈
本主題說明如何透過使用 <xref:System.Windows.Threading.Dispatcher> 中現有的訊息迴圈 \(Loop\) 公開，或是在互通性程式碼的 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 端建立個別訊息迴圈，以便實作用來與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 互通的訊息迴圈。  
  
## ComponentDispatcher 和訊息迴圈  
 互通性和鍵盤事件支援的一般案例是實作 <xref:System.Windows.Interop.IKeyboardInputSink>，或是從已經實作 <xref:System.Windows.Interop.IKeyboardInputSink> 的類別 \(例如 <xref:System.Windows.Interop.HwndSource> 或 <xref:System.Windows.Interop.HwndHost>\) 進行子類別化 \(Subclass\)。  不過，鍵盤接收器支援無法處理跨互通界限傳送及接收訊息時，可能產生的所有訊息迴圈需求。  為了協助應用程式訊息迴圈架構的成形，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了 <xref:System.Windows.Interop.ComponentDispatcher> 類別，用以定義供訊息迴圈遵守的簡單通訊協定 \(Protocol\)。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 是公開幾個成員的靜態類別。  每個方法的範圍都隱含繫結至呼叫端執行緒。  訊息迴圈必須在關鍵時間 \(如下一節所定義\) 呼叫部分 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 提供其他元件 \(例如鍵盤接收器\) 可以接聽的事件。  <xref:System.Windows.Threading.Dispatcher> 類別會按照適當的順序呼叫所有適當的 <xref:System.Windows.Interop.ComponentDispatcher> 方法。  若實作的是您自己的訊息，便由您的程式碼負責以類似的方式呼叫 <xref:System.Windows.Interop.ComponentDispatcher> 方法。  
  
 在執行緒上呼叫 <xref:System.Windows.Interop.ComponentDispatcher> 方法只會叫用 \(Invoke\) 已在該執行緒上註冊的事件處理常式 \(Event Handler\)。  
  
## 撰寫訊息迴圈  
 以下提供一份檢查清單，其中列出自行撰寫訊息迴圈時所要使用的 <xref:System.Windows.Interop.ComponentDispatcher> 成員：  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>：訊息迴圈應該呼叫這個成員，表示執行緒是強制回應。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>：訊息迴圈應該呼叫這個成員，表示執行緒已還原為非強制回應。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>：訊息迴圈應該呼叫這個成員，表示 <xref:System.Windows.Interop.ComponentDispatcher> 應該引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> 事件。  如果 <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> 為 `true`，<xref:System.Windows.Interop.ComponentDispatcher> 就不會引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>，但是訊息迴圈還是可以選擇呼叫 <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> \(即使 <xref:System.Windows.Interop.ComponentDispatcher> 在強制回應狀態中無法回應呼叫\)。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>：訊息迴圈應該呼叫這個成員，表示有新的訊息。  傳回的值會指出 <xref:System.Windows.Interop.ComponentDispatcher> 事件的接聽程式 \(Listener\) 是否已處理該訊息。  如果 <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> 傳回 `true` \(已處理\)，發送器應該不會對訊息執行其他動作。  如果傳回值是 `false`，則發送器應該會呼叫 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 函式 `TranslateMessage`，然後再呼叫 `DispatchMessage`。  
  
## 使用 ComponentDispatcher 和現有訊息處理  
 以下提供一份檢查清單，其中列出依賴固有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 訊息迴圈時所要使用的 <xref:System.Windows.Interop.ComponentDispatcher> 成員。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>：傳回應用程式是否已變成強制回應 \(也就是已推入強制回應訊息迴圈\)。  <xref:System.Windows.Interop.ComponentDispatcher> 可以追蹤這個狀態，因為這個類別維護了訊息迴圈傳回之 <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> 和 <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> 呼叫的計數。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 和 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 事件會遵守委派引動過程 的標準規則。  未特別指定叫用委派的順序，而且即使第一個委派將訊息標記為已處理，也會叫用所有的委派。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>：指出進行閒置處理適當又有效率的時間 \(執行緒中沒有其他擱置訊息\)。  如果執行緒是強制回應，則不會引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>：訊息幫浦 \(Message Pump\) 處理之所有訊息都會引發此成員。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>：<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 期間未處理的所有訊息都會引發此成員。  
  
 如果在 <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 事件或 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 事件之後，事件資料中以傳址方式傳遞的 `handled` 參數為 `true`，就會將訊息視為已經處理。  若 `handled` 為 `true`，事件處理常式應該忽略該訊息，因為這表示不同的處理常式已先處理該訊息。  這兩個事件的事件處理常式都可以修改該訊息。  發送器應該發送修改過的訊息，而不是未更動過的原始訊息。  <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 會傳送給所有接聽程式，但在架構目的中，應該只有內含訊息鎖定之 HWND 的最上層視窗 \(Top\-Level Window\) 才能叫用程式碼來回應訊息。  
  
## HwndSource 處理 ComponentDispatcher 事件的方式  
 如果 <xref:System.Windows.Interop.HwndSource> 是最上層視窗 \(無父代 HWND\)，它會註冊 <xref:System.Windows.Interop.ComponentDispatcher>。  如果引發 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>，而且訊息是要用於 <xref:System.Windows.Interop.HwndSource> 或子視窗，<xref:System.Windows.Interop.HwndSource> 便會呼叫其 <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>、<xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>、<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> 鍵盤接收器序列。  
  
 如果 <xref:System.Windows.Interop.HwndSource> 不是最上層視窗 \(有父代 HWND\)，則不會進行任何處理動作。  只有最上層視窗才能執行處理作業，而且任何互通性案例應該都有可以支援鍵盤接收器的最上層視窗。  
  
 如果呼叫 <xref:System.Windows.Interop.HwndSource> 上的 <xref:System.Windows.Interop.HwndHost.WndProc%2A> 之前沒有先呼叫適當的鍵盤接收器方法，應用程式會收到較高層級的鍵盤事件，例如 <xref:System.Windows.UIElement.KeyDown>。  不過，系統不會呼叫任何鍵盤接收器方法，而無法提供需要的鍵盤輸入模型功能，例如便捷鍵 \(Access Key\) 支援。  發生這種情況的原因可能是訊息迴圈未正確通知 <xref:System.Windows.Interop.ComponentDispatcher> 上的相關執行緒，或是父代 HWND 未叫用適當的鍵盤接收器回應。  
  
 如果您使用 <xref:System.Windows.Interop.HwndSource.AddHook%2A> 方法加入進入鍵盤接收器之訊息的攔截程式 \(Hook\)，該訊息可能不會傳送到 HWND。  這個訊息可能已經直接在訊息幫浦層級加以處理，而且不會送出至 `DispatchMessage` 函式。  
  
## 請參閱  
 <xref:System.Windows.Interop.ComponentDispatcher>   
 <xref:System.Windows.Interop.IKeyboardInputSink>   
 [WPF 和 Win32 互通](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [執行緒模型](../../../../docs/framework/wpf/advanced/threading-model.md)   
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)