---
title: "輸入概觀 | Microsoft Docs"
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
  - "命令 [WPF]"
  - "輸入 [WPF] 概觀"
  - "鍵盤焦點 [WPF]"
  - "鍵盤輸入 [WPF]"
  - "觸控事件 [WPF]"
  - "事件路由 [WPF]"
  - "觸控輸入 [WPF]"
  - "操作 [WPF]"
  - "邏輯焦點 [WPF]"
  - "手寫筆輸入 [WPF]"
  - "文字輸入 [WPF]"
  - "處理輸入的事件 [WPF]"
  - "WPF 中，輸入概觀"
  - "操作事件 [WPF]"
  - "滑鼠輸入 [WPF]"
  - "滑鼠捕捉 [WPF]"
  - "焦點 [WPF]"
  - "滑鼠位置 [WPF]"
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
caps.latest.revision: 50
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 50
---
# 輸入概觀
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]子系統提供功能強大[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]取得各種不同裝置的輸入，包括滑鼠、 鍵盤、 觸控及手寫筆。 本主題說明所提供的服務[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]和說明輸入系統的架構。  
  
  
<a name="input_api"></a>   
## <a name="input-api"></a>輸入 API  
 主要輸入[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]暴露在基底項目類別中找到︰ <xref:System.Windows.UIElement>， <xref:System.Windows.ContentElement>， <xref:System.Windows.FrameworkElement>，和<xref:System.Windows.FrameworkContentElement>。  如需基底的項目，請參閱[基底的項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)。  這些類別提供輸入事件的按鍵動作、 滑鼠按鈕、 滑鼠滾輪、 滑鼠移動，焦點管理和滑鼠捕捉，等等相關的功能。 藉由將輸入放[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]基底的項目，而不是將所有輸入事件做為服務中，輸入的架構可讓 UI 中的特定物件來源，並支援事件路由配置，藉此讓多個項目有機會先處理輸入的事件之輸入的事件。 許多輸入的事件都具有一組與其相關聯的事件。  例如，向下的按鍵事件相關聯<xref:System.Windows.Input.Keyboard.KeyDown>和<xref:System.Windows.Input.Keyboard.PreviewKeyDown>事件。  這些事件中的差異是在目標項目的路由方式。  預覽事件通道項目樹狀結構的根項目從目標項目。  反昇事件反昇至目標項目從根項目。  事件路由中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]稍後在本概觀和詳細討論[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
### <a name="keyboard-and-mouse-classes"></a>鍵盤和滑鼠類別  
 除了輸入[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]基底項目類別，<xref:System.Windows.Input.Keyboard>類別和<xref:System.Windows.Input.Mouse>類別會提供額外[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]使用鍵盤和滑鼠輸入。  
  
 輸入的範例[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]上<xref:System.Windows.Input.Keyboard>類別<xref:System.Windows.Input.Keyboard.Modifiers%2A>屬性，會傳回<xref:System.Windows.Input.ModifierKeys>目前已按下和<xref:System.Windows.Input.Keyboard.IsKeyDown%2A>方法，可判斷是否已按下指定的索引鍵。  
  
 下列範例會使用<xref:System.Windows.Input.Keyboard.GetKeyStates%2A>方法來判斷<xref:System.Windows.Input.Key>處於關閉狀態。  
  
 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]  
  
 輸入的範例[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]上<xref:System.Windows.Input.Mouse>類別<xref:System.Windows.Input.Mouse.MiddleButton%2A>，從中取得滑鼠中間按鈕的狀態和<xref:System.Windows.Input.Mouse.DirectlyOver%2A>，此 cmdlet 會取得之項目的滑鼠指標位於目前。  
  
 下列範例會判斷是否<xref:System.Windows.Input.Mouse.LeftButton%2A>滑鼠處於<xref:System.Windows.Input.MouseButtonState>狀態。  
  
 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]  
  
 <xref:System.Windows.Input.Mouse>和<xref:System.Windows.Input.Keyboard>類別會在此概觀的更詳細地討論。  
  
### <a name="stylus-input"></a>手寫筆輸入  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]已整合的支援<xref:System.Windows.Input.Stylus>。  <xref:System.Windows.Input.Stylus>是所產生的熱門畫筆輸入[!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式可以將滑鼠視為手寫筆使用滑鼠[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]，但是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也會公開使用的鍵盤和滑鼠的類似模型的手寫筆裝置抽象概念。  所有的手寫筆相關[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]包含 「 手寫筆 」 一詞。  
  
 手寫筆可以做為滑鼠，因為只支援滑鼠輸入的應用程式仍然可以自動取得某種程度的手寫筆的支援。 在這種方式使用手寫筆時，應用程式就有機會處理適當的手寫筆事件，然後處理相對應的滑鼠事件。 此外，還有可透過手寫筆裝置抽象較高層級的服務，例如筆跡輸入。  做為輸入筆墨的相關資訊，請參閱[筆墨入門](../../../../docs/framework/wpf/advanced/getting-started-with-ink.md)。  
  
