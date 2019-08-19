---
title: Visual Basic 和 WPF 事件處理
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 4ff006099dd2fa706cb575eec18e135d6e74ad46
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972325"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Visual Basic 和 WPF 事件處理
特別針對 Microsoft Visual Basic .net 語言, 您可以使用特定`Handles`語言的關鍵字, 將事件處理常式與實例產生關聯, 而不是附加具有屬性的事件處理常式或<xref:System.Windows.UIElement.AddHandler%2A>使用方法。 不過，將處理常式附加至執行個體的 `Handles` 技術有一些限制，因為 `Handles` 語法無法支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系統中某些特定的路由事件功能。  
  
## <a name="using-handles-in-a-wpf-application"></a>在 WPF 應用程式中使用「Handles」  
 使用 `Handles` 連線到執行個體和事件的事件處理常式全需定義於執行個體的部分類別宣告中，這也是透過元素上的屬性值所指派之事件處理常式的需求。 您只能針對頁面`Handles`上<xref:System.Windows.FrameworkContentElement.Name%2A>具有屬性值 (或已宣告[x:Name](../../xaml-services/x-name-directive.md)指示詞) 的元素指定。 這是因為中<xref:System.Windows.FrameworkContentElement.Name%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的會建立支援*實例*所需的實例參考, 這是`Handles`語法所需的事件參考格式。 唯一可以用於`Handles` <xref:System.Windows.FrameworkContentElement.Name%2A>沒有參考的專案, 是定義部分類別的根項目實例。  
  
 您可以將相同的處理常式指派給多個元素，方法是在 `Handles` 之後使用逗號來隔開 Instance.Event 參考。  
  
 您可以使用 `Handles`，將多個處理常式指派給同一個 Instance.Event 參考。 不要為 `Handles` 參考中指定處理常式的順序指派任何重要性；您應該假設可以任何順序叫用處理同一個事件的處理常式。  
  
 若要移除`Handles`在宣告中以加入的處理常式, 您可以呼叫<xref:System.Windows.UIElement.RemoveHandler%2A>。  
  
 您可以使用 `Handles` 來附加路由事件的處理常式，只要您將處理常式附加至會在其成員資料表中定義要處理事件的執行個體。 針對路由事件, 附加`Handles`的處理常式會遵循與附加為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性的處理常式相同的路由規則, 或<xref:System.Windows.UIElement.AddHandler%2A>具有的一般簽章。 這表示, 如果事件已標示為已處理 (事件<xref:System.Windows.RoutedEventArgs.Handled%2A>資料中的屬性為`True`), 則不會叫用`Handles`附加的處理常式來回應該事件實例。 事件可能是透過路由中另一個元素上的執行個體處理常式標示為已處理，或是透過路由上目前元素或先前元素上所處理的類別來標示。 對於支援配對的通道/事件反昇事件的輸入事件，通道路由可能已將事件配對標示已處理。 如需路由事件的詳細資訊，請參閱[路由事件概觀](routed-events-overview.md)。  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>加入處理常式的「Handles」限制  
 `Handles` 不能參考附加事件的處理常式。 您必須針對該附加事件使用 `add` 存取子方法，或 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的 typename.eventname 事件屬性。 如需詳細資訊，請參閱[路由事件概觀](routed-events-overview.md)。  
  
 針對路由事件，您只能使用 `Handles` 來指派執行個體的處理常式，該事件存在於執行個體成員資料表中。 不過，透過路由事件，父元素通常可以是來自子元素之事件的接聽程式，即使父元素的成員資料表中沒有該事件也一樣。 在屬性語法中，您可以透過 typename.membername 屬性格式來指定此動作，此格式會限定哪種類型實際上會定義您想要處理的事件。 例如, 父代`Page` (未`Click`定義事件) 可以藉由指派表單`Button.Click`中的屬性處理常式來接聽按鈕點擊事件。 但是 `Handles` 不支援 typename.membername 格式，因為它必須支援衝突的 Instance.Event 格式。 如需詳細資訊，請參閱[路由事件概觀](routed-events-overview.md)。  
  
 `Handles` 無法附加要針對已經標示為已處理之事件叫用的處理常式。 相反地, 您必須使用程式碼並`handledEventsToo`呼叫<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>的多載。  
  
> [!NOTE]
>  當您為 XAML `Handles`中的相同事件指定事件處理常式時, 請勿在 Visual Basic 程式碼中使用語法。 在這個情況下，會呼叫事件處理常式兩次。  
  
## <a name="how-wpf-implements-handles-functionality"></a>WPF 如何實作「Handles」功能  
 編譯[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]頁面時, 中繼檔案會宣告頁面上具有<xref:System.Windows.FrameworkContentElement.Name%2A>屬性集 (或已宣告 [x:Name 指示詞](../../xaml-services/x-name-directive.md)) 之每個元素的`Friend``WithEvents`參考。 每個具名執行個體可能都是可透過 `Handles` 指派給處理常式的元素。  
  
> [!NOTE]
>  在[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]中, IntelliSense 可以顯示可在頁面中`Handles`參考哪些元素的完成。 不過，這可能需要採取一次編譯傳遞，讓中繼檔案可以填入所有的 `Friends` 參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.UIElement.AddHandler%2A>
- [將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)
- [路由事件概觀](routed-events-overview.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
