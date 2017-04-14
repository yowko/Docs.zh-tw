---
title: "基底項目概觀 | Microsoft Docs"
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
  - "基底項目"
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 基底項目概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的類別大多都是衍生自 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 文件中通稱為基底項目類別的四個類別。  這些類別包括 <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>、<xref:System.Windows.ContentElement> 和 <xref:System.Windows.FrameworkContentElement>。  <xref:System.Windows.DependencyObject> 類別也有關聯，因為它是 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 兩者的通用基底類別。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="base_apis"></a>   
## WPF 類別中的基底項目 API  
 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 都是衍生自 <xref:System.Windows.DependencyObject>，但兩者所經過的路徑稍有不同。  這個層級的區別牽涉到 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 在使用者介面中的使用方式，以及它們在應用程式中提供的用途。  <xref:System.Windows.UIElement> 的類別階層中也有 <xref:System.Windows.Media.Visual>，這個類別會公開 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 基礎的低階圖形支援。  <xref:System.Windows.Media.Visual> 會藉由定義獨立的矩形螢幕區域的方式，提供呈現架構。  實際上，<xref:System.Windows.UIElement> 適用的項目包括支援較大物件模型、用來呈現及配置成可描述成矩形螢幕區域的區域，而且其中的內容模型刻意保持較為開放，以容許不同的項目組合。  <xref:System.Windows.ContentElement> 不是衍生自 <xref:System.Windows.Media.Visual>；其模型是將供其他項目使用的 <xref:System.Windows.ContentElement>，例如接著將會解譯項目並產生完整的 <xref:System.Windows.Media.Visual> 供 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 使用的讀取器或檢視器。  某些 <xref:System.Windows.UIElement> 類別的目的是要當做內容裝載，以提供一個或多個 <xref:System.Windows.ContentElement> 類別 \(<xref:System.Windows.Controls.DocumentViewer> 是這種類別的範例\) 的裝載和呈現。  <xref:System.Windows.ContentElement> 可用來做為物件模型較小，而且較能處理 <xref:System.Windows.UIElement> 內可能裝載之文字、資訊或文件內容之項目的基底類別。  
  
### 架構層級和核心層級  
 <xref:System.Windows.UIElement> 可做為 <xref:System.Windows.FrameworkElement> 的基底類型，而 <xref:System.Windows.ContentElement> 則可做為 <xref:System.Windows.FrameworkContentElement> 的基底類別。  採用這種更高類別層級的原因是為了支援與 [WPF 架構層級](GTMT)不同的 [WPF 核心層級](GTMT)，而這種分割方式也存在於 PresentationCore 和 PresentationFramework 組件之間分割 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 的方式。  [WPF 架構層級](GTMT)提供較完整的解決方案，以滿足基本應用程式的需求，包括用於展示之配置管理員的實作 \(Implementation\)。  [WPF 核心層級](GTMT)提供一種方法，可以充分利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，但卻不會造成其他組件的額外負荷。  在大部分的一般應用程式開發案例中，這些層級之間的差別幾乎不會造成任何影響；此外，在一般情況下，您應該將 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 視為整體，而不需要理會 [WPF 架構層級](GTMT)和 [WPF 核心層級](GTMT)之間的差異。  如果您的應用程式設計選擇取代大量的 [WPF 架構層級](GTMT)功能，例如您的整體方案已經擁有自己的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 撰寫及配置實作時，您可能必須知道層級的差別。  
  
<a name="subclassing_elements"></a>   
## 選擇衍生來源項目  
 建立擴充 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的自訂類別時，最實用的方法是從其中一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別衍生，如此便可透過現有的類別階層，盡量取得您需要的功能。  本節列出三個最重要的項目類別所隨附的功能，以幫助您決定所要繼承的來源項目。  
  
 如果是實作控制項 \(實際上這也是衍生自 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別其中一個最常見的原因\)，您可能必須從本身即為實際控制項的類別或控制項系列基底類別衍生，或至少必須從 <xref:System.Windows.Controls.Control> 基底類別衍生。  如需部分指引和實際範例，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 如果您不是要建立控制項，而必須從階層中層級較高的類別衍生，下列章節可做為各個基底項目類別中定義之特性的指引。  
  
 若建立衍生自 <xref:System.Windows.DependencyObject> 的類別，則您繼承的功能將包括：  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 支援，以及一般的屬性系統支援。  
  
-   使用[相依性屬性](GTMT)和實作為[相依性屬性](GTMT)之[附加屬性](GTMT)的能力。  
  
 若建立衍生自 <xref:System.Windows.UIElement> 的類別，則除了 <xref:System.Windows.DependencyObject> 提供的功能之外，您還會繼承下列功能：  
  
