---
title: 相依性屬性概觀
description: WPF 屬性系統所支援的屬性稱為相依性屬性。 本概觀說明 WPF 屬性系統和相依性屬性的功能。
ms.date: 03/30/2017
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
ms.openlocfilehash: 196e858c52c06c96d652209e86039bfcc81a785a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dependency-properties-overview"></a>相依性屬性概觀

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供一組可用來擴充 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性功能的服務。 整體而言，這些服務通常稱為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統。 受到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統支援的屬性則稱為相依性屬性。 本概觀說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統和相依性屬性的功能。 這包括如何在 XAML 和程式碼中使用現有的相依性屬性。 本概觀也介紹相依性屬性的特製化層面，例如相依性屬性中繼資料，以及如何在自訂類別中建立您自己的相依性屬性。

## <a name="prerequisites"></a>必要條件
本主題假設您對 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 和物件導向程式設計有基本的認識。 為了解本主題中的範例，您也應該了解 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。 如需詳細資訊，請參閱[逐步解說： 第一個 WPF 桌面應用程式](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="dependency-properties-and-clr-properties"></a>相依性屬性和 CLR 屬性
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，屬性通常會公開為 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性。 在基本層級，您可以和這些屬性直接互動，永遠不知道它們會實作為相依性屬性。 但您應該要熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的部分或全部功能，以便可以利用這些功能。

相依性屬性的目的是提供一個方式，根據其他輸入的值來計算屬性值。 這些其他輸入可能包含系統屬性 (例如佈景主題和使用者喜好設定)、Just-In-Time 屬性決策機制 (例如資料繫結和動畫/腳本)、多用途的範本 (例如資源和樣式)，或者透過父子關聯性與項目樹狀結構中的其他項目知道的值。 此外，您也可以實作相依性屬性，提供獨立的驗證、預設值、監視其他屬性變更的回撥，以及可根據潛在執行階段資訊強制轉型屬性值的系統。 衍生的類別也可以透過覆寫相依性屬性中繼資料，而不是覆寫現有屬性的實際實作或建立新屬性，來變更現有屬性的某些特定特性。

在 SDK 參考中，您可以在該屬性 Managed 參考頁面出現相依性屬性資訊區段時，識別哪個屬性是相依性屬性。 相依性屬性資訊區段包含的連結<xref:System.Windows.DependencyProperty>識別項欄位的相依性屬性，而且也包含設定該屬性，每個類別中覆寫資訊，以及其他詳細資料的中繼資料 選項的清單。

## <a name="dependency-properties-back-clr-properties"></a>相依性屬性回 CLR 屬性
相依性屬性和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統透過提供支援屬性的類型來擴充屬性功能，作為支援有私用欄位屬性之標準模式的替代實作。 此類型的名稱是<xref:System.Windows.DependencyProperty>。 其他重要定義的型別[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性系統<xref:System.Windows.DependencyObject>。 <xref:System.Windows.DependencyObject> 定義可以註冊及擁有相依性屬性的基底類別。

以下是本 [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] 文件討論相依性屬性時使用的術語總結︰

- **相依性屬性：**屬性，並受到<xref:System.Windows.DependencyProperty>。

- **相依性屬性的識別項：** A<xref:System.Windows.DependencyProperty>執行個體，這是註冊相依性屬性時，取得做為傳回值，並儲存為類別的靜態成員。 此識別碼用為與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統互動之多個 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 的參數。

- **CLR「包裝函式」：**實際取得及設定屬性的實作。 這些實作結合的使用中的相依性屬性的識別項<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>呼叫，因此能提供屬性使用的備份[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]屬性系統。

下列範例會定義`IsSpinning`相依性屬性，並顯示的關係<xref:System.Windows.DependencyProperty>到它所支援之屬性的識別項。

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
屬性和其支援的命名慣例<xref:System.Windows.DependencyProperty>欄位很重要。 欄位名稱一律是屬性名稱，後綴尾碼 `Property`。 如需此慣例及其原因的詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  

## <a name="setting-property-values"></a>設定屬性值
您可以在程式碼或 XAML 中設定屬性。

### <a name="setting-property-values-in-xaml"></a>在 XAML 中設定屬性值 
下列 XAML 範例將按鈕的背景色彩指定為紅色。 這個範例將說明其中 XAML 屬性的簡單字串值是型別轉換成 WPF XAML 剖析器的情況[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類型 ( <xref:System.Windows.Media.Color>，藉由<xref:System.Windows.Media.SolidColorBrush>) 產生的程式碼中。

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML 支援各種設定屬性的語法形式。 特定屬性要使用哪種語法，取決於屬性使用的實值型別以及其他因素，例如有無類型轉換器。 如需屬性設定之 XAML 語法的詳細資訊，請參閱 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) 和 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。

下列 XAML 範例為非屬性語法的範例，示範另一個按鈕的背景。 這一次不是設定簡單的純色，而是將背景設定為映像，將表示該映像和該映像來源的項目指定為巢狀項目的屬性。 這是屬性項目語法的範例。

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>在程式碼中設定屬性
 在程式碼中設定相依性屬性值，通常只要呼叫 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」公開的 set 實作即可。

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

取得屬性值，基本上也就是呼叫 get「包裝函式」實作︰

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

您也可以呼叫屬性系統[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>直接。 如果您使用現有的屬性，這通常非必要 (包裝函式更方便，也更好公開開發人員工具屬性)，但某些情況下直接呼叫 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 更適當。

屬性也可以在 XAML 中設定，稍後再於程式碼中透過程式碼後置存取。 如需詳細資訊，請參閱 [WPF 中的程式碼後置和 XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)。

## <a name="property-functionality-provided-by-a-dependency-property"></a>屬性的相依性屬性所提供的功能
相對於欄位支援屬性，相依性屬性提供能擴充屬性功能的功能。 通常，這類功能每一個都代表或支援整體 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能集的特定功能：

- [資源](#resources)

- [資料繫結](#data-binding)

- [樣式](#styles)

- [動畫](#animations)

- [中繼資料覆寫](#metadata-overrides)

- [屬性值繼承](#property-value-inheritance)

- [WPF 設計工具整合](#wpf-designer-integration)

### <a name="resources"></a>資源
您可以參考資源來設定相依性屬性值。 資源通常指定為 `Resources` 頁面根項目或應用程式的屬性值 (這些位置最方便存取資源)。 下列範例示範如何定義<xref:System.Windows.Media.SolidColorBrush>資源。

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

定義資源之後，您即可參考資源並用它提供屬性值︰

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

這個特定的資源稱之為 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (在 WPF XAML 中，您可以使用靜態或動態資源參考)。 若要使用動態資源參考，您必須設定相依性屬性，因此它是由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統啟用的專門動態資源參考使用。 如需詳細資訊，請參閱 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。

> [!NOTE]
> 資源視為區域數值，這表示如果您設定另一個區域數值，就會排除資源參考。 如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。

### <a name="data-binding"></a>資料繫結
相依性屬性可以透過資料繫結參考值。 資料繫結適用於透過特定的標記延伸語法，在 XAML 中，或<xref:System.Windows.Data.Binding>程式碼中的物件。 使用資料繫結，最後一個屬性值決定會延後到執行階段，此時已自資料來源取得值。

下列範例會設定<xref:System.Windows.Controls.ContentControl.Content%2A>屬性<xref:System.Windows.Controls.Button>，在 XAML 中使用的繫結宣告。 繫結使用繼承的資料內容和<xref:System.Windows.Data.XmlDataProvider>（未顯示） 的資料來源。 本身的繫結會指定所需的來源屬性<xref:System.Windows.Data.Binding.XPath%2A>內的資料來源。

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> 繫結視為區域數值，這表示如果您設定另一個區域數值，就會排除繫結。 如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。

相依性屬性，或<xref:System.Windows.DependencyObject>類別中，執行原本不支援<xref:System.ComponentModel.INotifyPropertyChanged>產生通知中的變更進行<xref:System.Windows.DependencyObject>來源的資料繫結作業的屬性值。 如需如何建立資料繫結所用屬性的詳細資訊，該資料繫結可以報告資料繫結目標的變更，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。

### <a name="styles"></a>樣式
樣式和範本是使用相依性屬性的兩大激勵案例。 樣式特別適用於設定定義應用程式 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的屬性。 樣式通常會定義為 XAML 中的資源。 樣式與屬性系統互動，因為它們通常包含特定屬性的 "setter"，以及根據另一個屬性的即時值變更屬性值的「觸發程序」。

下列範例會建立非常簡單的樣式 (這會定義在<xref:System.Windows.FrameworkElement.Resources%2A>字典中，不會顯示)，然後直接將套用該樣式<xref:System.Windows.FrameworkElement.Style%2A>屬性<xref:System.Windows.Controls.Button>。 樣式集內 setter<xref:System.Windows.Controls.Control.Background%2A>屬性已設定樣式的<xref:System.Windows.Controls.Button>為綠色。

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

如需詳細資訊，請參閱 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。

### <a name="animations"></a>Animations
相依性屬性可以動畫方式顯示。 套用並執行動畫時，動畫顯示值的運作優先於屬性可能執行的任何值 (例如本機值)。

下列範例以動畫方式顯示<xref:System.Windows.Controls.Control.Background%2A>上<xref:System.Windows.Controls.Button>屬性 (技術上來說，<xref:System.Windows.Controls.Control.Background%2A>會使用屬性項目語法來指定空白動畫<xref:System.Windows.Media.SolidColorBrush>為<xref:System.Windows.Controls.Control.Background%2A>，然後在<xref:System.Windows.Media.SolidColorBrush.Color%2A>屬性，<xref:System.Windows.Media.SolidColorBrush>是直接繪製的屬性)。

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

如需可動畫顯示屬性的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)及[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。

### <a name="metadata-overrides"></a>中繼資料會覆寫
當您衍生自最初登錄相依性屬性的類別時，您可以覆寫該屬性的中繼資料，變更相依性屬性的特定行為。 覆寫中繼資料依賴<xref:System.Windows.DependencyProperty>識別項。 覆寫中繼資料不需要重新實作屬性。 屬性系統會以原生方式處理中繼資料變更。每個類別都可能依每個類型，保存繼承自基底類別之所有屬性的個別中繼資料。

下列範例會覆寫相依性屬性的中繼資料<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>。 覆寫此特定相依性屬性中繼資料，是建立可使用佈景主題預設樣式控制項之實作模式的一部分。

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

如需覆寫或取得屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。

### <a name="property-value-inheritance"></a>屬性值繼承
項目可以繼承物件樹狀結構中的父代相依性屬性值。

> [!NOTE]
> 並非所有的相依性屬性都會啟用屬性值繼承行為，因為繼承的計算時間會影響效能。 通常只有建議屬性值繼承為適當的特定案例屬性才會啟用屬性值繼。 您可以在＜SDK 參考＞的**相依性屬性資訊**一節中查看相依性屬性，判斷該相依性屬性是否有繼承行為。

下列範例顯示繫結並設定<xref:System.Windows.FrameworkElement.DataContext%2A>指定的繫結，已不會顯示在先前範例中，繫結來源的屬性。 指定的來源不需要任何後續的繫結中的子物件，即可使用繼承的值從<xref:System.Windows.FrameworkElement.DataContext%2A>父系<xref:System.Windows.Controls.StackPanel>物件。 (或者，子物件可以改為選擇直接指定它自己<xref:System.Windows.FrameworkElement.DataContext%2A>或<xref:System.Windows.Data.Binding.Source%2A>中<xref:System.Windows.Data.Binding>，且如果故意不使用它的繫結的資料內容繼承的值。)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。

### <a name="wpf-designer-integration"></a>WPF 設計工具整合
有實作為相依性屬性之屬性的自訂控制項會獲得適當的 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 支援。 其中一例就是能夠使用 [屬性] 視窗編輯直接和附加的相依性屬性。 如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。

## <a name="dependency-property-value-precedence"></a>相依性屬性的值優先順序
當您取得相依性屬性的值時，您就可能取得一個值，此值原透過參與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的任何其他屬性型輸入來設定在該屬性上。 相依性屬性值有優先順序，所以屬性如何取得其值的各種案例才能以可預測的方式互動。

請參考下列範例。 此範例也包含適用於所有按鈕的樣式和其<xref:System.Windows.Controls.Control.Background%2A>屬性，但是再也會指定一個按鈕與本機設定<xref:System.Windows.Controls.Control.Background%2A>值。

> [!NOTE]
> SDK 文件在討論相依性屬性時，偶爾會使用詞彙「區域數值」或「本機設定值」。 本機設定值是一個屬性值，其直接設定在程式碼的物件執行個體上，或作為 XAML 項目上的屬性。  
  
基本上，第一個按鈕會設定兩次屬性，但只套用一個值：有最高優先順序的值。 本機設定值有最高優先順序 (執行中的動畫除外，但本例中未套用任何動畫)，因此第一個按鈕的背景使用本機設定值，而不使用樣式 setter 值。 第二個按鈕沒有區域數值 (樣式 setter 有最高的優先順序)，因此該按鈕的背景來自樣式 setter。

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>為什麼會有相依性屬性的優先順序？
通常您不會希望樣式一律套用樣式，甚至隱藏個別項目的本機設定值 (否則一般很難使用樣式或項目)。 因此，來自樣式的值運作優先順序比本機設定值低。 如需更完整的相依性屬性清單及相依性屬性有效值的可能來源，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。

> [!NOTE]
> 許多屬性是定義在相依性屬性的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目上。 大體上，屬性過去只有在需要支援至少一個屬性系統啟用的案例時，才會實作為相依性屬性︰資料繫結、樣式、動畫、預設值支援、繼承、附加屬性或失效。

## <a name="learning-more-about-dependency-properties"></a>深入了解相依性屬性  

- 附加屬性是支援 XAML 特殊語法的屬性類型。 附加屬性通常和 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性沒有 1:1 對應，而且不一定是相依性屬性。 附加屬性的一般用途是允許子項目向父項目回報屬性值，即使父項目和子項目未同時擁有列為類別成員的該屬性。 其中一個主要案例是啟用通知如何它們應呈現在父系的子項目[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; 如需範例，請參閱<xref:System.Windows.Controls.DockPanel.Dock%2A>或<xref:System.Windows.Controls.Canvas.Left%2A>。 如需詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。

- 元件開發人員或應用程式開發人員可能希望建立自己的相依性屬性，以便啟用資料繫結或樣式支援等功能，或用於失效和值的強制型轉支援。 如需詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。

- 相依性屬性通常應該視為公用屬性，任何可存取執行個體的呼叫端皆可存取或至少可探索它們。 如需詳細資訊，請參閱[相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)。

## <a name="see-also"></a>另請參閱
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [唯讀相依性屬性](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [WPF 架構](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
