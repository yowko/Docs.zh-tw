---
title: 相依性屬性概觀
description: 受到 WPF 屬性系統支援的屬性則稱為相依性屬性。 本概觀描述 WPF 屬性系統和相依性屬性的功能。
ms.date: 06/06/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], attached
- properties [WPF], overview
- styles [WPF]
- attached properties [WPF]
- data binding [WPF]
- dependency properties [WPF]
- resources [WPF], references to
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
ms.openlocfilehash: 0d336a55ee849ea3e9584cdcfd87e5d6c4befe25
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374644"
---
# <a name="dependency-properties-overview"></a>相依性屬性概觀

Windows Presentation Foundation (WPF) 提供一組可用來擴充類型的[屬性](../../../standard/base-types/common-type-system.md#Properties)功能之服務。 整體而言，這些服務通常稱為 WPF 屬性系統。 受到 WPF 屬性系統支援的屬性則稱為相依性屬性。 本概觀描述 WPF 屬性系統和相依性屬性的功能。 這包括如何在 XAML 和程式碼中使用現有的相依性屬性。 本概觀也介紹相依性屬性的特製化層面，例如相依性屬性中繼資料，以及如何在自訂類別中建立您自己的相依性屬性。

## <a name="prerequisites"></a>必要條件
本主題假設您對 NET 類型系統和物件導向程式設計有基本的認識。 為了遵循本主題中的範例，您也應該了解 XAML 並知道如何撰寫 WPF 應用程式。 如需詳細資訊，請參閱[逐步解說：我第一個 WPF 桌面應用程式](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="dependency-properties-and-clr-properties"></a>相依性屬性與 CLR 屬性
 在 WPF 中，屬性通常會公開為標準 .NET [屬性](../../../standard/base-types/common-type-system.md#Properties)。 在基本層級，您可以和這些屬性直接互動，永遠不知道它們會實作為相依性屬性。 但您應該要熟悉 WPF 屬性系統的部分或全部功能，以便可以利用這些功能。

相依性屬性的目的是提供一個方式，根據其他輸入的值來計算屬性值。 這些其他輸入可能包含系統屬性 (例如佈景主題和使用者喜好設定)、Just-In-Time 屬性決策機制 (例如資料繫結和動畫/腳本)、多用途的範本 (例如資源和樣式)，或者透過父子關聯性與項目樹狀結構中的其他項目知道的值。 此外，您也可以實作相依性屬性，提供獨立的驗證、預設值、監視其他屬性變更的回撥，以及可根據潛在執行階段資訊強制轉型屬性值的系統。 衍生的類別也可以透過覆寫相依性屬性中繼資料，而不是覆寫現有屬性的實際實作或建立新屬性，來變更現有屬性的某些特定特性。

在 SDK 參考中，您可以在該屬性 Managed 參考頁面出現相依性屬性資訊區段時，識別哪個屬性是相依性屬性。 相依性屬性資訊區段包含該相依性屬性的 <xref:System.Windows.DependencyProperty> 識別碼欄位連結，也包含為該屬性、依類別層級覆寫資訊及其他詳細資料設定的中繼資料選項清單。

## <a name="dependency-properties-back-clr-properties"></a>相依性屬性支援 CLR 屬性
相依性屬性和 WPF 屬性系統透過提供支援屬性的類型來擴充屬性功能，作為支援有私用欄位屬性之標準模式的替代實作。 這個類型的名稱為 <xref:System.Windows.DependencyProperty>。 另一個定義 WPF 屬性系統的重要類型為 <xref:System.Windows.DependencyObject>。 <xref:System.Windows.DependencyObject> 定義可以登錄並擁有相依性屬性的基底類別。

以下列出與相依性屬性搭配使用的術語：

- **相依性屬性：** 此屬性，做為後盾<xref:System.Windows.DependencyProperty>。

- **相依性屬性識別項：** A<xref:System.Windows.DependencyProperty>執行個體，這是註冊的相依性屬性時，取得做為傳回值，然後儲存為類別的靜態成員。 此識別碼用為與 WPF 屬性系統互動的多個 API 參數。

- **CLR 「 包裝函式 」:** 實際取得及設定屬性的實作。 這些實作透過在 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 呼叫中使用相依性屬性識別碼，為使用 WPF 屬性系統的屬性提供支援。

下例定義 `IsSpinning` 相依性屬性，並向其支援的屬性顯示 <xref:System.Windows.DependencyProperty> 識別碼關聯性。

[!code-csharp[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
屬性的命名慣例及其支援的 <xref:System.Windows.DependencyProperty> 欄位很重要。 欄位名稱一律是屬性名稱，後綴尾碼 `Property`。 如需此慣例及其原因的詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。  

## <a name="setting-property-values"></a>設定屬性值
您可以在程式碼或 XAML 中設定屬性。

### <a name="setting-property-values-in-xaml"></a>在 XAML 中設定屬性值 
下列 XAML 範例將按鈕的背景色彩指定為紅色。 本範例示範 XAML 屬性的簡單字串值，它的類型由 WPF XAML 剖析器在產生的程式碼中轉換成 WPF 類型 (<xref:System.Windows.Media.Color>，透過 <xref:System.Windows.Media.SolidColorBrush>)。

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML 支援各種設定屬性的語法形式。 特定屬性要使用哪種語法，取決於屬性使用的實值型別以及其他因素，例如有無類型轉換器。 如需屬性設定之 XAML 語法的詳細資訊，請參閱 [XAML 概觀 (WPF)](xaml-overview-wpf.md) 和 [XAML 語法詳細資料](xaml-syntax-in-detail.md)。

下列 XAML 範例為非屬性語法的範例，示範另一個按鈕的背景。 這一次不是設定簡單的純色，而是將背景設定為映像，將表示該映像和該映像來源的項目指定為巢狀項目的屬性。 這是屬性項目語法的範例。

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>在程式碼中設定屬性
 在程式碼中設定相依性屬性值，通常只要呼叫 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」公開的 set 實作即可。

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

取得屬性值，基本上也就是呼叫 get「包裝函式」實作︰

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

您也可以直接呼叫屬性系統 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A>。 如果您使用現有的屬性，這通常非必要 (包裝函式更方便，也更好公開開發人員工具屬性)，但某些情況下直接呼叫 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 更適當。

屬性也可以在 XAML 中設定，稍後再於程式碼中透過程式碼後置存取。 如需詳細資訊，請參閱 [WPF 中的程式碼後置和 XAML](code-behind-and-xaml-in-wpf.md)。

## <a name="property-functionality-provided-by-a-dependency-property"></a>相依性屬性提供的屬性功能
相對於欄位支援屬性，相依性屬性提供能擴充屬性功能的功能。 通常，這類功能代表或支援下列特定功能其中之一：

- [資源](#resources)

- [資料繫結](#data-binding)

- [樣式](#styles)

- [動畫](#animations)

- [中繼資料覆寫](#metadata-overrides)

- [屬性值繼承](#property-value-inheritance)

- [WPF 設計工具整合](#wpf-designer-integration)

### <a name="resources"></a>資源
您可以參考資源來設定相依性屬性值。 資源通常指定為 `Resources` 頁面根項目或應用程式的屬性值 (這些位置最方便存取資源)。 下例示範如何定義 <xref:System.Windows.Media.SolidColorBrush> 資源。

[!code-xaml[PropertiesOvwSupport#ResourcesResource](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

定義資源之後，您即可參考資源並用它提供屬性值︰

[!code-xaml[PropertiesOvwSupport#ResourcesReference](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

這個特定的資源稱之為 [DynamicResource 標記延伸](dynamicresource-markup-extension.md) (在 WPF XAML 中，您可以使用靜態或動態資源參考)。 若要使用動態資源參考，您必須設定相依性屬性，因此它是由 WPF 屬性系統啟用的專門動態資源參考使用。 如需詳細資訊，請參閱 [XAML 資源](xaml-resources.md)。

> [!NOTE]
> 資源視為區域數值，這表示如果您設定另一個區域數值，就會排除資源參考。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。

### <a name="data-binding"></a>資料繫結
相依性屬性可以透過資料繫結參考值。 資料繫結的運作是透過 XAML 中的特定標記延伸語法，或程式碼中的 <xref:System.Windows.Data.Binding> 物件。 使用資料繫結，最後一個屬性值決定會延後到執行階段，此時已自資料來源取得值。

下列範例會使用在 XAML 中宣告的繫結來設定 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性。 繫結使用繼承的資料內容和 <xref:System.Windows.Data.XmlDataProvider> 資料來源 (未顯示)。 繫結本身會指定資料來源內 <xref:System.Windows.Data.Binding.XPath%2A> 所需的來源屬性。

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> 繫結視為區域數值，這表示如果您設定另一個區域數值，就會排除繫結。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。

為了產生資料繫結作業的 <xref:System.Windows.DependencyObject> 來源屬性值中變更之通知，相依性屬性或 <xref:System.Windows.DependencyObject> 類別並不原生支援 <xref:System.ComponentModel.INotifyPropertyChanged>。 如需如何建立資料繫結所用屬性的詳細資訊，該資料繫結可以報告資料繫結目標的變更，請參閱[資料繫結概觀](../data/data-binding-overview.md)。

### <a name="styles"></a>樣式
樣式和範本是使用相依性屬性的兩大激勵案例。 樣式特別適用於設定定義應用程式 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的屬性。 樣式通常會定義為 XAML 中的資源。 樣式與屬性系統互動，因為它們通常包含特定屬性的 "setter"，以及根據另一個屬性的即時值變更屬性值的「觸發程序」。

下列範例會建立非常簡單的樣式 (該樣式將在 <xref:System.Windows.FrameworkElement.Resources%2A> 字典內部中定義，未顯示)，然後將該樣式直接套用於 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.FrameworkElement.Style%2A> 屬性。 樣式中的 setter 會將樣式 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 屬性設定為綠色。

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

如需詳細資訊，請參閱 [設定樣式和範本](../controls/styling-and-templating.md)。

### <a name="animations"></a>Animations
相依性屬性可以動畫方式顯示。 套用並執行動畫時，動畫顯示值的運作優先於屬性可能執行的任何值 (例如本機值)。

下列範例在 <xref:System.Windows.Controls.Button> 屬性上以動畫方式顯示 <xref:System.Windows.Controls.Control.Background%2A> (技術上來說，<xref:System.Windows.Controls.Control.Background%2A> 透過使用屬性項目語法來指定空白 <xref:System.Windows.Media.SolidColorBrush> 為 <xref:System.Windows.Controls.Control.Background%2A>，然後該 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性是直接繪製的屬性)。

[!code-xaml[PropertiesOvwSupport#MiniAnimate](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

如需可動畫顯示屬性的詳細資訊，請參閱[動畫概觀](../graphics-multimedia/animation-overview.md)及[腳本概觀](../graphics-multimedia/storyboards-overview.md)。

### <a name="metadata-overrides"></a>中繼資料覆寫
當您衍生自最初登錄相依性屬性的類別時，您可以覆寫該屬性的中繼資料，變更相依性屬性的特定行為。 覆寫依賴於 <xref:System.Windows.DependencyProperty> 識別碼的中繼資料。 覆寫中繼資料不需要重新實作屬性。 屬性系統會以原生方式處理中繼資料變更。每個類別都可能依每個類型，保存繼承自基底類別之所有屬性的個別中繼資料。

下列範例會覆寫相依性屬性的中繼資料 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>。 覆寫此特定相依性屬性中繼資料，是建立可使用佈景主題預設樣式控制項之實作模式的一部分。

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

如需覆寫或取得屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](dependency-property-metadata.md)。

### <a name="property-value-inheritance"></a>屬性值繼承
項目可以繼承物件樹狀結構中的父代相依性屬性值。

> [!NOTE]
> 並非所有的相依性屬性都會啟用屬性值繼承行為，因為繼承的計算時間會影響效能。 通常只有建議屬性值繼承為適當的特定案例屬性才會啟用屬性值繼。 您可以在＜SDK 參考＞的**相依性屬性資訊**一節中查看相依性屬性，判斷該相依性屬性是否有繼承行為。

下例會示範繫結並設定指定繫結來源的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性，之前的繫結範例未示範。 子物件中的任何後續繫結都不需要指定來源，即可使用父系 <xref:System.Windows.Controls.StackPanel> 物件中來自 <xref:System.Windows.FrameworkElement.DataContext%2A> 的繼承值。 (或者，子物件可以改為選擇直接在 <xref:System.Windows.Data.Binding> 中指定自己的 <xref:System.Windows.FrameworkElement.DataContext%2A> 或 <xref:System.Windows.Data.Binding.Source%2A>，並故意不使用其繫結的資料內容之繼承值。)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

如需詳細資訊，請參閱[屬性值繼承](property-value-inheritance.md)。

### <a name="wpf-designer-integration"></a>WPF 設計工具整合
有實作為相依性屬性之屬性的自訂控制項會獲得適當的 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 支援。 其中一例就是能夠使用 [屬性] 視窗編輯直接和附加的相依性屬性。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。

## <a name="dependency-property-value-precedence"></a>相依性屬性值優先順序
當您取得相依性屬性的值時，您就可能取得一個值，此值原透過參與 WPF 屬性系統的任何其他屬性型輸入來設定在該屬性上。 相依性屬性值有優先順序，所以屬性如何取得其值的各種案例才能以可預測的方式互動。

請參考下列範例。 此範例包含適用於所有按鈕及其 <xref:System.Windows.Controls.Control.Background%2A> 屬性的樣式，但也會指定一個具有本機設定 <xref:System.Windows.Controls.Control.Background%2A> 值的按鈕。

> [!NOTE]
> SDK 文件在討論相依性屬性時，偶爾會使用詞彙「區域數值」或「本機設定值」。 本機設定值是一個屬性值，其直接設定在程式碼的物件執行個體上，或作為 XAML 項目上的屬性。  
  
基本上，第一個按鈕會設定兩次屬性，但只套用一個值：有最高優先順序的值。 本機設定值有最高優先順序 (執行中的動畫除外，但本例中未套用任何動畫)，因此第一個按鈕的背景使用本機設定值，而不使用樣式 setter 值。 第二個按鈕沒有區域數值 (樣式 setter 有最高的優先順序)，因此該按鈕的背景來自樣式 setter。

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>為什麼會有相依性屬性優先順序？
通常您不會希望樣式一律套用樣式，甚至隱藏個別項目的本機設定值 (否則一般很難使用樣式或項目)。 因此，來自樣式的值運作優先順序比本機設定值低。 如需更完整的相依性屬性清單及相依性屬性有效值的可能來源，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。

> [!NOTE]
> 許多屬性是定義在相依性屬性的 WPF 項目上。 大體上，屬性過去只有在需要支援至少一個屬性系統啟用的案例時，才會實作為相依性屬性︰資料繫結、樣式、動畫、預設值支援、繼承、附加屬性或失效。

## <a name="learning-more-about-dependency-properties"></a>深入了解相依性屬性  

- 附加屬性是支援 XAML 特殊語法的屬性類型。 附加屬性通常和 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性沒有 1:1 對應，而且不一定是相依性屬性。 附加屬性的一般用途是允許子項目向父項目回報屬性值，即使父項目和子項目未同時擁有列為類別成員的該屬性。 一個主要案例是使子項目能夠告知父系應如何在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中將其呈現；如需範例，請參閱 <xref:System.Windows.Controls.DockPanel.Dock%2A> 或 <xref:System.Windows.Controls.Canvas.Left%2A>。 如需詳細資訊，請參閱[附加屬性概觀](attached-properties-overview.md)。

- 元件開發人員或應用程式開發人員可能希望建立自己的相依性屬性，以便啟用資料繫結或樣式支援等功能，或用於失效和值的強制型轉支援。 如需詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。

- 相依性屬性通常應該視為公用屬性，任何可存取執行個體的呼叫端皆可存取或至少可探索它們。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。

## <a name="see-also"></a>另請參閱
- [自訂相依性屬性](custom-dependency-properties.md)
- [唯讀相依性屬性](read-only-dependency-properties.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [WPF 架構](wpf-architecture.md)