-   動畫屬性值的基本支援。  如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
-   基本輸入事件支援，以及命令支援。  如需詳細資訊，請參閱[輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)和[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
-   可供覆寫的虛擬方法，用來為配置系統提供資訊。  
  
 若建立衍生自 <xref:System.Windows.FrameworkElement> 的類別，則除了 <xref:System.Windows.UIElement> 提供的功能之外，您還會繼承下列功能：  
  
-   樣式和腳本的支援。  如需詳細資訊，請參閱 <xref:System.Windows.Style> 和[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
-   資料繫結的支援。  如需詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
-   動態資源參考的支援。  如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
-   屬性值繼承 \(Inheritance\) 支援，以及中繼資料 \(Metadata\) 內有助於將屬性相關條件回報至架構服務 \(例如資料繫結、樣式或配置的架構實作\) 的其他旗標。  如需詳細資訊，請參閱 [架構屬性中繼資料](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)。  
  
-   [邏輯樹狀結構](GTMT)的概念。  如需詳細資訊，請參閱 [WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。  
  
-   配置系統的實際 [WPF 架構階層](GTMT)實作支援，包括可偵測影響配置之屬性變更的 <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> 覆寫。  
  
 若建立衍生自 <xref:System.Windows.ContentElement> 的類別，則除了 <xref:System.Windows.DependencyObject> 提供的功能之外，您還會繼承下列功能：  
  
-   動畫支援。  如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
-   基本輸入事件支援，以及命令支援。  如需詳細資訊，請參閱[輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)和[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
 若建立衍生自 <xref:System.Windows.FrameworkContentElement> 的類別，則除了 <xref:System.Windows.ContentElement> 提供的功能之外，您還會獲得下列功能：  
  
-   樣式和腳本的支援。  如需詳細資訊，請參閱 <xref:System.Windows.Style> 和[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
-   資料繫結的支援。  如需詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
-   動態資源參考的支援。  如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
-   屬性值繼承支援，以及中繼資料內有助於將屬性相關條件回報至架構服務 \(例如資料繫結、樣式或配置的架構實作\) 的其他旗標。  如需詳細資訊，請參閱 [架構屬性中繼資料](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)。  
  
-   您不會繼承配置系統修改 \(例如 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>\) 的存取權。  配置系統實作只能在 <xref:System.Windows.FrameworkElement> 上使用。  不過，您會繼承 <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> 覆寫，而此覆寫可以偵測影響配置的屬性變更，並將這些變更回報至任何內容裝載。  
  
 各種不同的類別都記載了內容模型。  如果您想找出適合做為衍生來源的類別，類別的內容模型是您應該考量的其中一項可能的因素。  如需詳細資訊，請參閱 [WPF 內容模型](../../../../docs/framework/wpf/controls/wpf-content-model.md)。  
  
<a name="other_base_classes"></a>   
## 其他基底類別  
  
### DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> 提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 執行緒模型的支援，而且能夠讓針對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式建立的所有物件與 <xref:System.Windows.Threading.Dispatcher> 產生關聯。  即使衍生來源不是 <xref:System.Windows.UIElement>、<xref:System.Windows.DependencyObject> 或 <xref:System.Windows.Media.Visual>，您也應該考慮從 <xref:System.Windows.Threading.DispatcherObject> 衍生，以取得這項執行緒模型支援。  如需詳細資訊，請參閱 [執行緒模型](../../../../docs/framework/wpf/advanced/threading-model.md)。  
  
### Visual  
 <xref:System.Windows.Media.Visual> 實作 2D 物件的概念，而這種概念通常必須在近似矩形的區域中以視覺方式呈現。  <xref:System.Windows.Media.Visual> 的實際呈現發生在其他類別中 \(不是獨立的 \(Self\-Contained\) 呈現\)，但是 <xref:System.Windows.Media.Visual> 類別則提供了呈現處理序在各種層級中使用的已知型別。  <xref:System.Windows.Media.Visual> 會實作點擊測試 \(Hit Testing\)，但是不會公開回報點擊測試結果的事件 \(這些事件位於 <xref:System.Windows.UIElement> 中\)。  如需詳細資訊，請參閱 [視覺分層程式設計](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md)。  
  
### Freezable  
 因為效能考量而需要有不可變的物件時，<xref:System.Windows.Freezable> 可以提供產生物件複本的方法，藉以在可變動的物件中模擬不變性。  <xref:System.Windows.Freezable> 型別提供了某些圖形項目 \(例如幾何和筆刷\) 以及動畫的一般基礎。  值得注意的是，<xref:System.Windows.Freezable> 並不是 <xref:System.Windows.Media.Visual>；它可以保留在套用 <xref:System.Windows.Freezable> 以填入其他物件的屬性值時，會變成子屬性的屬性，而這些子屬性可能會影響呈現效果。  如需詳細資訊，請參閱 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> 是 <xref:System.Windows.Freezable> 衍生類別 \(Derived Class\)，它會明確加入動畫控制層和某些公用程式成員，使目前顯示動畫的屬性可以跟非動畫的屬性有所區別。  
  
### 控制項  
 <xref:System.Windows.Controls.Control> 是稱為控制項或元件 \(根據不同的技術而定\) 之物件型別需要的基底類別。  一般而言，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控制項類別是直接代表 UI 控制項或積極參與控制項撰寫程序的類別。  <xref:System.Windows.Controls.Control> 啟用的主要功能是控制項樣板化。  
  
## 請參閱  
 <xref:System.Windows.Controls.Control>   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [WPF 架構](../../../../docs/framework/wpf/advanced/wpf-architecture.md)