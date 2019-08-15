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
ms.openlocfilehash: 40e7bd34388bec06cd8a7c3610599d814aef101f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038148"
---
# <a name="attached-events-overview"></a>附加事件概觀

Extensible Application Markup Language (XAML) 會定義語言元件和事件種類, 稱為*附加事件*。 附加事件的概念，讓您能新增特定事件的處理常式到任意項目，而不是實際定義或繼承事件的項目。 在此情況下，可能引發事件的物件和目的地處理執行個體都不會定義或以其他方式「擁有」事件。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已閱讀[路由事件概觀](routed-events-overview.md)和 [XAML 概觀 (WPF)](xaml-overview-wpf.md)。  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>附加事件語法  
 附加的事件具有 XAML 語法和程式碼撰寫模式, 必須由支援程式碼使用, 才能支援附加的事件使用方式。  
  
 在 XAML 語法中, 附加事件不只是由其事件名稱所指定, 而是由其擁有類型加上事件名稱 (以點 (.) 分隔)。 因為事件名稱以其擁有類型的名稱來限定，附加事件語法可讓任何附加事件附加至可以具現化的任何項目。  
  
 例如, 下列是用於附加自訂`NeedsCleaning`附加事件之處理常式的 XAML 語法:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 請注意 `aqua:` 前置詞，前置詞在此情況中是必要的，因為附加事件是來自自訂對應 xmlns 的自訂事件。  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>WPF 如何實作附加事件

在 WPF 中, 附加事件是由<xref:System.Windows.RoutedEvent>欄位所支援, 而且會在引發之後透過樹狀結構進行路由。 一般而言，附加事件的來源 (引發事件的物件) 是系統或服務來源，因此執行引發事件之程式碼的物件不直接是項目樹狀結構的一部分。  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>附加事件的情節  
 在 WPF 中, 附加事件會出現在有服務層級抽象的特定功能區域中, 例如, 針對靜態<xref:System.Windows.Input.Mouse>類別<xref:System.Windows.Controls.Validation>或類別所啟用的事件。 與服務互動或是使用服務的類別可以以附加事件語法使用事件，或者它們可以選擇將附加事件公開為路由事件，路由事件是類別整合服務功能的方式之一。  
  
 雖然 WPF 會定義數個附加事件, 但您會直接使用或處理附加事件的情況非常有限。 一般而言, 附加事件會提供架構用途, 但接著會轉送到非附加的 (使用 CLR 事件「包裝函式」) 路由事件。  
  
 例如, 基礎附加<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>事件可以在任何指定<xref:System.Windows.UIElement>的上使用<xref:System.Windows.UIElement.MouseDown>來處理, 而不是在<xref:System.Windows.UIElement> XAML 或程式碼中處理附加事件語法。 附加事件在架構中有其用途，因為它可讓您在未來擴充輸入裝置。 假設裝置只需要引發<xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType>才能模擬滑鼠輸入, 而且不需要衍生自<xref:System.Windows.Input.Mouse>來這麼做。 不過, 此案例牽涉到事件的程式碼處理, 而附加事件的 XAML 處理與此案例無關。  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>在 WPF 中處理附加事件  
 處理附加事件的程序，以及您將撰寫的處理常式程式碼，基本上與路由事件一樣。  
  
 一般而言, WPF 附加事件與 WPF 路由事件的差異並不大。 其差異在於事件的來源, 以及類別如何公開為成員 (這也會影響 XAML 處理常式語法)。  
  
 不過, 如先前所述, 現有的 WPF 附加事件並不特別適用于 WPF 中的處理。 更常見的是，事件的目的是要在複合 (compositing) 中啟用報告狀態給父項目的複合項目，在此情況下，事件通常會在程式碼中引發，並依賴相關父類別中的類別處理。 比方<xref:System.Windows.Controls.Primitives.Selector>說, 中的專案應該會引發附加<xref:System.Windows.Controls.Primitives.Selector.Selected>事件, 這是類別所處理<xref:System.Windows.Controls.Primitives.Selector>的類別, 然後可能由<xref:System.Windows.Controls.Primitives.Selector>類別轉換成不同的路由事件, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. 如需路由事件與類別處理的詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)。  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>將您自己的附加事件定義為路由事件  
 如果您是從通用 WPF 基類衍生, 您可以在類別中包含特定模式方法, 並使用已存在於基類上的公用程式方法, 來實作為附加事件。  
  
 模式如下所示︰  
  
