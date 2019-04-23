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
ms.openlocfilehash: 72b866d714e6a77020bdb74843c3aaa0ba0c3278
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073880"
---
# <a name="focus-overview"></a>焦點概觀
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有兩個關於焦點的主要概念︰鍵盤焦點和邏輯焦點。  鍵盤焦點是指接收鍵盤輸入的項目，邏輯焦點是指焦點範圍中具有焦點的項目。  本概觀會詳細討論這些概念。  了解這些概念的差異對建立複雜的應用程式很重要，這些應用程式有多個可取得焦點的區域。  
  
 參與焦點管理的主要類別皆<xref:System.Windows.Input.Keyboard>類別，<xref:System.Windows.Input.FocusManager>類別和基底的項目，這類類別<xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>。  如需基底項目的詳細資訊，請參閱[基底項目概觀](base-elements-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard>類別有關主要與鍵盤焦點和<xref:System.Windows.Input.FocusManager>是著重於邏輯焦點，但這不是絕對的區別。  具有鍵盤焦點的項目也會有邏輯焦點，但具有邏輯焦點的項目不一定有鍵盤焦點。  當您使用很明顯<xref:System.Windows.Input.Keyboard>類別來設定它具有鍵盤焦點的項目也會設定邏輯焦點的項目上。  

<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>鍵盤焦點  
 鍵盤焦點是指目前接收鍵盤輸入的項目。  整個桌面只能有一個項目有鍵盤焦點。  在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，具有鍵盤焦點的項目會有<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>設定為`true`。  靜態屬性<xref:System.Windows.Input.Keyboard.FocusedElement%2A>上<xref:System.Windows.Input.Keyboard>類別取得目前具有鍵盤焦點的項目。  
  
 為了讓項目取得鍵盤焦點<xref:System.Windows.UIElement.Focusable%2A>而<xref:System.Windows.UIElement.IsVisible%2A>基底的項目上的屬性必須設為`true`。  部分類別，例如<xref:System.Windows.Controls.Panel>基底類別，具有<xref:System.Windows.UIElement.Focusable%2A>設為`false`預設值; 因此，您必須設定<xref:System.Windows.UIElement.Focusable%2A>到`true`如果您想要能夠取得鍵盤焦點的這類項目。  
  
 鍵盤焦點可以透過使用者與 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的互動取得，例如項目的定位處理，或以滑鼠按一下某些項目。  鍵盤焦點，還可以取得以程式設計方式使用<xref:System.Windows.Input.Keyboard.Focus%2A>方法<xref:System.Windows.Input.Keyboard>類別。  <xref:System.Windows.Input.Keyboard.Focus%2A>方法會嘗試將指定的項目鍵盤焦點。  傳回的項目是具有鍵盤焦點的項目，如果舊或新的焦點物件封鎖要求，這可能是不同於要求的項目。  
  
 下列範例會使用<xref:System.Windows.Input.Keyboard.Focus%2A>方法上設定鍵盤焦點<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>基底的項目類別的屬性會取得值，指出項目是否有鍵盤焦點。  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>基底的項目類別的屬性會取得值，指出項目，或任何一種 visual 其子項目是否具有鍵盤焦點。  
  
 當應用程式啟動時設定初始焦點，要接收焦點的項目必須在應用程式所載入之初始視窗的視覺化樹狀結構和元素必須有<xref:System.Windows.UIElement.Focusable%2A>並<xref:System.Windows.UIElement.IsVisible%2A>設定為`true`。  設定初始焦點的建議的位置是在<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。  A<xref:System.Windows.Threading.Dispatcher>回呼也用於藉由呼叫<xref:System.Windows.Threading.Dispatcher.Invoke%2A>或<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>。  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>邏輯焦點  
 邏輯焦點是指<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType>焦點範圍中。  焦點範圍是追蹤的項目<xref:System.Windows.Input.FocusManager.FocusedElement%2A>其範圍內。  當鍵盤焦點離開焦點範圍時，焦點項目就會失去鍵盤焦點，但卻仍然保有邏輯焦點。  當鍵盤焦點回到焦點範圍時，焦點項目就會取得鍵盤焦點。  這讓鍵盤焦點能在多個焦點範圍間變更，但確保當焦點回到集點範圍內時，焦點範圍內的焦點項目會重新取得鍵盤焦點。  
  
 應用程式中可以有多個具有邏輯焦點的項目，但特定的焦點範圍中只能有一個有邏輯焦點的項目。  
  
 具有鍵盤焦點的項目有其所屬焦點範圍的邏輯焦點。  
  
 項目可以轉換成焦點範圍[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]splittunneling<xref:System.Windows.Input.FocusManager>附加屬性<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>至`true`。  在程式碼中的項目可以轉換成焦點範圍藉由呼叫<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>。  
  
 下列範例會使<xref:System.Windows.Controls.StackPanel>成焦點範圍，藉由設定<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>附加屬性。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> 傳回指定之項目的焦點範圍。  
  
 中的類別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是焦點範圍，預設為<xref:System.Windows.Window>， <xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.ToolBar>，和<xref:System.Windows.Controls.ContextMenu>。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> 取得指定的焦點範圍的焦點項目。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 指定的焦點範圍中設定焦點的項目。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 通常用來設定初始焦點的項目。  
  
 下例在焦點範圍中設定焦點項目，並取得焦點範圍的焦點項目。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>鍵盤導覽  
 <xref:System.Windows.Input.KeyboardNavigation>類別會負責實作預設的鍵盤焦點導覽，按下其中一個導覽鍵時。  導覽鍵是：索引鍵 索引標籤、 SHIFT + TAB、 CTRL + TAB、 CTRL + SHIFT + TAB、 UPARROW、 向下箭號、 LEFTARROW 和向右鍵。  
  
 設定附加也可以變更導覽容器的瀏覽行為<xref:System.Windows.Input.KeyboardNavigation>屬性<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>， <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>，和<xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>。  這些屬性都屬於類型<xref:System.Windows.Input.KeyboardNavigationMode>和可能的值為<xref:System.Windows.Input.KeyboardNavigationMode.Continue>， <xref:System.Windows.Input.KeyboardNavigationMode.Local>， <xref:System.Windows.Input.KeyboardNavigationMode.Contained>， <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>， <xref:System.Windows.Input.KeyboardNavigationMode.Once>，和<xref:System.Windows.Input.KeyboardNavigationMode.None>。  預設值是<xref:System.Windows.Input.KeyboardNavigationMode.Continue>，表示項目不是導覽容器。  
  
 下列範例會建立<xref:System.Windows.Controls.Menu>數目的<xref:System.Windows.Controls.MenuItem>物件。  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>附加的屬性設定為<xref:System.Windows.Input.KeyboardNavigationMode.Cycle>上<xref:System.Windows.Controls.Menu>。  使用 tab 鍵在變更焦點時<xref:System.Windows.Controls.Menu>、 焦點會移動每個項目和最後一個項目到達時就會回到第一個項目。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>以程式設計方式巡覽焦點  
 額外[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]若要使用焦點項目<xref:System.Windows.UIElement.MoveFocus%2A>和<xref:System.Windows.UIElement.PredictFocus%2A>。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> 將焦點變更至應用程式中的下一個項目。  A<xref:System.Windows.Input.TraversalRequest>用來指定的方向。   <xref:System.Windows.Input.FocusNavigationDirection>傳遞給<xref:System.Windows.UIElement.MoveFocus%2A>指定的不同方向焦點可以移動，例如<xref:System.Windows.Input.FocusNavigationDirection.First>， <xref:System.Windows.Input.FocusNavigationDirection.Last>，<xref:System.Windows.Input.FocusNavigationDirection.Up>和<xref:System.Windows.Input.FocusNavigationDirection.Down>。  
  
 下列範例會使用<xref:System.Windows.FrameworkElement.MoveFocus%2A>變更焦點的項目。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> 傳回變更焦點時接收焦點的物件。  目前，只有<xref:System.Windows.Input.FocusNavigationDirection.Up>， <xref:System.Windows.Input.FocusNavigationDirection.Down>， <xref:System.Windows.Input.FocusNavigationDirection.Left>，和<xref:System.Windows.Input.FocusNavigationDirection.Right>受到<xref:System.Windows.FrameworkElement.PredictFocus%2A>。  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>焦點事件  
 與鍵盤焦點相關的事件<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>，<xref:System.Windows.Input.Keyboard.GotKeyboardFocus>並<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>， <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>。  事件上定義為附加事件<xref:System.Windows.Input.Keyboard>類別，但更容易存取做為基底的項目類別的對等路由事件。  如需事件的詳細資訊，請參閱[路由事件概觀](routed-events-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 項目取得鍵盤焦點時引發。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> 項目失去鍵盤焦點時引發。  如果<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>事件或<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent>處理事件並<xref:System.Windows.RoutedEventArgs.Handled%2A>設定為`true`，則不會變更焦點。  
  
 下列範例會將附加<xref:System.Windows.UIElement.GotKeyboardFocus>並<xref:System.Windows.UIElement.LostKeyboardFocus>事件處理常式<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 當<xref:System.Windows.Controls.TextBox>取得鍵盤焦點<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.TextBox>變更為<xref:System.Windows.Media.Brushes.LightBlue%2A>。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 當<xref:System.Windows.Controls.TextBox>失去鍵盤焦點<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.TextBox>變更回白色。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 與邏輯焦點相關的事件<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>。  這些事件上定義<xref:System.Windows.Input.FocusManager>為附加事件，但<xref:System.Windows.Input.FocusManager>不會公開 CLR 事件包裝函式。  <xref:System.Windows.UIElement> 和<xref:System.Windows.ContentElement>更方便地公開 （expose) 這些事件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [輸入概觀](input-overview.md)
- [基底項目概觀](base-elements-overview.md)