<a name="event_routing"></a>   
## <a name="event-routing"></a>事件路由  
 A <xref:System.Windows.FrameworkElement>可以包含其他項目做為其內容模型中，形成樹狀結構的項目子系項目。  在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，父項目可以參與導向至其子項目或其他子系，藉由處理事件的輸入。 這特別適用於建置控制項出現在較小的控制項，處理程序稱為 「 控制項組合 」 或 「 組合 」。 如需項目樹狀結構，以及與項目樹狀結構關聯事件路由的詳細資訊，請參閱[WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。  
  
 事件路由轉送至多個項目，事件的處理程序是特定物件或路由項目，可以選擇提供主要回應可能由不同的項目來源的事件 （透過處理）。  路由的事件使用三種路由機制的其中一個︰ 直接、 反昇和通道。  在直接路由中，來源項目會收到通知，唯一的項目，事件不會路由至任何其他項目。 不過，直接路由的事件仍會提供一些額外的功能，只會出現的路由事件，而不是標準[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]事件。 反昇項目樹狀結構中向上運作首先會告知事件，然後來源之項目的父項目，依此類推。  通道會從項目樹狀結構的根目錄，然後往下運作，原始的來源項目，以結束。  如需路由事件的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]輸入的事件通常有通道的事件和反昇事件所組成的配對。  通道事件會與 「 預覽 」 前置詞的反昇事件有所區分。  比方說， <xref:System.Windows.Input.Mouse.PreviewMouseMove>是滑鼠移動事件的通道版本和<xref:System.Windows.Input.Mouse.MouseMove>是此事件反昇版本。 事件配對是一項慣例，在項目層級實作，而且不是一項固有的功能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系統。 如需詳細資訊，請參閱 < WPF 輸入事件節[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
<a name="handling_input_events"></a>   
## <a name="handling-input-events"></a>處理輸入的事件  
 若要接收的輸入項目上的，事件處理常式必須與該特定事件相關聯。  在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]這是相當直接︰ 您可以參考事件的名稱做為屬性，將會接聽這個事件的項目。  然後，您可以設定屬性的值定義，委派為基礎的事件處理常式的名稱。  事件處理常式必須撰寫程式碼中例如[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]，而且可以包含在程式碼後置檔案。  
  
 鍵盤事件發生時作業系統回報鍵盤焦點的項目上時所發生的重要動作。 滑鼠及手寫筆事件每分為兩類︰ 變更指標的位置，相對於項目，報表記錄的事件和報告中的裝置按鈕狀態變更的事件。  
  
