---
title: 焦點概觀
description: 深入瞭解 Windows Presentation Foundation 中著重于焦點的兩個主要概念：鍵盤焦點和邏輯焦點。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 71aeb577cccd2c3b16df1c5a3cb772dd1f5479e2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165102"
---
# <a name="focus-overview"></a>焦點概觀
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有兩個關於焦點的主要概念︰鍵盤焦點和邏輯焦點。  鍵盤焦點是指接收鍵盤輸入的項目，邏輯焦點是指焦點範圍中具有焦點的項目。  本概觀會詳細討論這些概念。  了解這些概念的差異對建立複雜的應用程式很重要，這些應用程式有多個可取得焦點的區域。  
  
 參與焦點管理的主要類別是 <xref:System.Windows.Input.Keyboard> 類別、 <xref:System.Windows.Input.FocusManager> 類別和基底元素類別，例如 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 。  如需基底項目的詳細資訊，請參閱[基底項目概觀](base-elements-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard>類別主要是與鍵盤焦點有關，而且 <xref:System.Windows.Input.FocusManager> 主要著重于邏輯焦點，但這並不是絕對的區別。  具有鍵盤焦點的項目也會有邏輯焦點，但具有邏輯焦點的項目不一定有鍵盤焦點。  當您使用 <xref:System.Windows.Input.Keyboard> 類別來設定具有鍵盤焦點的專案時，這會很明顯，也就是在元素上設定邏輯焦點。  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>鍵盤焦點  
 鍵盤焦點是指目前接收鍵盤輸入的項目。  整個桌面只能有一個項目有鍵盤焦點。  在中 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ，具有鍵盤焦點的元素會將 <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> 設定為 `true` 。  <xref:System.Windows.Input.Keyboard.FocusedElement%2A>類別上的靜態屬性 <xref:System.Windows.Input.Keyboard> 會取得目前具有鍵盤焦點的元素。  
  
 為了讓元素取得鍵盤焦點， <xref:System.Windows.UIElement.Focusable%2A> 基底專案上的和 <xref:System.Windows.UIElement.IsVisible%2A> 屬性必須設定為 `true` 。  某些類別（例如 <xref:System.Windows.Controls.Panel> 基類） <xref:System.Windows.UIElement.Focusable%2A> 預設會設定為， `false` 因此， <xref:System.Windows.UIElement.Focusable%2A> `true` 如果您想要讓這類專案能夠取得鍵盤焦點，則必須將設為。  
  
 鍵盤焦點可以透過使用者與 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的互動取得，例如項目的定位處理，或以滑鼠按一下某些項目。  您也可以在類別上使用方法，以程式設計方式取得鍵盤焦點 <xref:System.Windows.Input.Keyboard.Focus%2A> <xref:System.Windows.Input.Keyboard> 。  <xref:System.Windows.Input.Keyboard.Focus%2A>方法會嘗試提供指定的元素鍵盤焦點。  傳回的項目是具有鍵盤焦點的項目，如果舊或新的焦點物件封鎖要求，這可能是不同於要求的項目。  
  
 下列範例會使用 <xref:System.Windows.Input.Keyboard.Focus%2A> 方法，在上設定鍵盤焦點 <xref:System.Windows.Controls.Button> 。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>基底元素類別上的屬性會取得一個值，指出專案是否具有鍵盤焦點。  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>基底元素類別上的屬性會取得一個值，指出元素或其任何一個視覺子專案是否具有鍵盤焦點。  
  
 在應用程式啟動時設定初始焦點時，要接收焦點的元素必須位於應用程式載入之初始視窗的視覺化樹狀結構中，而且專案必須具有 <xref:System.Windows.UIElement.Focusable%2A> ，並 <xref:System.Windows.UIElement.IsVisible%2A> 將設定為 `true` 。  設定初始焦點的建議位置是在 <xref:System.Windows.FrameworkElement.Loaded> 事件處理常式中。  <xref:System.Windows.Threading.Dispatcher>回呼也可以藉由呼叫或來 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> 使用 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 。  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>邏輯焦點  
 邏輯焦點是指 <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> 焦點範圍中的。  焦點範圍是追蹤 <xref:System.Windows.Input.FocusManager.FocusedElement%2A> 其範圍內的元素。  當鍵盤焦點離開焦點範圍時，焦點項目就會失去鍵盤焦點，但卻仍然保有邏輯焦點。  當鍵盤焦點回到焦點範圍時，焦點項目就會取得鍵盤焦點。  這讓鍵盤焦點能在多個焦點範圍間變更，但確保當焦點回到集點範圍內時，焦點範圍內的焦點項目會重新取得鍵盤焦點。  
  
 應用程式中可以有多個具有邏輯焦點的項目，但特定的焦點範圍中只能有一個有邏輯焦點的項目。  
  
 具有鍵盤焦點的項目有其所屬焦點範圍的邏輯焦點。  
  
 藉 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 由將 <xref:System.Windows.Input.FocusManager> 附加屬性設定為，可以將專案轉換成中的焦點範圍 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> `true` 。  在程式碼中，可以藉由呼叫，將專案轉換成焦點範圍 <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> 。  
  
 下列範例會藉 <xref:System.Windows.Controls.StackPanel> 由設定附加屬性，使成為焦點範圍 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> 。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>傳回指定元素的焦點範圍。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]預設為焦點範圍的類別為 <xref:System.Windows.Window> 、 <xref:System.Windows.Controls.MenuItem> 、 <xref:System.Windows.Controls.ToolBar> 和 <xref:System.Windows.Controls.ContextMenu> 。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>取得指定焦點範圍的焦點元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>設定指定焦點範圍中的焦點元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>通常用來設定初始專注的元素。  
  
 下例在焦點範圍中設定焦點項目，並取得焦點範圍的焦點項目。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>鍵盤導覽  
 <xref:System.Windows.Input.KeyboardNavigation>當按下其中一個導覽鍵時，類別會負責執行預設的鍵盤焦點導覽。  導覽鍵是︰TAB、SHIFT+TAB、CTRL+TAB、CTRL+SHIFT+TAB、UPARROW、DOWNARROW、LEFTARROW 和 RIGHTARROW 等鍵。  
  
 您可以藉由設定附加 <xref:System.Windows.Input.KeyboardNavigation> 屬性、和來變更導覽容器的導覽 <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> 行為 <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> 。  這些屬性的類型是 <xref:System.Windows.Input.KeyboardNavigationMode> ，而且可能的值為 <xref:System.Windows.Input.KeyboardNavigationMode.Continue> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Local> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Contained> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Once> 和 <xref:System.Windows.Input.KeyboardNavigationMode.None> 。  預設值為 <xref:System.Windows.Input.KeyboardNavigationMode.Continue> ，表示元素不是導覽容器。  
  
 下列範例會建立 <xref:System.Windows.Controls.Menu> 具有多個物件的 <xref:System.Windows.Controls.MenuItem> 。  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>附加屬性在上設定為 <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Controls.Menu> 。  當焦點在中使用 tab 鍵變更時 <xref:System.Windows.Controls.Menu> ，焦點會從每個專案移動，而當到達最後一個元素時，焦點就會回到第一個專案。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>以程式設計方式巡覽焦點  
 另一個使用焦點的 API 是 <xref:System.Windows.UIElement.MoveFocus%2A> 和 <xref:System.Windows.UIElement.PredictFocus%2A> 。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>將焦點變更至應用程式中的下一個元素。  <xref:System.Windows.Input.TraversalRequest>是用來指定方向。   <xref:System.Windows.Input.FocusNavigationDirection>傳遞給的 <xref:System.Windows.UIElement.MoveFocus%2A> 會指定可以移動的不同方向焦點，例如 <xref:System.Windows.Input.FocusNavigationDirection.First> 、 <xref:System.Windows.Input.FocusNavigationDirection.Last> <xref:System.Windows.Input.FocusNavigationDirection.Up> 和 <xref:System.Windows.Input.FocusNavigationDirection.Down> 。  
  
 下列範例會使用 <xref:System.Windows.FrameworkElement.MoveFocus%2A> 來變更焦點元素。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>傳回物件，如果要變更焦點，則會收到焦點。  目前，僅 <xref:System.Windows.Input.FocusNavigationDirection.Up> 支援、、 <xref:System.Windows.Input.FocusNavigationDirection.Down> <xref:System.Windows.Input.FocusNavigationDirection.Left> 和 <xref:System.Windows.Input.FocusNavigationDirection.Right> <xref:System.Windows.FrameworkElement.PredictFocus%2A> 。  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>焦點事件  
 與鍵盤焦點相關的事件為 <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> 、 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 和 <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> 。  事件會定義為類別上的附加事件 <xref:System.Windows.Input.Keyboard> ，但更容易在基底元素類別上作為對等路由事件存取。  如需事件的詳細資訊，請參閱[路由事件概觀](routed-events-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>當元素取得鍵盤焦點時引發。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>當元素失去鍵盤焦點時引發。  如果 <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> 事件或 <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> 事件已處理，而且 <xref:System.Windows.RoutedEventArgs.Handled%2A> 設定為 `true` ，則焦點不會變更。  
  
 下列範例會將 <xref:System.Windows.UIElement.GotKeyboardFocus> 和 <xref:System.Windows.UIElement.LostKeyboardFocus> 事件處理常式附加至 <xref:System.Windows.Controls.TextBox> 。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 當取得 <xref:System.Windows.Controls.TextBox> 鍵盤焦點時，的 <xref:System.Windows.Controls.Control.Background%2A> 屬性 <xref:System.Windows.Controls.TextBox> 會變更為 <xref:System.Windows.Media.Brushes.LightBlue%2A> 。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 當 <xref:System.Windows.Controls.TextBox> 失去鍵盤焦點時，的 <xref:System.Windows.Controls.Control.Background%2A> 屬性 <xref:System.Windows.Controls.TextBox> 會變更回白色。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 與邏輯焦點相關的事件是 <xref:System.Windows.UIElement.GotFocus> 和 <xref:System.Windows.UIElement.LostFocus> 。  這些事件是在 <xref:System.Windows.Input.FocusManager> as 附加事件上定義的，但不 <xref:System.Windows.Input.FocusManager> 會公開 CLR 事件包裝函式。  <xref:System.Windows.UIElement>並 <xref:System.Windows.ContentElement> 更方便地公開這些事件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [輸入概觀](input-overview.md)
- [基底項目概觀](base-elements-overview.md)
