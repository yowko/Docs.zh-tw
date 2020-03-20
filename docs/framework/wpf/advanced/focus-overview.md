---
title: 焦點概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: de788ec3f0628ff2f7c422c76c73ff7985424113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186661"
---
# <a name="focus-overview"></a>焦點概觀
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有兩個關於焦點的主要概念︰鍵盤焦點和邏輯焦點。  鍵盤焦點是指接收鍵盤輸入的項目，邏輯焦點是指焦點範圍中具有焦點的項目。  本概觀會詳細討論這些概念。  了解這些概念的差異對建立複雜的應用程式很重要，這些應用程式有多個可取得焦點的區域。  
  
 參與焦點<xref:System.Windows.Input.Keyboard>管理的主要類是類、<xref:System.Windows.Input.FocusManager>類和基元素類，如<xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>。  如需基底項目的詳細資訊，請參閱[基底項目概觀](base-elements-overview.md)。  
  
 類<xref:System.Windows.Input.Keyboard>主要關注鍵盤焦點，主要關注邏輯焦點，<xref:System.Windows.Input.FocusManager>但這不是絕對的區別。  具有鍵盤焦點的項目也會有邏輯焦點，但具有邏輯焦點的項目不一定有鍵盤焦點。  當您使用<xref:System.Windows.Input.Keyboard>類設置具有鍵盤焦點的元素時，這是顯而易見的，因為它還會對元素設置邏輯焦點。  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>鍵盤焦點  
 鍵盤焦點是指目前接收鍵盤輸入的項目。  整個桌面只能有一個項目有鍵盤焦點。  在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中，具有鍵盤焦點的元素將<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>設置為`true`。  類上的<xref:System.Windows.Input.Keyboard>靜態<xref:System.Windows.Input.Keyboard.FocusedElement%2A>屬性獲取當前具有鍵盤焦點的元素。  
  
 為了使元素獲得鍵盤焦點，必須將 基元素<xref:System.Windows.UIElement.Focusable%2A>上的<xref:System.Windows.UIElement.IsVisible%2A>和 屬性設置為`true`。  預設情況下，<xref:System.Windows.Controls.Panel>某些類（如基類）已<xref:System.Windows.UIElement.Focusable%2A>設置為;`false`因此，它已設置為"基類"。因此，如果希望此類<xref:System.Windows.UIElement.Focusable%2A>元素`true`能夠獲得鍵盤焦點，則必須設置為。  
  
 鍵盤焦點可以透過使用者與 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的互動取得，例如項目的定位處理，或以滑鼠按一下某些項目。  鍵盤焦點也可以使用<xref:System.Windows.Input.Keyboard.Focus%2A><xref:System.Windows.Input.Keyboard>類上的方法以程式設計方式獲得。  該方法<xref:System.Windows.Input.Keyboard.Focus%2A>嘗試為指定元素鍵盤焦點提供。  傳回的項目是具有鍵盤焦點的項目，如果舊或新的焦點物件封鎖要求，這可能是不同於要求的項目。  
  
 下面的示例使用 方法<xref:System.Windows.Input.Keyboard.Focus%2A>將鍵盤焦點設置為<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 基<xref:System.Windows.UIElement.IsKeyboardFocused%2A>元素類上的屬性獲取一個值，指示該元素是否具有鍵盤焦點。  基<xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>元素類上的屬性獲取一個值，指示該元素或其任何可視子項目是否具有鍵盤焦點。  
  
 在應用程式啟動時設置初始焦點時，接收焦點的元素必須位於應用程式載入的初始視窗的可視樹中，並且該元素必須具有<xref:System.Windows.UIElement.Focusable%2A>並<xref:System.Windows.UIElement.IsVisible%2A>設置為`true`。  設置初始焦點的建議位置位於事件處理常式中<xref:System.Windows.FrameworkElement.Loaded>。  <xref:System.Windows.Threading.Dispatcher>回檔也可以通過調用<xref:System.Windows.Threading.Dispatcher.Invoke%2A>或<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>使用。  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>邏輯焦點  
 邏輯焦點是指焦點範圍內<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType>的。  焦點範圍是跟蹤其範圍內的元素<xref:System.Windows.Input.FocusManager.FocusedElement%2A>。  當鍵盤焦點離開焦點範圍時，焦點項目就會失去鍵盤焦點，但卻仍然保有邏輯焦點。  當鍵盤焦點回到焦點範圍時，焦點項目就會取得鍵盤焦點。  這讓鍵盤焦點能在多個焦點範圍間變更，但確保當焦點回到集點範圍內時，焦點範圍內的焦點項目會重新取得鍵盤焦點。  
  
 應用程式中可以有多個具有邏輯焦點的項目，但特定的焦點範圍中只能有一個有邏輯焦點的項目。  
  
 具有鍵盤焦點的項目有其所屬焦點範圍的邏輯焦點。  
  
 通過將[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<xref:System.Windows.Input.FocusManager>附加屬性<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>設置為 ，可以將元素轉換為焦點範圍。 `true`  在代碼中，可以通過調用<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>將 元素轉換為焦點範圍。  
  
 下面的示例通過設置<xref:System.Windows.Controls.StackPanel><xref:System.Windows.Input.FocusManager.IsFocusScope%2A>附加屬性將 焦點範圍設置為焦點範圍。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>返回指定元素的焦點範圍。  
  
 預設情況下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在其中作為焦點作用域的類是<xref:System.Windows.Window> <xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.ToolBar>和<xref:System.Windows.Controls.ContextMenu>。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>獲取指定焦點範圍的聚焦元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>在指定的焦點範圍內設置焦點元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>通常用於設置初始焦點元素。  
  
 下例在焦點範圍中設定焦點項目，並取得焦點範圍的焦點項目。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>鍵盤導覽  
 當<xref:System.Windows.Input.KeyboardNavigation>按下其中一個導航鍵時，該類負責實現預設鍵盤焦點導航。  導覽鍵是︰TAB、SHIFT+TAB、CTRL+TAB、CTRL+SHIFT+TAB、UPARROW、DOWNARROW、LEFTARROW 和 RIGHTARROW 等鍵。  
  
 <xref:System.Windows.Input.KeyboardNavigation>可以通過設置附加<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>屬性 和<xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>來更改導航容器的導航行為。 <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>  <xref:System.Windows.Input.KeyboardNavigationMode>這些屬性的類型和可能的值是<xref:System.Windows.Input.KeyboardNavigationMode.Continue>、、、、、、<xref:System.Windows.Input.KeyboardNavigationMode.Once><xref:System.Windows.Input.KeyboardNavigationMode.None><xref:System.Windows.Input.KeyboardNavigationMode.Local><xref:System.Windows.Input.KeyboardNavigationMode.Contained><xref:System.Windows.Input.KeyboardNavigationMode.Cycle>和 。  預設值為<xref:System.Windows.Input.KeyboardNavigationMode.Continue>，這意味著元素不是導航容器。  
  
 下面的示例創建具有多個<xref:System.Windows.Controls.Menu><xref:System.Windows.Controls.MenuItem>物件的 。  附加<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>屬性設置為<xref:System.Windows.Input.KeyboardNavigationMode.Cycle>。 <xref:System.Windows.Controls.Menu>  當使用 中的選項卡鍵更改焦點時<xref:System.Windows.Controls.Menu>，焦點將從每個元素移動，到達最後一個元素時，焦點將返回到第一個元素。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>以程式設計方式巡覽焦點  
 要使用焦點的其他 API<xref:System.Windows.UIElement.MoveFocus%2A>是<xref:System.Windows.UIElement.PredictFocus%2A>和 。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>將焦點更改為應用程式中的下一個元素。  A<xref:System.Windows.Input.TraversalRequest>用於指定方向。   <xref:System.Windows.Input.FocusNavigationDirection> <xref:System.Windows.UIElement.MoveFocus%2A>傳遞給指定<xref:System.Windows.Input.FocusNavigationDirection.First>可以移動的不同方向焦點，例如 ，<xref:System.Windows.Input.FocusNavigationDirection.Last><xref:System.Windows.Input.FocusNavigationDirection.Up>和<xref:System.Windows.Input.FocusNavigationDirection.Down>。  
  
 下面的示例用於<xref:System.Windows.FrameworkElement.MoveFocus%2A>更改焦點元素。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>返回如果焦點被更改，將接收焦點的物件。  目前，只有<xref:System.Windows.Input.FocusNavigationDirection.Up> <xref:System.Windows.Input.FocusNavigationDirection.Down>、<xref:System.Windows.Input.FocusNavigationDirection.Left>和<xref:System.Windows.Input.FocusNavigationDirection.Right>受<xref:System.Windows.FrameworkElement.PredictFocus%2A>的支援。  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>焦點事件  
 與鍵盤<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>焦點相關的事件是 和<xref:System.Windows.Input.Keyboard.GotKeyboardFocus> <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>。 <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>  事件被定義為類上的<xref:System.Windows.Input.Keyboard>附加事件，但更容易訪問為基元素類上的等效路由事件。  如需事件的詳細資訊，請參閱[路由事件概觀](routed-events-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>當元素獲取鍵盤焦點時引發。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>當元素失去鍵盤焦點時引發。  如果<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>事件或<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent>事件已處理並<xref:System.Windows.RoutedEventArgs.Handled%2A>設置為`true`，則焦點不會更改。  
  
 以下示例將<xref:System.Windows.UIElement.GotKeyboardFocus>和<xref:System.Windows.UIElement.LostKeyboardFocus>事件處理常式附加到<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 <xref:System.Windows.Controls.TextBox>獲取鍵盤焦點時，<xref:System.Windows.Controls.Control.Background%2A>的屬性<xref:System.Windows.Controls.TextBox>將更改為<xref:System.Windows.Media.Brushes.LightBlue%2A>。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 當<xref:System.Windows.Controls.TextBox>失去鍵盤焦點時，<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.TextBox>將更改回白色。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 與邏輯焦點相關的事件是<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>。  這些事件在 附加事件上<xref:System.Windows.Input.FocusManager>定義，但不會<xref:System.Windows.Input.FocusManager>公開 CLR 事件包裝器。  <xref:System.Windows.UIElement>並<xref:System.Windows.ContentElement>更方便地公開這些事件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [輸入概觀](input-overview.md)
- [基底項目概觀](base-elements-overview.md)
