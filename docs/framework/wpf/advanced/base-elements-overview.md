---
title: 基底項目概觀
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: f6519675ebf3624152e1077e7582f04e38b1dce9
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644044"
---
# <a name="base-elements-overview"></a>基底項目概觀
中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]較高的類是從 SDK 文檔中通常稱為基元素類的四個類派生的。 這些類別是<xref:System.Windows.UIElement><xref:System.Windows.FrameworkElement>,<xref:System.Windows.ContentElement><xref:System.Windows.FrameworkContentElement>與 。 類<xref:System.Windows.DependencyObject>也是相關的,因為它是兩<xref:System.Windows.UIElement>個 和<xref:System.Windows.ContentElement>  

<a name="base_apis"></a>
## <a name="base-element-apis-in-wpf-classes"></a>WPF 類別中的基底項目 API  
 和<xref:System.Windows.UIElement><xref:System.Windows.ContentElement>都派生<xref:System.Windows.DependencyObject>自 ,通過稍有不同途徑。 此級別的拆分涉及用戶介面中的<xref:System.Windows.UIElement>使用<xref:System.Windows.ContentElement>或 ,以及它們在應用程式中的作用。 <xref:System.Windows.UIElement>其類<xref:System.Windows.Media.Visual>層次結構中也有,該層次結構是公開底層較低級別的圖形支援的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]類 。 <xref:System.Windows.Media.Visual>通過定義獨立的矩形螢幕區域提供渲染框架。 實際上,<xref:System.Windows.UIElement>對於支援較大物件模型的元素,用於渲染和佈局到可描述為矩形螢幕區域的區域,以及內容模型有意更開放的區域,以允許不同的元素組合。 <xref:System.Windows.ContentElement>不派生自<xref:System.Windows.Media.Visual>。其模型是,將<xref:System.Windows.ContentElement>被其他的東西(如讀取器或查看器)使用,然後解釋元素並生成<xref:System.Windows.Media.Visual>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]要消耗的完整元素。 某些<xref:System.Windows.UIElement>類別旨在成為內容主機:它們為一個或<xref:System.Windows.ContentElement>多個 類提供宿主和<xref:System.Windows.Controls.DocumentViewer>呈現( 是此類類的範例)。 <xref:System.Windows.ContentElement>用作物件模型稍小的元素的基類,用於更多內容,這些元素可能託管在<xref:System.Windows.UIElement>中。  
  
