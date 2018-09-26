---
title: 附加事件概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: c6a8b3b7355d315b83f859e7016018b56ade5484
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196339"
---
# <a name="attached-events-overview"></a>附加事件概觀
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義語言元件和稱為「附加事件」的事件類型。 附加事件的概念，讓您能新增特定事件的處理常式到任意項目，而不是實際定義或繼承事件的項目。 在此情況下，可能引發事件的物件和目的地處理執行個體都不會定義或以其他方式「擁有」事件。  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已閱讀[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)和 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>附加事件語法  
 附加事件具有 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法和程式碼撰寫模式，支援程式碼必須使用才能支援附加事件的使用。  
  
 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法中，附加事件的指定不只是依事件名稱，也依其擁有類型加上事件名稱，以點 (.) 分隔。 因為事件名稱以其擁有類型的名稱來限定，附加事件語法可讓任何附加事件附加至可以具現化的任何項目。  
  
 例如，下列是附加自訂 `NeedsCleaning` 附加事件之處理常式的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語法︰  
  
 [!code-xaml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 請注意 `aqua:` 前置詞，前置詞在此情況中是必要的，因為附加事件是來自自訂對應 xmlns 的自訂事件。  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>WPF 如何實作附加事件  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，附加事件都會受到<xref:System.Windows.RoutedEvent>欄位，並在引發之後路由傳送到樹狀結構。 一般而言，附加事件的來源 (引發事件的物件) 是系統或服務來源，因此執行引發事件之程式碼的物件不直接是項目樹狀結構的一部分。  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>附加事件的情節  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，附加事件會出現在特定功能區域沒有服務層級的抽象概念，例如靜態所啟用的事件<xref:System.Windows.Input.Mouse>類別或<xref:System.Windows.Controls.Validation>類別。 與服務互動或是使用服務的類別可以以附加事件語法使用事件，或者它們可以選擇將附加事件公開為路由事件，路由事件是類別整合服務功能的方式之一。  
  
 雖然 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義許多附加事件，您會直接使用或處理附加事件的情節非常有限。 一般而言，附加事件用於架構用途，但接著會轉送到非附加的 (由 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件「包裝函式」支援) 路由事件。  
  
 比方說，基礎附加事件<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>可以更輕鬆地處理任何給定<xref:System.Windows.UIElement>利用<xref:System.Windows.UIElement.MouseDown>上的<xref:System.Windows.UIElement>而不處理附加的事件語法中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]或程式碼。 附加事件在架構中有其用途，因為它可讓您在未來擴充輸入裝置。 假想的裝置只需要引發<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>模擬滑鼠輸入，並不需要衍生自<xref:System.Windows.Input.Mouse>若要這樣做。 不過，此情節牽涉到事件的程式碼處理，附加事件的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理與此情節無關。  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>在 WPF 中處理附加事件  
 處理附加事件的程序，以及您將撰寫的處理常式程式碼，基本上與路由事件一樣。  
  
 一般而言，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加事件與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 路由事件差異不大。 差異之處在於事件來源的方式，以及它由類別公開為成員的方式 (這也會影響 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理常式語法)。  
  
 不過，如先前所述，現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加事件並不特別適合在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中處理。 更常見的是，事件的目的是要在複合 (compositing) 中啟用報告狀態給父項目的複合項目，在此情況下，事件通常會在程式碼中引發，並依賴相關父類別中的類別處理。 比方說，項目內<xref:System.Windows.Controls.Primitives.Selector>預期會引發附加<xref:System.Windows.Controls.Primitives.Selector.Selected>處理事件，然後是類別<xref:System.Windows.Controls.Primitives.Selector>類別，並接著可能會藉由轉換<xref:System.Windows.Controls.Primitives.Selector>到不同的路由事件的類別<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. 如需路由事件與類別處理的詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>將您自己的附加事件定義為路由事件  
 如果您衍生自一般 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基底類別，您可以在類別中加入特定模式方法，並使用已在基底類別的公用程式方法，來實作自己的附加事件。  
  
 模式如下所示︰  
  
-   一種方法**新增*EventName*處理常式**具有兩個參數。 第一個參數必須識別事件，並識別出的事件必須符合的名稱***EventName***在方法名稱。 第二個參數是要新增的處理常式。 這個方法必須是`public`和`static`，且沒有傳回值。  
  
-   一種方法**移除*EventName*處理常式**具有兩個參數。 第一個參數必須識別事件，並識別出的事件必須符合的名稱***EventName***在方法名稱。 第二個參數是要移除的處理常式。 這個方法必須是`public`和`static`，且沒有傳回值。  
  
 **新增*EventName*處理常式**存取子方法可協助[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]時處理附加事件處理常式屬性宣告的項目。 **新增*EventName*處理常式**並**移除*EventName*處理常式**方法也可讓程式碼存取的事件處理常式存放區附加事件。  
  
 這種一般模式還不夠精確，無法實際實作在架構中，因為任何指定的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 讀取器實作都可能會有不同的方式來識別支援語言與架構中的基礎事件。 這是其中一個原因所[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]作為路由事件的實作附加事件、 要使用事件的識別項 (<xref:System.Windows.RoutedEvent>) 已經定義[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]事件系統。 此外，路由事件是 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 語言層級的附加事件概念的自然實作延伸模組。  
  
 **新增*EventName*處理常式**實作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]附加的事件組成包括呼叫<xref:System.Windows.UIElement.AddHandler%2A>與路由的事件和處理常式做為引數。  
  
 此實作策略和路由的事件系統一般會處理附加事件的限制設為<xref:System.Windows.UIElement>衍生的類別或<xref:System.Windows.ContentElement>衍生類別，因為只有這些類別有<xref:System.Windows.UIElement.AddHandler%2A>實作。  
  
 例如，下列程式碼定義擁有者類別 `Aquarium` 上的 `NeedsCleaning` 附加事件，並使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加事件策略，將附加事件宣告為路由事件。  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 請注意此方法用來建立附加的事件的識別項欄位， <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>，實際的方法一樣，用來登錄非附加路由的事件。 附加事件和路由事件全都註冊到集中式內部存放區。 此事件存放區實作促成了[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)中所討論的「事件即介面」概念考量。  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>引發 WPF 附加事件  
 您通常不需要從程式碼引發現有的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 已定義附加事件。 這些事件遵循一般 「 服務 」 概念模型，而且這類服務類別<xref:System.Windows.Input.InputManager>負責引發事件。  
  
 不過，如果您要定義自訂的附加的事件，依據[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為基礎的模型上附加事件<xref:System.Windows.RoutedEvent>，您可以使用<xref:System.Windows.UIElement.RaiseEvent%2A>引發任何附加的事件<xref:System.Windows.UIElement>或<xref:System.Windows.ContentElement>。 引發路由的事件 （不論附加） 需要您宣告為事件來源; 項目樹狀結構中的特定項目該來源會報告為<xref:System.Windows.UIElement.RaiseEvent%2A>呼叫端。 判斷樹狀結構中的哪個項目報告為來源是服務的責任  
  
## <a name="see-also"></a>另請參閱  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
