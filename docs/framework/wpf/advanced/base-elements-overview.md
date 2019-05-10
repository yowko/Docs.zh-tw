---
title: 基底項目概觀
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 6fc34c02ab1add0710b65da7d63f444e1628cbc6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64657366"
---
# <a name="base-elements-overview"></a>基底項目概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中有高百分比的類別衍生自 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 文件中通稱為基底項目類別的四個類別。 這些類別是<xref:System.Windows.UIElement>， <xref:System.Windows.FrameworkElement>， <xref:System.Windows.ContentElement>，和<xref:System.Windows.FrameworkContentElement>。 <xref:System.Windows.DependencyObject>類別也會相關，因為它是通用的基底類別，這兩者的<xref:System.Windows.UIElement>和 <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>WPF 類別中的基底項目 API  
 兩者<xref:System.Windows.UIElement>並<xref:System.Windows.ContentElement>衍生自<xref:System.Windows.DependencyObject>，透過略為不同的路徑。 在此層級分割會處理如何<xref:System.Windows.UIElement>或<xref:System.Windows.ContentElement>會用於使用者介面和應用程式中提供它們的目的。 <xref:System.Windows.UIElement> 也有<xref:System.Windows.Media.Visual>在其類別階層中，這是會公開較低層級圖形支援基礎類別[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。 <xref:System.Windows.Media.Visual> 藉由定義獨立矩形螢幕區域來提供轉譯架構。 在實務上，<xref:System.Windows.UIElement>是項目將會支援較大的物件模型，都將是用來轉譯和版面配置，可描述為矩形螢幕區域，和其中的內容模型是刻意更開放，以允許不同的區域項目組合。 <xref:System.Windows.ContentElement> 不是衍生自<xref:System.Windows.Media.Visual>; 其模型在於<xref:System.Windows.ContentElement>就可供其他用途，例如讀取器或接著解譯項目並產生完整的檢視器<xref:System.Windows.Media.Visual>的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]取用。 某些<xref:System.Windows.UIElement>類別要作為內容主機︰ 它們提供裝載和轉譯一或多個<xref:System.Windows.ContentElement>類別 (<xref:System.Windows.Controls.DocumentViewer>是這種類別的範例)。 <xref:System.Windows.ContentElement> 項目具有略小的物件模型的基底類別，並且更能處理的文字、 資訊或文件內容可能會裝載於當做<xref:System.Windows.UIElement>。  
  