### <a name="framework-level-and-core-level"></a>架構層級和核心層級  
 <xref:System.Windows.UIElement>用作 的基<xref:System.Windows.FrameworkElement>類<xref:System.Windows.ContentElement>,<xref:System.Windows.FrameworkContentElement>並用作 的基類。 下一級類的原因是支援獨立於 WPF 框架級別的 WPF 核心級別,此劃分還存在於如何在表示核心程式集和表示框架程式集之間劃分 API 中。 WPF 架構層級提供基本應用程式需求的更完整解決方案，包括配置管理員的呈現實作。 WPF 核心層級提供一個方式來使用大部分的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，而沒有額外組件的額外負荷。 這些級別之間的區別很少對大多數典型的應用程式開發方案很重要,通常您應該將[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API 視為一個整體,而不應關注 WPF 框架級別和 WPF 核心級別之間的區別。 如果您的應用程式設計選擇取代相當數量的 WPF 架構層級功能，例如，整體方案已有自己的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 組合和配置實作，則可能需要知道層級差異。  
  
<a name="subclassing_elements"></a>
## <a name="choosing-which-element-to-derive-from"></a>選擇要從中衍生的項目  
 建立可延伸 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的自訂類別的最實用方法，是衍生自透過現有類別階層盡可能善用所需功能的其中一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別。 本節列出隨附三個最重要項目類別的功能，協助您決定要從中繼承的類別。  
  
 如果要實現控件(這確實是從類派生的更常見原因之一[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]),則可能需要從實際控件、控件族基類或至少<xref:System.Windows.Controls.Control>從 基類派生的類。 如需某些指引和實用範例，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 如果您不要建立控制項，而且需要衍生自階層中較高的類別，則下列各節是作為在每個基底項目類別中定義特性的指南。  
  
 如果建立派生自<xref:System.Windows.DependencyObject>的類,則繼承以下功能:  
  
- <xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>和支援,以及一般財產系統支援。  
  
- 可以使用相依性屬性以及實作為相依性屬性的附加屬性。  
  
 如果建立的類派生自<xref:System.Windows.UIElement>,<xref:System.Windows.DependencyObject>除了 提供 的功能外,還繼承了以下功能:  
  
- 動畫屬性值的基本支援。 有關詳細資訊,請參閱[動畫概述](../graphics-multimedia/animation-overview.md)。  
  
- 基本輸入事件支援和命令支援。 如需詳細資訊，請參閱[輸入概觀](input-overview.md)和[命令概觀](commanding-overview.md)。  
  
- 可覆寫以將資訊提供給配置系統的虛擬方法。  
  
 如果建立的類派生自<xref:System.Windows.FrameworkElement>,<xref:System.Windows.UIElement>除了 提供 的功能外,還繼承了以下功能:  
  
- 樣式和分鏡腳本的支援。 有關詳細資訊,請參閱<xref:System.Windows.Style>和[情節提要概述](../graphics-multimedia/storyboards-overview.md)。  
  
- 資料繫結的支援。 有關詳細資訊,請參閱[資料繫結此概述](../../../desktop-wpf/data/data-binding-overview.md)。  
  
- 動態資源參考的支援。 如需詳細資訊，請參閱 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
- 屬性值繼承支援，以及中繼資料中協助向架構服務報告屬性條件的其他旗標，例如資料繫結、樣式或配置架構實作。 如需詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
- 邏輯樹狀結構的概念。 如需詳細資訊，請參閱 [WPF 中的樹狀結構](trees-in-wpf.md)。  
  
- 支援佈局系統的實際 WPF 框架級實現,包括可以檢測<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>影響佈局 的屬性更改的重寫。  
  
 如果建立的類派生自<xref:System.Windows.ContentElement>,<xref:System.Windows.DependencyObject>除了 提供 的功能外,還繼承了以下功能:  
  
- 動畫的支援。 有關詳細資訊,請參閱[動畫概述](../graphics-multimedia/animation-overview.md)。  
  
- 基本輸入事件支援和命令支援。 如需詳細資訊，請參閱[輸入概觀](input-overview.md)和[命令概觀](commanding-overview.md)。  
  
 如果建立的類派生自<xref:System.Windows.FrameworkContentElement>,<xref:System.Windows.ContentElement>除了 提供的功能外,還獲取以下功能:  
  
- 樣式和分鏡腳本的支援。 有關詳細資訊,請參閱<xref:System.Windows.Style>和[動畫概述](../graphics-multimedia/animation-overview.md)。  
  
- 資料繫結的支援。 有關詳細資訊,請參閱[資料繫結此概述](../../../desktop-wpf/data/data-binding-overview.md)。  
  
- 動態資源參考的支援。 如需詳細資訊，請參閱 [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
- 屬性值繼承支援，以及中繼資料中協助向架構服務報告屬性條件的其他旗標，例如資料繫結、樣式或配置架構實作。 如需詳細資訊，請參閱[架構屬性中繼資料](framework-property-metadata.md)。  
  
- 不繼承對佈局系統修改(如<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>) 的訪問。 布局系統實現僅在上<xref:System.Windows.FrameworkElement>可用。 但是,您繼承了一<xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>個重寫,該重寫可以檢測對影響佈局的屬性的更改,並將這些更改報告給任何內容主機。  
  
 會記錄各種類別的內容模型。 如果您想要尋找從中衍生的適當類別，則類別的內容模型是您應該考慮的一個可能因素。 如需詳細資訊，請參閱 [WPF 內容模型](../controls/wpf-content-model.md)。  
  
<a name="other_base_classes"></a>
## <a name="other-base-classes"></a>其他基底類別  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject>支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]線程模型,並使[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為 應用程式創建的所有物件都與相關<xref:System.Windows.Threading.Dispatcher>聯。 即使您不<xref:System.Windows.UIElement>派生於<xref:System.Windows.DependencyObject>、<xref:System.Windows.Media.Visual>或, 也應考慮<xref:System.Windows.Threading.DispatcherObject>派生, 以便獲得此線程模型支援。 如需詳細資訊，請參閱[執行緒模型](threading-model.md)。  
  
### <a name="visual"></a>視覺效果  
 <xref:System.Windows.Media.Visual>實現 2D 物件的概念,該物件通常需要在大致矩形區域中進行可視化表示。 實際<xref:System.Windows.Media.Visual>呈現發生在其他類中(它不是自包含的),<xref:System.Windows.Media.Visual>但 該類提供了一個已知類型,該類型由不同級別的渲染過程使用。 <xref:System.Windows.Media.Visual>實現命中測試,但不會公開報告命中測試陽性的事件(這些事件在<xref:System.Windows.UIElement>中)。 如需詳細資訊，請參閱[視覺分層程式設計](../graphics-multimedia/visual-layer-programming.md)。  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable>通過提供在性能原因需要或需要不可變物件時生成物件副本的方法,類比可變物件中的不變性。 該<xref:System.Windows.Freezable>類型為某些圖形元素(如幾何和畫筆以及動畫)提供了通用基礎。 值得注意的是,a<xref:System.Windows.Freezable>不是<xref:System.Windows.Media.Visual>;它可以保存在應用 以填充另<xref:System.Windows.Freezable>一 個物件的屬性值時成為子屬性的屬性,並且這些子屬性可能會影響渲染。 如需詳細資訊，請參閱 [Freezable 物件概觀](freezable-objects-overview.md)。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>是一<xref:System.Windows.Freezable>個派生類,專門添加動畫控制層和一些實用程式成員,以便當前動畫屬性可以區分為非動畫屬性。  
  
### <a name="control"></a>控制  
 <xref:System.Windows.Controls.Control>是各種稱為控件或元件的物件類型的預期基類,具體取決於技術。 一般而言，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項類別是直接代表 UI 控制項或緊密參與控制項組合的類別。 <xref:System.Windows.Controls.Control>啟用的主要功能是控制範本化。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Control>
- [相依性屬性概觀](dependency-properties-overview.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [WPF 架構](wpf-architecture.md)