- 方法會新增具有兩個參數的 __*事件名稱*處理常式__。 第一個參數是要加入事件處理常式的實例。 第二個參數是要加入的事件處理常式。 方法必須是`public`和, `static`而且沒有傳回值。  
  
- 方法會移除具有兩個參數的 __*事件名稱*處理常式__。 第一個參數是要從中移除事件處理常式的實例。 第二個參數是要移除的事件處理常式。 方法必須是`public`和, `static`而且沒有傳回值。  
  
 在元素上宣告附加事件處理常式屬性時, 「__新增事件*名稱*處理常式__」存取子方法可加速 XAML 處理。 「__加入事件*名稱*處理常式__」和「__移除事件*名稱*」處理常式__方法也可讓您存取附加事件的事件處理常式存放區。  
  
 這種一般模式還不夠精確, 無法用於架構中的實際執行, 因為任何指定的 XAML 讀取器執行可能會有不同的配置來識別支援語言和架構中的基礎事件。 這是 WPF 將附加事件實作為路由事件的原因之一;用於事件的識別碼 (<xref:System.Windows.RoutedEvent>) 已由 WPF 事件系統定義。 此外, 路由事件是附加事件之 XAML 語言層級概念的自然執行延伸模組。  
  
 WPF 附加事件的「__加入*事件名稱*」處理常式__, 包含以<xref:System.Windows.UIElement.AddHandler%2A>路由事件和處理常式做為引數呼叫。  
  
 這項實策略和路由事件系統通常會將附加事件的處理限制為<xref:System.Windows.UIElement>衍生類別或<xref:System.Windows.ContentElement>衍生類別, 因為只有那些類別具有<xref:System.Windows.UIElement.AddHandler%2A> 「執行」 (class)。  
  
 例如, 下列程式碼會使用將`NeedsCleaning`附加事件宣告為路由事件`Aquarium`的 WPF 附加事件策略, 定義擁有者類別上的附加事件。  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 請注意, 用來建立附加事件識別碼欄位<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>的方法, 實際上是用來註冊非附加路由事件的相同方法。 附加事件和路由事件全都註冊到集中式內部存放區。 此事件存放區實作促成了[路由事件概觀](routed-events-overview.md)中所討論的「事件即介面」概念考量。  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>引發 WPF 附加事件  
 您通常不需要從程式碼引發現有的 WPF 定義附加事件。 這些事件會遵循一般的「服務」概念模型, 而服務類別 ( <xref:System.Windows.Input.InputManager>例如) 則負責引發事件。  
  
 不過, 如果您要<xref:System.Windows.RoutedEvent>根據在上建立基關聯事件的 WPF 模型來定義自訂附加事件, 您可以使用<xref:System.Windows.UIElement.RaiseEvent%2A>從任何<xref:System.Windows.UIElement>或<xref:System.Windows.ContentElement>引發附加事件。 引發路由事件 (已附加) 需要您在專案樹狀結構中宣告特定元素做為事件來源;該來源會回報為<xref:System.Windows.UIElement.RaiseEvent%2A>呼叫端。 判斷樹狀結構中的哪個項目報告為來源是服務的責任  
  
## <a name="see-also"></a>另請參閱

- [路由事件概觀](routed-events-overview.md)
- [XAML 語法詳細資料](xaml-syntax-in-detail.md)
- [WPF 的 XAML 和自訂類別](xaml-and-custom-classes-for-wpf.md)