### <a name="framework-level-and-core-level"></a>架構層級和核心層級  
 <xref:System.Windows.UIElement> 做為基底類別<xref:System.Windows.FrameworkElement>，並<xref:System.Windows.ContentElement>做為基底類別<xref:System.Windows.FrameworkContentElement>。 這個下一個層級之類別的原因是支援與 WPF 架構層級不同的 WPF 核心層級，而這項分割也存在於如何在 PresentationCore 與 PresentationFramework 組件之間分割 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。 WPF 架構層級提供基本應用程式需求的更完整解決方案，包括配置管理員的呈現實作。 WPF 核心層級提供一個方式來使用大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，而沒有額外組件的額外負荷。 在大部分一般應用程式開發情節中，這些層級之間的區分非常罕見，而且一般而言，您應該將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 視為整體，而不需要顧慮 WPF 架構層級與 WPF 核心層級之間的差異。 如果您的應用程式設計選擇取代相當數量的 WPF 架構層級功能，例如，整體方案已有自己的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 組合和配置實作，則可能需要知道層級差異。  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>選擇要從中衍生的項目  
 建立可延伸 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的自訂類別的最實用方法，是衍生自透過現有類別階層盡可能善用所需功能的其中一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別。 本節列出隨附三個最重要項目類別的功能，協助您決定要從中繼承的類別。  
  
 如果您正在實作控制項，這實際上是衍生自的更常見原因之一[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別，您可能想要衍生自為實用控制項，控制項系列基底類別，類別，或在從最低<xref:System.Windows.Controls.Control>基底類別。 如需某些指引和實用範例，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 如果您不要建立控制項，而且需要衍生自階層中較高的類別，則下列各節是作為在每個基底項目類別中定義特性的指南。  
  
 如果您建立衍生自類別<xref:System.Windows.DependencyObject>，還會繼承下列功能：  
  
- <xref:System.Windows.DependencyObject.GetValue%2A> 和<xref:System.Windows.DependencyObject.SetValue%2A>支援，以及一般屬性系統支援。  
  
- 可以使用相依性屬性以及實作為相依性屬性的附加屬性。  
  
 如果您建立衍生自類別<xref:System.Windows.UIElement>，您會繼承下列功能除了提供<xref:System.Windows.DependencyObject>:  
  
- 動畫屬性值的基本支援。 如需詳細資訊，請參閱 [動畫概觀](../graphics-multimedia/animation-overview.md)。  
  
- 基本輸入事件支援和命令支援。 如需詳細資訊，請參閱[輸入概觀](input-overview.md)和[命令概觀](commanding-overview.md)。  
  
- 可覆寫以將資訊提供給配置系統的虛擬方法。  
  
 如果您建立衍生自類別<xref:System.Windows.FrameworkElement>，您會繼承下列功能除了提供<xref:System.Windows.UIElement>:  
  
- 樣式和分鏡腳本的支援。 如需詳細資訊，請參閱 <<c0> <xref:System.Windows.Style> 並[分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)。  
  
- 資料繫結的支援。 如需詳細資訊，請參閱 [資料繫結概觀](../data/data-binding-overview.md)。  
  
- 動態資源參考的支援。 如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。  
  
- 屬性值繼承支援，以及中繼資料中協助向架構服務報告屬性條件的其他旗標，例如資料繫結、樣式或配置架構實作。 如需詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
- 邏輯樹狀結構的概念。 如需詳細資訊，請參閱 [WPF 中的樹狀結構](trees-in-wpf.md)。  
  
- 版面配置系統的實用 WPF 架構層級實作支援包括<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>屬性可影響配置覆寫，可以偵測變更。  
  
 如果您建立衍生自類別<xref:System.Windows.ContentElement>，您會繼承下列功能除了提供<xref:System.Windows.DependencyObject>:  
  
- 動畫的支援。 如需詳細資訊，請參閱 [動畫概觀](../graphics-multimedia/animation-overview.md)。  
  
- 基本輸入事件支援和命令支援。 如需詳細資訊，請參閱[輸入概觀](input-overview.md)和[命令概觀](commanding-overview.md)。  
  
 如果您建立衍生自類別<xref:System.Windows.FrameworkContentElement>，取得所提供的下列功能<xref:System.Windows.ContentElement>:  
  
- 樣式和分鏡腳本的支援。 如需詳細資訊，請參閱 <<c0> <xref:System.Windows.Style> 並[動畫概觀](../graphics-multimedia/animation-overview.md)。  
  
- 資料繫結的支援。 如需詳細資訊，請參閱 [資料繫結概觀](../data/data-binding-overview.md)。  
  
- 動態資源參考的支援。 如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。  
  
- 屬性值繼承支援，以及中繼資料中協助向架構服務報告屬性條件的其他旗標，例如資料繫結、樣式或配置架構實作。 如需詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
- 您不會繼承配置系統修改的存取 (例如<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>)。 配置系統實作才有提供的<xref:System.Windows.FrameworkElement>。 不過，您可以繼承<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>覆寫，可以偵測影響版面配置和回報這些向任何內容主機的屬性變更。  
  
 會記錄各種類別的內容模型。 如果您想要尋找從中衍生的適當類別，則類別的內容模型是您應該考慮的一個可能因素。 如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>其他基底類別  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> 提供的支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]執行緒模型，並啟用所有的物件建立[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]相關聯的應用程式<xref:System.Windows.Threading.Dispatcher>。 即使您不是衍生自<xref:System.Windows.UIElement>， <xref:System.Windows.DependencyObject>，或<xref:System.Windows.Media.Visual>，您應該考慮衍生自<xref:System.Windows.Threading.DispatcherObject>以取得此執行緒模型支援。 如需詳細資訊，請參閱[執行緒模型](threading-model.md)。  
  
### <a name="visual"></a>視覺效果  
 <xref:System.Windows.Media.Visual> 會實作 2D 物件一般需要大約矩形區域中的視覺呈現的概念。 實際轉譯<xref:System.Windows.Media.Visual>發生在其他類別 （它不是自封式） 中，但<xref:System.Windows.Media.Visual>類別提供各種層級的轉譯處理序使用的已知型別。 <xref:System.Windows.Media.Visual> 實作點擊測試，但它不會公開報表點擊測試肯定的事件 (這兩者位於<xref:System.Windows.UIElement>)。 如需詳細資訊，請參閱[視覺分層程式設計](../graphics-multimedia/visual-layer-programming.md)。  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> 提供方法來產生物件的複本，需要或想要基於效能考量不可變物件時，會模擬可變物件中的不變性。 <xref:System.Windows.Freezable>類型提供的通用基礎特定圖形項目，例如幾何和筆刷，以及動畫。 值得注意的是，<xref:System.Windows.Freezable>不是<xref:System.Windows.Media.Visual>; 它可以保存變成子屬性的屬性時<xref:System.Windows.Freezable>套用至填滿屬性值的另一個物件，而且這些子屬性可能會影響轉譯。 如需詳細資訊，請參閱 [Freezable 物件概觀](freezable-objects-overview.md)。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> 是<xref:System.Windows.Freezable>衍生特別著重於新增動畫控制項層和一些公用程式成員，因此可以區分目前動畫的屬性的區分內容的類別。  
  
### <a name="control"></a>控制項  
 <xref:System.Windows.Controls.Control> 是預期的基底類別類型，為 ad-hoc 控制項或元件，根據的技術。 一般而言，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項類別是直接代表 UI 控制項或緊密參與控制項組合的類別。 主要功能，<xref:System.Windows.Controls.Control>啟用是控制項範本。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Control>
- [相依性屬性概觀](dependency-properties-overview.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [WPF 架構](wpf-architecture.md)
