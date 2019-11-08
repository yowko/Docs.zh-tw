---
title: 基底項目概觀
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 823c81bf6b21b88d719503387a68ce6e7d643d61
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740921"
---
# <a name="base-elements-overview"></a>基底項目概觀
在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，高百分比的類別衍生自四個類別，SDK 檔中通常稱為基底元素類別。 這些類別是 <xref:System.Windows.UIElement>、<xref:System.Windows.FrameworkElement>、<xref:System.Windows.ContentElement>和 <xref:System.Windows.FrameworkContentElement>。 <xref:System.Windows.DependencyObject> 類別也是相關的，因為它是 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 的通用基類。  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>WPF 類別中的基底項目 API  
 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 都是衍生自 <xref:System.Windows.DependencyObject>，透過有點不同的路徑。 此層級的分割會處理如何在使用者介面中使用 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement>，以及它們在應用程式中的用途。 <xref:System.Windows.UIElement> 在其類別階層中也有 <xref:System.Windows.Media.Visual>，這是一個類別，會公開 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]基礎的較低層級圖形支援。 <xref:System.Windows.Media.Visual> 藉由定義獨立的矩形螢幕區域來提供轉譯架構。 在實務上，<xref:System.Windows.UIElement> 適用于將支援較大物件模型的元素，其目的是要呈現和配置到可描述為矩形螢幕區域的區域，以及內容模型刻意更開放的位置，以允許不同的組合元素的。 <xref:System.Windows.ContentElement> 不是衍生自 <xref:System.Windows.Media.Visual>;其模型是 <xref:System.Windows.ContentElement> 會由其他專案取用，例如讀取器或檢視器，接著會解讀元素並產生完整的 <xref:System.Windows.Media.Visual> 供 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 取用。 某些 <xref:System.Windows.UIElement> 類別的用途是內容主機：它們提供一或多個 <xref:System.Windows.ContentElement> 類別的裝載和呈現（<xref:System.Windows.Controls.DocumentViewer> 是這類類別的範例）。 <xref:System.Windows.ContentElement> 可用來做為具有較小物件模型之元素的基類，並且更能解決可能裝載于 <xref:System.Windows.UIElement>中的文字、資訊或檔內容。  
  
### <a name="framework-level-and-core-level"></a>架構層級和核心層級  
 <xref:System.Windows.UIElement> 做為 <xref:System.Windows.FrameworkElement>的基類，<xref:System.Windows.ContentElement> 做為 <xref:System.Windows.FrameworkContentElement>的基類。 下一個類別層級的原因，是為了支援與 WPF 架構層級不同的 WPF 核心層級，而此劃分也存在於 Api 在 PresentationCore 和 PresentationFramework 元件之間的劃分方式。 WPF 架構層級提供基本應用程式需求的更完整解決方案，包括配置管理員的呈現實作。 WPF 核心層級提供一個方式來使用大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，而沒有額外組件的額外負荷。 這些層級之間的區別非常少對大部分的一般應用程式開發案例很重要，而且一般而言，您應該將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的 Api 視為整體，而不會擔心 WPF 架構層級與 WPF 核心層級之間的差異。 如果您的應用程式設計選擇取代相當數量的 WPF 架構層級功能，例如，整體方案已有自己的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 組合和配置實作，則可能需要知道層級差異。  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>選擇要從中衍生的項目  
 建立可延伸 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的自訂類別的最實用方法，是衍生自透過現有類別階層盡可能善用所需功能的其中一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別。 本節列出隨附三個最重要項目類別的功能，協助您決定要從中繼承的類別。  
  
 如果您要執行的控制項是從 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別衍生的較常見原因之一，您可能會想要從實作為實務控制項的類別、控制項系列基類，或至少從 <xref:System.Windows.Controls.Control> 基類衍生。 如需某些指引和實用範例，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 如果您不要建立控制項，而且需要衍生自階層中較高的類別，則下列各節是作為在每個基底項目類別中定義特性的指南。  
  
 如果您建立衍生自 <xref:System.Windows.DependencyObject>的類別，則會繼承下列功能：  
  
- <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 支援，以及一般的屬性系統支援。  
  
- 可以使用相依性屬性以及實作為相依性屬性的附加屬性。  
  
 如果您建立衍生自 <xref:System.Windows.UIElement>的類別，除了 <xref:System.Windows.DependencyObject>所提供的功能之外，還會繼承下列功能：  
  
- 動畫屬性值的基本支援。 如需詳細資訊，請參閱 [動畫概觀](../graphics-multimedia/animation-overview.md)。  
  
- 基本輸入事件支援和命令支援。 如需詳細資訊，請參閱[輸入概觀](input-overview.md)和[命令概觀](commanding-overview.md)。  
  
- 可覆寫以將資訊提供給配置系統的虛擬方法。  
  
 如果您建立衍生自 <xref:System.Windows.FrameworkElement>的類別，除了 <xref:System.Windows.UIElement>所提供的功能之外，還會繼承下列功能：  
  
