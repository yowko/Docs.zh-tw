---
title: 預覽事件
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 75165df94aa8b508ef85cf970933efb98b9d62ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211386"
---
# <a name="preview-events"></a>預覽事件
預覽事件，也就是通道事件，都是路由的事件的路由方向會從應用程式根目錄來引發事件，並報告為事件資料來源的項目傳送的位置。 並非所有的事件案例支援，或需要預覽事件;本主題描述的情況下，預覽事件存在，應用程式或元件應如何處理它們和建立自訂元件或類別中的預覽事件，可能適合的情況。  
  
## <a name="preview-events-and-input"></a>預覽事件和輸入  
 當您處理一般情況下，事件會謹慎的預覽將事件標記事件中處理資料。 以外的其他處理任何項目上的 Preview 事件引發 （報告為中的事件資料的來源項目） 的項目效果的機會先處理它所產生的事件時未提供項目。 有時候這是所要的結果，尤其是有問題的項目存在於控制項的複合關聯性。  
  
 輸入事件具體而言，預覽事件也共用事件資料執行個體與對等的事件反昇事件。 如果您使用預覽事件的類別處理常式來處理輸入的事件標記時，不會叫用事件反昇輸入的事件類別處理常式。 或者，如果您使用的預覽事件執行個體處理常式標記處理的事件，事件反昇事件的處理常式將會不通常會叫用。 可以註冊類別處理常式或執行個體處理常式，或附加要叫用即使事件已標示為已處理，但該技術不常使用的選項。  
  
 如需類別處理，以及它如何與預覽事件相關聯的詳細資訊，請參閱[路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)。  
  
### <a name="working-around-event-suppression-by-controls"></a>處理控制項的事件隱藏項目  
 通常用預覽事件的一個案例是複合控制項的輸入事件的處理。 有時候，控制項作者隱藏特定事件來自從其控制，或許是為了替換成元件定義的事件，提供詳細資訊，或更具體的行為。 比方說， [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>隱藏<xref:System.Windows.UIElement.MouseLeftButtonDown>並<xref:System.Windows.UIElement.MouseRightButtonDown>所引發的事件反昇事件<xref:System.Windows.Controls.Button>或複合項目以擷取滑鼠並引發<xref:System.Windows.Controls.Primitives.ButtonBase.Click>一律由所引發的事件<xref:System.Windows.Controls.Button>本身。 事件和其資料還是會繼續在路由中，但是由於<xref:System.Windows.Controls.Button>將做為事件資料標示<xref:System.Windows.RoutedEventArgs.Handled%2A>，特別指出應中之事件的處理常式`handledEventsToo`案例會叫用。  針對您的應用程式的根目錄的其他項目仍然希望機會先處理控制隱藏的事件，有一個替代方法是附加的程式碼中的處理常式`handledEventsToo`指定為`true`。 但通常較簡單的技術就是變更路由的方向，您可預覽對等的輸入事件的控制代碼。 比方說，如果控制項隱藏<xref:System.Windows.UIElement.MouseLeftButtonDown>，嘗試附加的處理常式<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>改。 這項技術僅適用於基底項目輸入事件這類<xref:System.Windows.UIElement.MouseLeftButtonDown>。 這些輸入的事件使用通道/事件反昇組、 引發這兩個事件，並共用事件資料。  
  
 每一種方法有副作用或限制。 處理將預覽事件的副作用是處理事件，此時可能會停用來處理事件反昇事件，預期的處理常式，因此其限制是，它通常不是個不錯的主意，處理而仍在 Previ 將事件標記路由的新功能組件。 限制`handledEventsToo`技巧是，您無法指定`handledEventsToo`中的處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]做為屬性，您必須註冊事件處理常式程式碼中取得要附加的處理常式的所在的物件參考的項目之後。  
  
## <a name="see-also"></a>另請參閱

- [將路由事件標記為已處理以及類別處理](marking-routed-events-as-handled-and-class-handling.md)
- [路由事件概觀](routed-events-overview.md)