### <a name="keyboard-input-event-example"></a>鍵盤輸入的事件範例  
 下列範例會接聽向的左鍵按下按鍵。  A <xref:System.Windows.Controls.StackPanel> ，裡面有<xref:System.Windows.Controls.Button>。  向左箭號按鍵會附加至接聽的事件處理常式<xref:System.Windows.Controls.Button>執行個體。  
  
 此範例的第一個區段會建立<xref:System.Windows.Controls.StackPanel>和<xref:System.Windows.Controls.Button>，並將附加的事件處理常式<xref:System.Windows.UIElement.KeyDown>。  
  
 [!code-xml[InputOvw#Input_OvwKeyboardExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]  
  
 第二個區段以程式碼撰寫，並定義事件處理常式。  當按下向的左鍵和<xref:System.Windows.Controls.Button>擁有鍵盤焦點，處理常式的執行和<xref:System.Windows.Controls.Control.Background%2A>色彩<xref:System.Windows.Controls.Button>已變更。  如果按下按鍵，但它不是向的左鍵<xref:System.Windows.Controls.Control.Background%2A>色彩<xref:System.Windows.Controls.Button>變回它的開始色彩。  
  
 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]  
  
### <a name="mouse-input-event-example"></a>滑鼠輸入的事件範例  
 在下列範例中，<xref:System.Windows.Controls.Control.Background%2A>色彩<xref:System.Windows.Controls.Button>變更滑鼠指標進入<xref:System.Windows.Controls.Button>。  <xref:System.Windows.Controls.Control.Background%2A>色彩還原當滑鼠離開<xref:System.Windows.Controls.Button>。  
  
 此範例的第一個區段會建立<xref:System.Windows.Controls.StackPanel>和<xref:System.Windows.Controls.Button>控制，並將附加的事件處理常式<xref:System.Windows.UIElement.MouseEnter>和<xref:System.Windows.UIElement.MouseLeave>事件<xref:System.Windows.Controls.Button>。  
  
 [!code-xml[InputOvw#Input_OvwMouseExampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]  
  
 範例的第二個部分以程式碼撰寫，並定義事件處理常式。  當滑鼠進入<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Control.Background%2A>色彩<xref:System.Windows.Controls.Button>變更為<xref:System.Windows.Media.Brushes.SlateGray%2A>。  當滑鼠離開<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Control.Background%2A>色彩<xref:System.Windows.Controls.Button>變回<xref:System.Windows.Media.Brushes.AliceBlue%2A>。  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]  
  
 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]  
  
<a name="text_input"></a>   
## <a name="text-input"></a>文字輸入  
 <xref:System.Windows.ContentElement.TextInput>事件可讓您聆聽語音文字輸入的與裝置無關的方式。 鍵盤是文字輸入，但是語音、 手寫的主要方法和其他輸入的裝置可以產生也輸入的文字。  
  
 鍵盤輸入[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]首先會傳送適當<xref:System.Windows.ContentElement.KeyDown>/<xref:System.Windows.ContentElement.KeyUp>事件。 如果未處理的事件和索引鍵是文字而非 （例如方向箭號控制金鑰） 或功能鍵，則<xref:System.Windows.ContentElement.TextInput>就會引發事件。  不一定都能之間的簡單一對一對應<xref:System.Windows.ContentElement.KeyDown>/<xref:System.Windows.ContentElement.KeyUp>和<xref:System.Windows.ContentElement.TextInput>事件因為多個按鍵就可以產生單一字元的文字輸入與單一按鍵可以產生多字元的字串。  這特別適用於使用中文、 日文和韓文等語言[!INCLUDE[TLA#tla_ime#plural](../../../../includes/tlasharptla-imesharpplural-md.md)]中其對應的字母產生上千個可能的字元。  
  
 當[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]傳送<xref:System.Windows.ContentElement.KeyUp>/<xref:System.Windows.ContentElement.KeyDown>事件，<xref:System.Windows.Input.KeyEventArgs.Key%2A>設為<xref:System.Windows.Input.Key?displayProperty=fullName>如果按鍵動作可能會變成組件的<xref:System.Windows.ContentElement.TextInput>（ALT + S 按下時，例如） 的事件。 這可讓程式碼中的<xref:System.Windows.ContentElement.KeyDown>事件處理常式來檢查<xref:System.Windows.Input.Key?displayProperty=fullName>而且，如果找到，保留之後引發的處理常式處理<xref:System.Windows.ContentElement.TextInput>事件。 在這些情況下的各種屬性<xref:System.Windows.Input.TextCompositionEventArgs>引數可以用來判斷原始的按鍵。 同樣地，如果[!INCLUDE[TLA2#tla_ime](../../../../includes/tla2sharptla-ime-md.md)]為作用中，<xref:System.Windows.Input.Key>的值為<xref:System.Windows.Input.Key?displayProperty=fullName>，和<xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A>提供原始的按鍵輸入。  
  
 下列範例會定義處理常式<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件和處理常式的<xref:System.Windows.UIElement.KeyDown>事件。  
  
 程式碼或標記的第一個區段會建立使用者介面。  
  
 [!code-xml[InputOvw#Input_OvwTextInputXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]  
  
 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]  
  
 程式碼的第二個區段包含的事件處理常式。  
  
 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]  
  
 輸入的事件反昇事件路由，因為<xref:System.Windows.Controls.StackPanel>收到的輸入，不論哪個項目具有鍵盤焦點。 <xref:System.Windows.Controls.TextBox>控制項第一次收到通知，`OnTextInputKeyDown`才處理常式會呼叫<xref:System.Windows.Controls.TextBox>並未處理輸入。 如果<xref:System.Windows.UIElement.PreviewKeyDown>而不是使用事件<xref:System.Windows.UIElement.KeyDown>事件，`OnTextInputKeyDown`會先呼叫處理常式。  
  
 在此範例中，處理邏輯會寫入兩次，一次 CTRL + O，以及一次按鈕的 click 事件。 這可簡化使用命令，而不直接處理輸入的事件。  本概觀中，然後在討論命令[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
<a name="touch_and_manipulation"></a>   
## <a name="touch-and-manipulation"></a>觸控與操作  
 新的硬體和 Windows 7 作業系統中的 API 提供應用程式能夠同時接收來自多個修飾的輸入。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可讓應用程式，以偵測和回應接觸到另一個輸入，例如滑鼠或鍵盤，藉由引發事件時就會發生觸控回應類似的方式。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]會公開兩種類型的事件時就會發生觸控︰ 觸控事件和操作事件。 觸控事件觸控螢幕，其提供有關每個手指的未經處理資料。 操作事件會解譯成特定動作的輸入。 本章節中討論這兩種類型的事件。  
  
### <a name="prerequisites"></a>必要條件  
 您需要下列元件才能開發涉及回應的應用程式。  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)].  
  
-   Windows 7。  
  
-   觸控螢幕，可支援 Windows Touch 等裝置。  
  
### <a name="terminology"></a>用語  
 觸控討論時，會使用下列詞彙。  
  
-   **觸控**是一種 Windows 7 所能辨識的使用者輸入。 通常，觸控起始將手指放在觸控式螢幕上。 請注意等常見攜帶型電腦的觸控裝置並不支援觸控是否指的位置和移動滑鼠輸入，只是將轉換裝置。  
  
-   **多點觸控**會同時從多個點發生的觸控式。 Windows 7 和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援多點觸控。 每當文件中所討論觸控[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的概念適用於多點觸控。  
  
-   A**操作**觸控會解譯為套用至物件的實體動作時發生。 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，操作事件會解譯為轉譯、 擴充或旋轉操作的輸入。  
  
-   A`touch device`表示產生觸控輸入，例如單指觸控螢幕上的裝置。  
  
### <a name="controls-that-respond-to-touch"></a>回應觸控的控制項  
 下列控制項可捲動的手指拖曳控制項，它具有捲動到檢視之外的內容。  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.DataGrid>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
 <xref:System.Windows.Controls.ScrollViewer>定義<xref:System.Windows.Controls.ScrollViewer.PanningMode%2A?displayProperty=fullName>附加屬性，可讓您指定觸控式移動瀏覽是否已啟用的水平、 垂直、 兩者，或兩者皆非。 <xref:System.Windows.Controls.ScrollViewer.PanningDeceleration%2A?displayProperty=fullName>屬性會指定如何快速地捲動變慢時使用者提開手指從觸控螢幕。 <xref:System.Windows.Controls.ScrollViewer.PanningRatio%2A?displayProperty=fullName>附加的屬性會指定捲動位移轉譯操作位移的比率。  
  
### <a name="touch-events"></a>觸控事件  
 基底類別， <xref:System.Windows.UIElement>， <xref:System.Windows.UIElement3D>，和<xref:System.Windows.ContentElement>，定義您可以訂閱讓您的應用程式會回應接觸的事件。 當您的應用程式會解譯為非操作物件的觸控，觸控事件會很有用。 例如，可讓使用者使用一或多個指繪圖應用程式會訂閱觸控事件。  
  
 所有三個類別定義的行為類似，不論定義類別的下列事件。  
  
-   <xref:System.Windows.UIElement.TouchDown>  
  
-   <xref:System.Windows.UIElement.TouchMove>  
  
-   <xref:System.Windows.UIElement.TouchUp>  
  
-   <xref:System.Windows.UIElement.TouchEnter>  
  
-   <xref:System.Windows.UIElement.TouchLeave>  
  
-   <xref:System.Windows.UIElement.PreviewTouchDown>  
  
-   <xref:System.Windows.UIElement.PreviewTouchMove>  
  
-   <xref:System.Windows.UIElement.PreviewTouchUp>  
  
-   <xref:System.Windows.UIElement.GotTouchCapture>  
  
-   <xref:System.Windows.UIElement.LostTouchCapture>  
  
 鍵盤和滑鼠事件，例如觸控事件都是路由的事件。 開始使用事件`Preview`事件和事件的開頭通道`Touch`會反昇事件。 如需路由事件的詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。 當您處理這些事件時，您可以取得位置的輸入，相對於任何項目，藉由呼叫<xref:System.Windows.Input.TouchEventArgs.GetTouchPoint%2A>或<xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A>方法。  
  
 若要瞭解觸控事件之間的互動，假設使用者項目上將單指、 手指移動項目，然後有一個從項目指的位置。 下圖反昇事件 （省略起見通道事件） 的執行。  
  
 ![觸控事件的順序。](../../../../docs/framework/wpf/advanced/media/ndp-touchevents.png "NDP_TouchEvents")  
觸控事件  
  
 下列清單描述在上圖中的事件順序。  
  
1.  <xref:System.Windows.UIElement.TouchEnter>事件發生於當使用者將手指放在項目一次。  
  
2.  <xref:System.Windows.UIElement.TouchDown>事件都會發生一次。  
  
3.  <xref:System.Windows.UIElement.TouchMove>事件發生很多次，當使用者移動的項目內手指。  
  
4.  <xref:System.Windows.UIElement.TouchUp>事件發生於當使用者提開手指從項目一次。  
  
5.  <xref:System.Windows.UIElement.TouchLeave>事件都會發生一次。  
  
 當使用多個兩隻手指放時，每個手指會發生的事件。  
  
### <a name="manipulation-events"></a>操作事件  
 情況下，應用程式可讓使用者操作的物件， <xref:System.Windows.UIElement>類別會定義操作事件。 不同於只會回報觸控位置觸控事件，操作事件會報告解譯輸入的方式。 有三種類型的操作、 轉譯、 擴展和旋轉。 下列清單說明如何叫用三種類型的操作。  
  
-   將手指放在物件上，並在叫用轉譯操作觸控螢幕上移動手指。 這通常是移動物件。  
  
-   將兩隻手指放在物件上，然後將手指，放大一起或遠除了彼此叫用擴充操作。 這通常是調整物件大小。  
  
-   將兩隻手指放在物件上，然後輪替相互作用旋轉操作叫用手指。 這通常會旋轉物件。  
  
 可以同時進行多個操作類型。  
  
 您會讓物件回應操作，您可以看起來沒有慣性的物件。 這可讓您模擬真實世界的物件。 比方說，如果您推送硬碟，在資料表之間推送活頁簿時夠活頁簿會持續移動後釋放它。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]可讓您藉由引發操作事件之後的使用者指釋放物件模擬此行為。  
  
 如需如何建立可讓使用者移動、 調整大小，和旋轉物件的應用程式資訊，請參閱[逐步解說︰ 建立第一個觸控應用程式](../../../../docs/framework/wpf/advanced/walkthrough-creating-your-first-touch-application.md)。  
  
 <xref:System.Windows.UIElement>會定義下列操作事件。  
  
-   <xref:System.Windows.UIElement.ManipulationStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationStarted>  
  
-   <xref:System.Windows.UIElement.ManipulationDelta>  
  
-   <xref:System.Windows.UIElement.ManipulationInertiaStarting>  
  
-   <xref:System.Windows.UIElement.ManipulationCompleted>  
  
-   <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>  
  
 根據預設， <xref:System.Windows.UIElement>不會收到這些操作事件。 操作事件接收的<xref:System.Windows.UIElement>，請將<xref:System.Windows.UIElement.IsManipulationEnabled%2A?displayProperty=fullName>到`true`。  
  
#### <a name="the-execution-path-of-manipulation-events"></a>操作事件的執行路徑  
 請考慮的案例，其中使用者 」 就會擲回 」 物件。 使用者將手指放在該物件，將手指移過短的距離，觸控螢幕，然後有一個在手指移動時。 因此，則物件將會在使用者的手指移動，並繼續來移動之後使用者提開手指。  
  
 下圖顯示操作事件和每個事件的重要資訊的執行路徑。  
  
 ![操作事件的順序。](../../../../docs/framework/wpf/advanced/media/ndp-manipulationevents.png "NDP_ManipulationEvents")  
操作事件  
  
 下列清單描述在上圖中的事件順序。  
  
1.  <xref:System.Windows.UIElement.ManipulationStarting>事件發生於使用者將手指放在物件上。 在其他方面，此事件可讓您設定<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>屬性。 在後續的事件，操作的位置會相對於<xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A>。 在事件以外<xref:System.Windows.UIElement.ManipulationStarting>，這個屬性是唯讀的因此<xref:System.Windows.UIElement.ManipulationStarting>事件是唯一的時間，您可以設定此屬性。  
  
2.  <xref:System.Windows.UIElement.ManipulationStarted>接下來發生的事件。 此事件報告操作的原點。  
  
3.  <xref:System.Windows.UIElement.ManipulationDelta>事件就會發生多個使用者的手指移動觸控螢幕上的時間。 <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A>屬性<xref:System.Windows.Input.ManipulationDeltaEventArgs>類別會報告操作是否會解譯為移動、 擴充或轉移。 這是工作的您用來執行大部分的管理物件。  
  
4.  <xref:System.Windows.UIElement.ManipulationInertiaStarting>事件發生於使用者的手指與失去連線物件。 此事件可讓您指定的操作期間慣性減速。 這是您的物件可以模擬不同的實體空間或屬性，如果您選擇。 例如，假設應用程式有兩個物件，代表項目在真實世界中，且其中一個是比其他繁重。 您可以將較輕的物件減速重物件。  
  
5.  <xref:System.Windows.UIElement.ManipulationDelta>慣性發生時，事件會發生很多次。 請注意，以及使用者的手指移動觸控螢幕時，會發生此事件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]模擬慣性。 換句話說， <xref:System.Windows.UIElement.ManipulationDelta>之前和之後，就會發生<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件。 <xref:System.Windows.Input.ManipulationDeltaEventArgs.IsInertial%2A?displayProperty=fullName>屬性報告是否<xref:System.Windows.UIElement.ManipulationDelta>事件發生期間慣性，因此您可以檢查該屬性，並執行不同的動作，其值而定。  
  
6.  <xref:System.Windows.UIElement.ManipulationCompleted>就會發生事件的操作和任何慣性結束。 也就是說，之後所有<xref:System.Windows.UIElement.ManipulationDelta>事件發生， <xref:System.Windows.UIElement.ManipulationCompleted>發出信號的操作已完成就會發生事件。  
  
 <xref:System.Windows.UIElement>也會定義<xref:System.Windows.UIElement.ManipulationBoundaryFeedback>事件。 這個事件發生時<xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A>方法被呼叫<xref:System.Windows.UIElement.ManipulationDelta>事件。 <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>事件可讓應用程式或元件物件點擊界限時，提供視覺化回饋。 例如，<xref:System.Windows.Window>類別控制代碼<xref:System.Windows.UIElement.ManipulationBoundaryFeedback>讓視窗稍微移動時遇到其邊緣的事件。  
  
 您可以藉由呼叫取消操作<xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>以外的任何操作事件中的事件引數的方法<xref:System.Windows.UIElement.ManipulationBoundaryFeedback>事件。 當您呼叫<xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>，不會再引發操作事件，而且滑鼠事件發生的觸控。 下表描述的操作已取消的時所發生的滑鼠事件之間的關聯性。  
  
|取消事件中呼叫|發生於輸入已發生的滑鼠事件|  
|----------------------------------------|-----------------------------------------------------------------|  
|<xref:System.Windows.UIElement.ManipulationStarting>和<xref:System.Windows.UIElement.ManipulationStarted>|將滑鼠指標關閉事件。|  
|<xref:System.Windows.UIElement.ManipulationDelta>|按下的滑鼠和滑鼠移動事件。|  
|<xref:System.Windows.UIElement.ManipulationInertiaStarting>和<xref:System.Windows.UIElement.ManipulationCompleted>|滑鼠向下、 滑鼠移動，以及滑鼠向上事件。|  
  
 請注意，如果您呼叫<xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>慣性處理時，此方法會傳回`false`和輸入不會引發滑鼠事件。  
  
### <a name="the-relationship-between-touch-and-manipulation-events"></a>觸控與操作事件之間的關聯性  
 A <xref:System.Windows.UIElement>一律可以收到觸控事件。 當<xref:System.Windows.UIElement.IsManipulationEnabled%2A>屬性設定為`true`、 <xref:System.Windows.UIElement>可以接收觸控與操作事件。  如果<xref:System.Windows.UIElement.TouchDown>不處理事件 (也就是<xref:System.Windows.RoutedEventArgs.Handled%2A>屬性是`false`)，會擷取項目的觸控操作邏輯，並產生操作事件。 如果<xref:System.Windows.RoutedEventArgs.Handled%2A>屬性設定為`true`中<xref:System.Windows.UIElement.TouchDown>事件，操作邏輯不會產生操作事件。 下圖顯示觸控事件和操作事件之間的關係。  
  
 ![觸控與操作事件之間的關聯性](../../../../docs/framework/wpf/advanced/media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents")  
觸控與操作事件  
  
 下列清單描述會顯示在上圖的觸控與操作事件之間的關聯性。  
  
-   當第一個觸控裝置產生<xref:System.Windows.UIElement.TouchDown>事件<xref:System.Windows.UIElement>，操作邏輯呼叫<xref:System.Windows.UIElement.CaptureTouch%2A>方法，會產生<xref:System.Windows.UIElement.GotTouchCapture>事件。  
  
-   當<xref:System.Windows.UIElement.GotTouchCapture>發生，操作邏輯呼叫<xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=fullName>方法，會產生<xref:System.Windows.UIElement.ManipulationStarting>事件。  
  
-   當<xref:System.Windows.UIElement.TouchMove>事件發生時，會產生操作邏輯<xref:System.Windows.UIElement.ManipulationDelta>之前發生的事件<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件。  
  
-   當最後一個觸控裝置的項目便會引發<xref:System.Windows.UIElement.TouchUp>會產生事件時，操作邏輯<xref:System.Windows.UIElement.ManipulationInertiaStarting>事件。  
  
<a name="focus"></a>   
## <a name="focus"></a>焦點  
 有兩個主要的概念有關以專注於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]︰ 鍵盤焦點和邏輯焦點。  
  
### <a name="keyboard-focus"></a>鍵盤焦點  
 鍵盤焦點是指接收鍵盤輸入的項目。  只有一個項目能在整個桌面上具有鍵盤焦點。  在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，具有鍵盤焦點的項目會有<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>設為`true`。  靜態<xref:System.Windows.Input.Keyboard>方法<xref:System.Windows.Input.Keyboard.FocusedElement%2A>傳回目前擁有鍵盤焦點的項目。  
  
 可以取得鍵盤焦點，按下 tab 鍵的項目或按一下 將滑鼠停在特定項目，例如<xref:System.Windows.Controls.TextBox>。  鍵盤焦點也可以取得以程式設計方式使用<xref:System.Windows.Input.Keyboard.Focus%2A>方法<xref:System.Windows.Input.Keyboard>類別。  <xref:System.Windows.Input.Keyboard.Focus%2A>嘗試讓指定的項目鍵盤焦點。  傳回的項目<xref:System.Windows.Input.Keyboard.Focus%2A>是目前具有鍵盤焦點的項目。  
  
 若要取得鍵盤焦點的項目順序<xref:System.Windows.UIElement.Focusable%2A>屬性和<xref:System.Windows.UIElement.IsVisible%2A>屬性必須設為**true**。  部分類別，例如<xref:System.Windows.Controls.Panel>，有<xref:System.Windows.UIElement.Focusable%2A>設`false`預設; 因此，您可能要將此屬性設定為`true`如果您想要能夠取得焦點的項目。  
  
 下列範例會使用<xref:System.Windows.Input.Keyboard.Focus%2A>上設定鍵盤焦點<xref:System.Windows.Controls.Button>。  建議您將在應用程式中設定初始焦點位於<xref:System.Windows.FrameworkElement.Loaded>事件處理常式。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 如需鍵盤焦點的詳細資訊，請參閱[焦點概觀](../../../../docs/framework/wpf/advanced/focus-overview.md)。  
  
### <a name="logical-focus"></a>邏輯焦點  
 邏輯焦點是指<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=fullName>焦點範圍內。  可以有多個應用程式中，具有邏輯焦點的項目，但只能有一個特別強調範圍中的邏輯焦點的項目。  
  
 焦點領域是容器項目，可追蹤的<xref:System.Windows.Input.FocusManager.FocusedElement%2A>的範圍內。  當焦點離開焦點範圍時，焦點的項目會失去鍵盤焦點，但卻仍然保有邏輯焦點。  當焦點返回焦點範圍時，焦點的項目將會取得鍵盤焦點。  這可以讓多個焦點領域間變更鍵盤焦點，但可以確保當焦點範圍內的焦點的項目時傳回焦點會維持焦點的項目。  
  
 項目可以變成焦點範圍中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]藉由設定<xref:System.Windows.Input.FocusManager>附加屬性<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>至`true`，或藉由使用設定附加的屬性的程式碼中<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>方法。  
  
 下列範例會使<xref:System.Windows.Controls.StackPanel>焦點範圍設定成<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>附加屬性。  
  
 [!code-xml[MarkupSnippets#MarkupIsFocusScopeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 中的類別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]是預設的焦點範圍是<xref:System.Windows.Window>，<xref:System.Windows.Controls.Menu>，<xref:System.Windows.Controls.ToolBar>，和<xref:System.Windows.Controls.ContextMenu>。  
  
 具有鍵盤焦點的項目也會有邏輯焦點焦點領域，它屬於;因此，使用的項目上設定焦點<xref:System.Windows.Input.Keyboard.Focus%2A>方法<xref:System.Windows.Input.Keyboard>類別或基底項目類別會嘗試提供邏輯焦點的項目鍵盤焦點。  
  
 若要判斷焦點範圍內的焦點的項目，請使用<xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>。 若要變更焦點領域焦點的項目，請使用<xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>。  
  
 如需邏輯焦點的詳細資訊，請參閱[焦點概觀](../../../../docs/framework/wpf/advanced/focus-overview.md)。  
  
<a name="mouse_position"></a>   
## <a name="mouse-position"></a>滑鼠位置  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]輸入[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]提供有用的資訊關於座標空間。  例如，協調`(0,0)`左上角座標中，但在樹狀目錄中的項目左上方嗎？ 輸入目標的項目嗎？ 您附加至事件處理常式的項目嗎？ 或其他項目嗎？ 為了避免混淆，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]輸入[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]會要求您指定參考框架的當您使用透過滑鼠座標。 <xref:System.Windows.Input.Mouse.GetPosition%2A>方法會傳回指定的項目相對的滑鼠指標的座標。  
  
<a name="mouse_capture"></a>   
## <a name="mouse-capture"></a>滑鼠捕捉  
 滑鼠裝置特別會持有稱為滑鼠捕捉的強制回應特性。 滑鼠捕捉用來維護轉換輸入的狀態，拖放作業開始時，使螢幕上牽涉表面上的其他作業滑鼠指標的位置不一定會發生。 在拖曳時，使用者無法按一下不需中止並拖曳，讓大部分 mouseover 提示不適當，拖曳原點持有滑鼠捕捉時。 輸入的系統公開[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，可以判斷滑鼠捕捉的狀態，以及[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，可以強制滑鼠捕捉到特定的項目，或清除滑鼠捕捉的狀態。 如需拖放作業的詳細資訊，請參閱[拖放概觀](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)。  
  
<a name="commands"></a>   
## <a name="commands"></a>命令  
 命令可讓輸入更多語意比裝置輸入處理。  命令是簡單的指示詞，例如`Cut`， `Copy`， `Paste`，或`Open`。  命令可用於集中命令邏輯。  可能存取相同的命令，從<xref:System.Windows.Controls.Menu>上<xref:System.Windows.Controls.ToolBar>，或透過鍵盤快速鍵。 命令也提供一種機制，命令會變成無法使用時，停用的控制項。  
  
 <xref:System.Windows.Input.RoutedCommand>是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作<xref:System.Windows.Input.ICommand>。  當<xref:System.Windows.Input.RoutedCommand>執行時， <xref:System.Windows.Input.CommandManager.PreviewExecuted>和<xref:System.Windows.Input.CommandManager.Executed>的通道和向上傳遞項目樹狀結構，例如其他輸入的命令目標上引發事件。  如果未設定命令目標，具有鍵盤焦點的項目將會是命令目標。  執行命令的邏輯連接至<xref:System.Windows.Input.CommandBinding>。  當<xref:System.Windows.Input.CommandManager.Executed>事件到達<xref:System.Windows.Input.CommandBinding>該特定命令， <xref:System.Windows.Input.ExecutedRoutedEventHandler>上<xref:System.Windows.Input.CommandBinding>呼叫。  這個處理常式會執行命令的動作。  
  
 如需命令的詳細資訊，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供常用命令所組成的程式庫<xref:System.Windows.Input.ApplicationCommands>， <xref:System.Windows.Input.MediaCommands>， <xref:System.Windows.Input.ComponentCommands>， <xref:System.Windows.Input.NavigationCommands>，和<xref:System.Windows.Documents.EditingCommands>，或者您也可以定義自己。  
  
 下列範例示範如何設定<xref:System.Windows.Controls.MenuItem> ，因此按一下時它會叫用<xref:System.Windows.Input.ApplicationCommands.Paste%2A>命令<xref:System.Windows.Controls.TextBox>，此時是假設<xref:System.Windows.Controls.TextBox>擁有鍵盤焦點。  
  
 [!code-xml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
 如需有關命令中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
<a name="the_input_system_and_base_elements"></a>   
## <a name="the-input-system-and-base-elements"></a>輸入的系統和基底項目  
 輸入事件，例如所定義的附加事件<xref:System.Windows.Input.Mouse>，<xref:System.Windows.Input.Keyboard>，和<xref:System.Windows.Input.Stylus>類別時，輸入系統引發並插入點擊測試的視覺化樹狀結構，在執行階段為基礎的物件模型中的特定位置。  
  
 每一個事件，<xref:System.Windows.Input.Mouse>，<xref:System.Windows.Input.Keyboard>，和<xref:System.Windows.Input.Stylus>定義所附加的事件也重新公開由基底項目類別<xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>做為新的路由事件。 處理原始的附加的事件和重複使用的事件資料的類別所產生的基底的項目路由事件。  
  
 透過其基底項目輸入的事件實作的特定來源項目相關聯的輸入的事件時，它可以路由傳送事件路由的邏輯和視覺樹狀結構物件的組合為基礎，而且處理應用程式程式碼的其餘部分。  一般而言，是比較容易處理這些裝置相關輸入的事件上使用路由的事件<xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>，因為您可以使用更具直覺性事件處理常式中的語法這兩個[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和程式碼中。 您可以選擇處理初始化程序，相反地，附加的事件，但會遇到幾個問題︰ 可能會附加的事件標記為已處理的項目基底類別處理，您需要使用存取子方法，而不是真正的事件語法，才能將附加事件處理常式。  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>後續步驟  
 您現在有數個方式來處理輸入中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  您也應該擁有各種類型的輸入的事件和路由的事件機制使用改良了解[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
 其他資源可供使用，說明[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]架構項目及路由更詳細的事件。 下列概觀如需詳細資訊，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)，[焦點概觀](../../../../docs/framework/wpf/advanced/focus-overview.md)，[基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)， [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)，和[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 [焦點概觀](../../../../docs/framework/wpf/advanced/focus-overview.md)   
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [路由的事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [屬性](../../../../docs/framework/wpf/advanced/properties-wpf.md)