- 樣式和分鏡腳本的支援。 如需詳細資訊，請參閱 <xref:System.Windows.Style> 和分鏡腳本[總覽](../graphics-multimedia/storyboards-overview.md)。  
  
- 資料繫結的支援。 如需詳細資訊，請參閱 [資料繫結概觀](../data/data-binding-overview.md)。  
  
- 動態資源參考的支援。 如需詳細資訊，請參閱 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
- 屬性值繼承支援，以及中繼資料中協助向架構服務報告屬性條件的其他旗標，例如資料繫結、樣式或配置架構實作。 如需詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
- 邏輯樹狀結構的概念。 如需詳細資訊，請參閱 [WPF 中的樹狀結構](trees-in-wpf.md)。  
  
- 支援配置系統的實際 WPF 架構層級實作為，包括可偵測影響版面配置之屬性變更的 <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> 覆寫。  
  
 如果您建立衍生自 <xref:System.Windows.ContentElement>的類別，除了 <xref:System.Windows.DependencyObject>所提供的功能之外，還會繼承下列功能：  
  
- 動畫的支援。 如需詳細資訊，請參閱 [動畫概觀](../graphics-multimedia/animation-overview.md)。  
  
- 基本輸入事件支援和命令支援。 如需詳細資訊，請參閱[輸入概觀](input-overview.md)和[命令概觀](commanding-overview.md)。  
  
 如果您建立衍生自 <xref:System.Windows.FrameworkContentElement>的類別，除了 <xref:System.Windows.ContentElement>提供的功能之外，還會取得下列功能：  
  
- 樣式和分鏡腳本的支援。 如需詳細資訊，請參閱 <xref:System.Windows.Style> 和[動畫總覽](../graphics-multimedia/animation-overview.md)。  
  
- 資料繫結的支援。 如需詳細資訊，請參閱 [資料繫結概觀](../data/data-binding-overview.md)。  
  
- 動態資源參考的支援。 如需詳細資訊，請參閱 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
- 屬性值繼承支援，以及中繼資料中協助向架構服務報告屬性條件的其他旗標，例如資料繫結、樣式或配置架構實作。 如需詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
- 您不會繼承配置系統修改的存取權（例如 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>）。 版面配置系統的執行僅適用于 <xref:System.Windows.FrameworkElement>。 不過，您會繼承可偵測影響配置之屬性變更的 <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> 覆寫，並將其報告給任何內容主機。  
  
 會記錄各種類別的內容模型。 如果您想要尋找從中衍生的適當類別，則類別的內容模型是您應該考慮的一個可能因素。 如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>其他基底類別  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> 提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 執行緒模型的支援，並可讓 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式所建立的所有物件與 <xref:System.Windows.Threading.Dispatcher>相關聯。 即使您不是從 <xref:System.Windows.UIElement>、<xref:System.Windows.DependencyObject>或 <xref:System.Windows.Media.Visual>衍生，您也應該考慮從 <xref:System.Windows.Threading.DispatcherObject> 衍生，以便取得此執行緒模型支援。 如需詳細資訊，請參閱[執行緒模型](threading-model.md)。  
  
### <a name="visual"></a>視覺效果  
 <xref:System.Windows.Media.Visual> 會實作為2D 物件的概念，通常需要在大約的矩形區域中進行視覺化呈現。 <xref:System.Windows.Media.Visual> 的實際轉譯會發生在其他類別（不是獨立的）中，但是 <xref:System.Windows.Media.Visual> 類別會提供在各種層級呈現程式所使用的已知型別。 <xref:System.Windows.Media.Visual> 會執行點擊測試，但不會公開報告點擊測試的事件（這些都是在 <xref:System.Windows.UIElement>中）。 如需詳細資訊，請參閱[視覺分層程式設計](../graphics-multimedia/visual-layer-programming.md)。  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> 藉由提供在不變物件需要時產生物件複本，或基於效能考慮而需要的方法，來模擬可變物件中的不可變性。 <xref:System.Windows.Freezable> 類型會針對某些圖形元素（例如幾何和筆刷）和動畫提供通用的基礎。 值得注意的是，<xref:System.Windows.Freezable> 不是 <xref:System.Windows.Media.Visual>;當套用 <xref:System.Windows.Freezable> 來填滿另一個物件的屬性值，而且這些子屬性可能會影響轉譯時，它可以保留變成子屬性的屬性。 如需詳細資訊，請參閱 [Freezable 物件概觀](freezable-objects-overview.md)。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> 是一個 <xref:System.Windows.Freezable> 的衍生類別，專門新增動畫控制層和一些公用程式成員，讓目前的動畫屬性可以與 nonanimated 屬性區別。  
  
### <a name="control"></a>控制項  
 <xref:System.Windows.Controls.Control> 是所各種之物件類型的預期基類，其稱為控制項或元件，視技術而定。 一般而言，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項類別是直接代表 UI 控制項或緊密參與控制項組合的類別。 <xref:System.Windows.Controls.Control> 啟用的主要功能是控制項樣板化。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Controls.Control>
- [相依性屬性概觀](dependency-properties-overview.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [WPF 架構](wpf-architecture.md)
