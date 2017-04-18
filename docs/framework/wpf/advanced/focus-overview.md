---
title: "焦點概觀 | Microsoft Docs"
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
  - "應用程式, 焦點"
  - "應用程式中的焦點"
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 焦點概觀
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有兩個關於焦點的主要概念：鍵盤焦點和邏輯焦點。  鍵盤焦點是指收到鍵盤輸入的項目，而邏輯焦點則是指在焦點範圍中具有焦點的項目。  本概觀將詳細討論這些概念。  認識這些概念的差別，將對建立具有可取得焦點的多個區域的複雜應用程式十分有幫助。  
  
 參與焦點管理的主要類別包括 <xref:System.Windows.Input.Keyboard> 類別、<xref:System.Windows.Input.FocusManager> 類別以及基底項目類別，例如 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement>。  如需基底項目的詳細資訊，請參閱[基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard> 類別主要與鍵盤焦點相關，而 <xref:System.Windows.Input.FocusManager> 則主要與邏輯焦點相關，但這並不是絕對的分際。  具有鍵盤焦點的項目也會具有邏輯焦點，但具有邏輯焦點的項目則不一定會具有鍵盤焦點。  這在使用 <xref:System.Windows.Input.Keyboard> 類別設定具有鍵盤焦點的項目時可明顯看出，因為它也會在項目上設定邏輯焦點。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Keyboard_Focus"></a>   
## 鍵盤焦點  
 鍵盤焦點是指目前收到鍵盤輸入的項目。  在整個桌面上只能有一個項目具有鍵盤焦點。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，具有鍵盤焦點的項目的 <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> 將會設成 `true`。  <xref:System.Windows.Input.Keyboard> 類別上的靜態屬性 <xref:System.Windows.Input.Keyboard.FocusedElement%2A> 會取得目前具有鍵盤焦點的項目。  
  
 為了要讓項目取得鍵盤焦點，基底項目上的 <xref:System.Windows.UIElement.Focusable%2A> 和 <xref:System.Windows.UIElement.IsVisible%2A> 屬性必須設定為 `true`。  有些如 <xref:System.Windows.Controls.Panel> 基底類別的類別，預設會將 <xref:System.Windows.UIElement.Focusable%2A> 設為 `false`，因此，如果要項目能夠取得鍵盤焦點，就必須將 <xref:System.Windows.UIElement.Focusable%2A> 設為 `true`。  
  
 鍵盤焦點可透過與 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的使用者互動取得，例如使用 TAB 鍵巡覽到某個項目，或是在某些項目上按一下滑鼠。  另外，也可以使用 <xref:System.Windows.Input.Keyboard> 類別上的 <xref:System.Windows.Input.Keyboard.Focus%2A> 方法，以程式設計方式取得鍵盤焦點。  <xref:System.Windows.Input.Keyboard.Focus%2A> 方法會嘗試將鍵盤焦點交給指定項目。  傳回的項目就是具有鍵盤焦點的項目，但如果舊的或新的焦點物件封鎖要求，則回傳的項目可能與原本要求的項目不同。  
  
 下列範例使用 <xref:System.Windows.Input.Keyboard.Focus%2A> 方法，將鍵盤焦點設給 <xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 基底項目類別上的 <xref:System.Windows.UIElement.IsKeyboardFocused%2A> 屬性會取得值，指出項目是否具有鍵盤焦點。  基底項目類別上的 <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> 會取得值，指出項目或其任何視覺化子項目是否具有鍵盤焦點。  
  
 設定應用程式啟動的初始焦點時，要接收焦點的項目必須位於應用程式所載入之初始視窗的視覺化樹狀結構，而且該項目必須將 <xref:System.Windows.UIElement.Focusable%2A> 與 <xref:System.Windows.UIElement.IsVisible%2A> 設為 `true`。  設定初始焦點的建議位置是在 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式。  <xref:System.Windows.Threading.Dispatcher> 回呼 \(Callback\) 也可以藉由呼叫 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 或 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 來使用。  
  
<a name="Logical_Focus"></a>   
## 邏輯焦點  
 邏輯焦點是指焦點範圍中的 <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=fullName>。  焦點範圍是一個項目，會持續追蹤範圍內的 <xref:System.Windows.Input.FocusManager.FocusedElement%2A>。  當鍵盤焦點離開焦點範圍時，具有焦點的項目會失去鍵盤焦點，但卻仍然保有邏輯焦點。  當鍵盤焦點返回焦點範圍時，具有焦點的項目將會取得鍵盤焦點。  這樣可以讓鍵盤焦點在多個焦點範圍間變更，但可以確保在焦點返回焦點範圍時，焦點範圍中的焦點項目會重新取得鍵盤焦點。  
  
 應用程式中可以有多個項目具有邏輯焦點，但在特定焦點範圍中只能有一個項目具有邏輯焦點。  
  
 具有鍵盤焦點的項目也具有所屬焦點範圍的邏輯焦點。  
  
 將 <xref:System.Windows.Input.FocusManager> 的附加屬性 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> 設為 `true`，即可讓任一項目進入 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中的焦點範圍。  在程式碼中，項目則可藉由呼叫 <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> 進入焦點範圍。  
  
 下列範例藉由設定 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> 附加屬性，讓 <xref:System.Windows.Controls.StackPanel> 進入焦點範圍。  
  
 [!code-xml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> 會傳回所指定項目的焦點範圍。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中預設是焦點範圍的類別有 <xref:System.Windows.Window>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.ToolBar> 和 <xref:System.Windows.Controls.ContextMenu>。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> 會取得所指定焦點範圍的焦點項目。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 會設定所指定焦點範圍中的焦點項目。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 通常用來設定初始焦點項目。  
  
 下列範例會在焦點範圍設定焦點項目，並取得焦點範圍的焦點項目。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## 鍵盤巡覽  
 當按下其中一個巡覽鍵時，<xref:System.Windows.Input.KeyboardNavigation> 類別會負責實作預設鍵盤焦點巡覽。  巡覽鍵有：TAB、SHIFT\+TAB、CTRL\+TAB、CTRL\+SHIFT\+TAB 鍵、向上、向下、向左和向右鍵。  
  
 巡覽容器的巡覽行為可藉由設定附加 <xref:System.Windows.Input.KeyboardNavigation> 屬性 <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>、<xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> 和 <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> 來變更。  這些屬性的型別為 <xref:System.Windows.Input.KeyboardNavigationMode>，可能的值包括 <xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode>、<xref:System.Windows.Input.KeyboardNavigationMode> 和 <xref:System.Windows.Input.KeyboardNavigationMode>。  預設值為 <xref:System.Windows.Input.KeyboardNavigationMode>，這表示項目不是巡覽容器。  
  
 下列範例會建立一個 <xref:System.Windows.Controls.Menu>，其有數個 <xref:System.Windows.Controls.MenuItem> 物件。  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> 附加屬性會設為 <xref:System.Windows.Controls.Menu> 上的 <xref:System.Windows.Input.KeyboardNavigationMode>。  在 <xref:System.Windows.Controls.Menu> 內使用 Tab 鍵變更焦點時，焦點會從每個項目移動，當達到最後一個項目時，焦點就會回到第一個項目。  
  
 [!code-xml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## 利用程式設計方式巡覽焦點  
 與焦點相關的其他 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 應用還包括 <xref:System.Windows.UIElement.MoveFocus%2A> 與 <xref:System.Windows.UIElement.PredictFocus%2A>。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> 會將焦點切換到應用程式中的下一個項目。  <xref:System.Windows.Input.TraversalRequest> 是用來指定方向。  傳遞至 <xref:System.Windows.UIElement.MoveFocus%2A> 的 <xref:System.Windows.Input.FocusNavigationDirection> 會指定焦點可移動的不同方向，例如 <xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection> 和 <xref:System.Windows.Input.FocusNavigationDirection>。  
  
 下列範例使用 <xref:System.Windows.FrameworkElement.MoveFocus%2A> 變更焦點項目。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> 會傳回變更焦點時將接收焦點的物件。  目前，<xref:System.Windows.FrameworkElement.PredictFocus%2A> 只支援 <xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection>、<xref:System.Windows.Input.FocusNavigationDirection> 和 <xref:System.Windows.Input.FocusNavigationDirection>。  
  
<a name="Focus_Events"></a>   
## 焦點事件  
 與鍵盤焦點相關的事件有 <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>、<xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 和 <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>、<xref:System.Windows.Input.Keyboard.LostKeyboardFocus>。  這些事件會定義為 <xref:System.Windows.Input.Keyboard> 類別上的附加事件，但當做基底項目類別上的對等路由事件會更容易存取。  如需事件的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 會在項目取得鍵盤焦點時引發。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> 會在項目失去鍵盤焦點時引發。  如果 <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> 事件或 <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> 事件已處理，並將 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設為 `true`，則焦點不會變更。  
  
 下列範例將 <xref:System.Windows.UIElement.GotKeyboardFocus> 和 <xref:System.Windows.UIElement.LostKeyboardFocus> 事件處理常式附加到 <xref:System.Windows.Controls.TextBox>。  
  
 [!code-xml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 當 <xref:System.Windows.Controls.TextBox> 取得鍵盤焦點時，<xref:System.Windows.Controls.TextBox> 的 <xref:System.Windows.Controls.Control.Background%2A> 屬性會變成 <xref:System.Windows.Media.Brushes.LightBlue%2A>。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 當 <xref:System.Windows.Controls.TextBox> 失去鍵盤焦點時，<xref:System.Windows.Controls.TextBox> 的 <xref:System.Windows.Controls.Control.Background%2A> 屬性會變回白色。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 與邏輯焦點相關的事件有 <xref:System.Windows.UIElement.GotFocus> 和 <xref:System.Windows.UIElement.LostFocus>。  這些事件會在 <xref:System.Windows.Input.FocusManager> 上定義為附加屬性，但 <xref:System.Windows.Input.FocusManager> 不會公開 CLR 事件包裝函式。  <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 能更便利地公開這些事件。  
  
## 請參閱  
 <xref:System.Windows.Input.FocusManager>   
 <xref:System.Windows.UIElement>   
 <xref:System.Windows.ContentElement>   
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)