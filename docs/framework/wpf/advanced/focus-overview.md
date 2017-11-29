---
title: "焦點概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4e10f7136b636829f99da34388db7676810cd06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="focus-overview"></a>焦點概觀
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有兩個關於焦點的主要概念︰鍵盤焦點和邏輯焦點。  鍵盤焦點是指接收鍵盤輸入的項目，邏輯焦點是指焦點範圍中具有焦點的項目。  本概觀會詳細討論這些概念。  了解這些概念的差異對建立複雜的應用程式很重要，這些應用程式有多個可取得焦點的區域。  
  
 參與焦點管理的主要類別是<xref:System.Windows.Input.Keyboard>類別<xref:System.Windows.Input.FocusManager>類別和基底的項目類別，例如<xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>。  如需基底項目的詳細資訊，請參閱[基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard>類別主要有關鍵盤焦點，<xref:System.Windows.Input.FocusManager>是著重於邏輯焦點，但這不是絕對的差異。  具有鍵盤焦點的項目也會有邏輯焦點，但具有邏輯焦點的項目不一定有鍵盤焦點。  當您使用時，這會出現<xref:System.Windows.Input.Keyboard>類別來設定的項目具有鍵盤焦點，它也會設定邏輯焦點在項目上。  
  

  
<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>鍵盤焦點  
 鍵盤焦點是指目前接收鍵盤輸入的項目。  整個桌面只能有一個項目有鍵盤焦點。  在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，具有鍵盤焦點的項目會有<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>設`true`。  靜態屬性<xref:System.Windows.Input.Keyboard.FocusedElement%2A>上<xref:System.Windows.Input.Keyboard>類別，取得目前具有鍵盤焦點的項目。  
  
 若要取得鍵盤焦點的項目順序<xref:System.Windows.UIElement.Focusable%2A>和<xref:System.Windows.UIElement.IsVisible%2A>基底的項目上的屬性必須設為`true`。  部分類別，例如<xref:System.Windows.Controls.Panel>基底類別，具有<xref:System.Windows.UIElement.Focusable%2A>設`false`根據預設值; 因此，您必須設定<xref:System.Windows.UIElement.Focusable%2A>至`true`如果您想要能夠取得鍵盤焦點的這類項目。  
  
 鍵盤焦點可以透過使用者與 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的互動取得，例如項目的定位處理，或以滑鼠按一下某些項目。  鍵盤焦點，還可以取得以程式設計方式使用<xref:System.Windows.Input.Keyboard.Focus%2A>方法<xref:System.Windows.Input.Keyboard>類別。  <xref:System.Windows.Input.Keyboard.Focus%2A>方法會嘗試以提供指定的項目鍵盤焦點。  傳回的項目是具有鍵盤焦點的項目，如果舊或新的焦點物件封鎖要求，這可能是不同於要求的項目。  
  
 下列範例會使用<xref:System.Windows.Input.Keyboard.Focus%2A>方法上設定鍵盤焦點<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>基底項目類別上的屬性會取得值，指出項目是否具有鍵盤焦點。  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>基底項目類別上的屬性會取得值，指出是否在項目，或其中一個 visual 其子項目具有鍵盤焦點。  
  
 當初始焦點設定在應用程式啟動時，要接收焦點的項目必須在初始載入應用程式視窗的視覺化樹狀結構和元素必須有<xref:System.Windows.UIElement.Focusable%2A>和<xref:System.Windows.UIElement.IsVisible%2A>設`true`。  建議設定初始焦點是在<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。  A<xref:System.Windows.Threading.Dispatcher>回呼也可以藉由呼叫用<xref:System.Windows.Threading.Dispatcher.Invoke%2A>或<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>。  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>邏輯焦點  
 邏輯焦點是指<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType>焦點領域中。  焦點範圍則是項目，可追蹤的<xref:System.Windows.Input.FocusManager.FocusedElement%2A>其範圍內。  當鍵盤焦點離開焦點範圍時，焦點項目就會失去鍵盤焦點，但卻仍然保有邏輯焦點。  當鍵盤焦點回到焦點範圍時，焦點項目就會取得鍵盤焦點。  這讓鍵盤焦點能在多個焦點範圍間變更，但確保當焦點回到集點範圍內時，焦點範圍內的焦點項目會重新取得鍵盤焦點。  
  
 應用程式中可以有多個具有邏輯焦點的項目，但特定的焦點範圍中只能有一個有邏輯焦點的項目。  
  
 具有鍵盤焦點的項目有其所屬焦點範圍的邏輯焦點。  
  
 項目可以變成焦點領域中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]藉由設定<xref:System.Windows.Input.FocusManager>附加屬性<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>至`true`。  程式碼中，項目可以變成焦點領域藉由呼叫<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>。  
  
 下列範例使<xref:System.Windows.Controls.StackPanel>焦點領域設定成<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>附加屬性。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>傳回指定之項目的焦點領域。  
  
 中的類別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]這是預設的焦點領域是<xref:System.Windows.Window>， <xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.ToolBar>，和<xref:System.Windows.Controls.ContextMenu>。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>取得焦點的項目指定的焦點領域。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>設定焦點的項目中指定的焦點領域。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>通常用來設定初始焦點的項目。  
  
 下例在焦點範圍中設定焦點項目，並取得焦點範圍的焦點項目。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>鍵盤導覽  
 <xref:System.Windows.Input.KeyboardNavigation>類別會負責實作其中一個瀏覽鍵按下時的預設鍵盤焦點瀏覽。  導覽鍵是︰TAB、SHIFT+TAB、CTRL+TAB、CTRL+SHIFT+TAB、UPARROW、DOWNARROW、LEFTARROW 和 RIGHTARROW 等鍵。  
  
 瀏覽容器的導覽行為可以藉由設定附加變更<xref:System.Windows.Input.KeyboardNavigation>屬性<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>， <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>，和<xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>。  這些屬性屬於類型<xref:System.Windows.Input.KeyboardNavigationMode>和可能的值為<xref:System.Windows.Input.KeyboardNavigationMode.Continue>， <xref:System.Windows.Input.KeyboardNavigationMode.Local>， <xref:System.Windows.Input.KeyboardNavigationMode.Contained>， <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>， <xref:System.Windows.Input.KeyboardNavigationMode.Once>，和<xref:System.Windows.Input.KeyboardNavigationMode.None>。  預設值是<xref:System.Windows.Input.KeyboardNavigationMode.Continue>，這表示項目不是瀏覽容器。  
  
 下列範例會建立<xref:System.Windows.Controls.Menu>數目<xref:System.Windows.Controls.MenuItem>物件。  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>附加的屬性設定為<xref:System.Windows.Input.KeyboardNavigationMode.Cycle>上<xref:System.Windows.Controls.Menu>。  使用 tab 鍵內變更焦點時<xref:System.Windows.Controls.Menu>、 從每個項目會將焦點移和焦點到達最後一個項目會傳回第一個項目。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>以程式設計方式巡覽焦點  
 其他[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]焦點會使用<xref:System.Windows.UIElement.MoveFocus%2A>和<xref:System.Windows.UIElement.PredictFocus%2A>。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>將焦點變更至應用程式中的下一個項目。  A<xref:System.Windows.Input.TraversalRequest>用來指定的方向。   <xref:System.Windows.Input.FocusNavigationDirection>傳遞至<xref:System.Windows.UIElement.MoveFocus%2A>指定不同的方向焦點可以移動，例如<xref:System.Windows.Input.FocusNavigationDirection.First>， <xref:System.Windows.Input.FocusNavigationDirection.Last>，<xref:System.Windows.Input.FocusNavigationDirection.Up>和<xref:System.Windows.Input.FocusNavigationDirection.Down>。  
  
 下列範例會使用<xref:System.Windows.FrameworkElement.MoveFocus%2A>變更焦點的項目。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>傳回變更焦點時接收焦點的物件。  目前，只有<xref:System.Windows.Input.FocusNavigationDirection.Up>， <xref:System.Windows.Input.FocusNavigationDirection.Down>， <xref:System.Windows.Input.FocusNavigationDirection.Left>，和<xref:System.Windows.Input.FocusNavigationDirection.Right>支援<xref:System.Windows.FrameworkElement.PredictFocus%2A>。  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>焦點事件  
 與鍵盤焦點相關的事件是<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>，<xref:System.Windows.Input.Keyboard.GotKeyboardFocus>和<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>， <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>。  為附加事件上定義之事件<xref:System.Windows.Input.Keyboard>類別，但更容易存取做為基底項目類別上的對等路由事件。  如需事件的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>當項目取得鍵盤焦點時引發。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>項目失去鍵盤焦點時引發。  如果<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>事件或<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent>處理事件和<xref:System.Windows.RoutedEventArgs.Handled%2A>設`true`，則不會變更焦點。  
  
 下列範例會附加<xref:System.Windows.UIElement.GotKeyboardFocus>和<xref:System.Windows.UIElement.LostKeyboardFocus>事件處理常式， <xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 當<xref:System.Windows.Controls.TextBox>取得鍵盤焦點<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.TextBox>變更為<xref:System.Windows.Media.Brushes.LightBlue%2A>。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 當<xref:System.Windows.Controls.TextBox>失去鍵盤焦點、<xref:System.Windows.Controls.Control.Background%2A>屬性<xref:System.Windows.Controls.TextBox>變更回為白色。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 邏輯焦點與相關的事件是<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>。  這些事件上定義<xref:System.Windows.Input.FocusManager>為附加的事件，但<xref:System.Windows.Input.FocusManager>不會公開 CLR 事件包裝函式。  <xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>更方便地公開 （expose) 這些事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Input.FocusManager>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.ContentElement>  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)
