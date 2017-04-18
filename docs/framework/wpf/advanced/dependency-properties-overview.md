---
title: "相依性屬性概觀 | Microsoft Docs"
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
  - "附加屬性"
  - "資料繫結"
  - "相依性屬性"
  - "屬性, 附加"
  - "屬性, 概觀"
  - "資源, 參考至"
  - "樣式"
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# 相依性屬性概觀
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供一組服務，可以用於擴充 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性的功能。  這些服務通常合稱為 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統。  受到 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統支援的屬性稱為[相依性屬性](GTMT)。本概觀將說明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統和[相依性屬性](GTMT)的功能。這包括如何在 XAML 和程式碼中使用現有的[相依性屬性](GTMT)。  本概觀也會介紹相依性屬性的特製化觀點，例如相依性屬性中繼資料，以及如何在自訂類別中建立您自己的相依性屬性。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您具有部分 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 和物件導向程式設計的基本知識。  為了能夠理解本主題中的範例，您也應該了解 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  如需詳細資訊，請參閱 [逐步解說：WPF 使用者入門](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
<a name="why_dependency_properties"></a>   
## 相依性屬性和 CLR 屬性  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，屬性通常會公開為 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性。  在基本的層面上，您可以直接與這些屬性互動，而永遠不需要知道他們是以[相依性屬性](GTMT)實作的。  然而，您應該要更為熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的部分或所有功能，這樣才能善用這些功能。  
  
 [相依性屬性](GTMT)的目的在於提供一個依據其他輸入值來計算屬性值的方式。  這些其他輸入可能包括系統屬性 \(例如佈景主題和使用者偏好設定\)、Just\-in\-Time 屬性決策機制 \(例如資料繫結和動畫\/Storyboard\)、多用途樣板 \(例如資源和樣式\)，或者是項目樹狀結構中透過父子關係與其他項目關聯的已知值。  除此之外，實作[相依性屬性](GTMT)可以提供獨立的 \(Self\-Contained\) 驗證、預設值、監視其他屬性變更的回呼，以及可以依據可能的執行階段資訊來強制轉型屬性值的系統。  衍生類別也可以藉由覆寫相依性屬性中繼資料來變更現有屬性的某些特定特性，而不用覆寫現有屬性的實際實作或建立新屬性。  
  
 在 SDK 參考中，您可以識別哪個屬性是相依性屬性，方法是看該屬性的 Managed 參考頁面上是否有＜相依性屬性資訊＞一節。  ＜相依性屬性資訊＞一節包含該相依性屬性的 <xref:System.Windows.DependencyProperty> 識別項欄位連結，也包含針對該屬性設定的中繼資料選項清單、針對類別的覆寫資訊，以及其他詳細資料。  
  
<a name="back_dependency_properties"></a>   
## 相依性屬性支援 CLR 屬性  
 藉由提供支援屬性的型別，[相依性屬性](GTMT)和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統會擴充屬性的功能，做為使用私用 \(Private\) 欄位來支援屬性的標準模式外的替代實作方式。  這個型別的名稱為 <xref:System.Windows.DependencyProperty>。  另一個定義 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的重要型別是 <xref:System.Windows.DependencyObject>。<xref:System.Windows.DependencyObject> 定義的基底類別可以註冊並擁有[相依性屬性](GTMT)。  
  
 以下是本[!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] 說明文件在討論[相依性屬性](GTMT)時，所使用的術語總結：  
  
-   **相依性屬性**：受到 <xref:System.Windows.DependencyProperty> 支援的屬性。  
  
-   **相依性屬性識別項**：一個 <xref:System.Windows.DependencyProperty> 執行個體，這是在註冊[相依性屬性](GTMT)時以傳回值的方式取得的，然後會儲存為靜態類別成員。  在許多與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統互動的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 中，會將這個識別項做為參數使用。  
  
-   **CLR 包裝函式**：屬性實際上的 get 和 set 實作。  藉由在 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 呼叫中使用識別項，這些實作會合併相依性屬性識別項，因而可支援使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的屬性。  
  
 下列範例會定義 `IsSpinning` [相依性屬性](GTMT)，並顯示 <xref:System.Windows.DependencyProperty> 識別項對其支援屬性的關係。  
  
 [!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
 [!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
[!code-csharp[PropertiesOvwSupport#DPFormBasic2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic2)]  
  
 屬性和其支援 <xref:System.Windows.DependencyProperty> 欄位的命名慣例是很重要的。  欄位的名稱一定要是屬性的名稱附加上後置字元 `Property`。  如需這個慣例和其原因的詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
<a name="setting_property_values"></a>   
## 設定屬性值  
 您可以在程式碼或是 XAML 中設定屬性。  
  
<a name="local_property_values"></a>   
### 在 XAML 中設定屬性值  
 下列 XAML 範例會將按鈕的背景色彩指定為紅色。  這個範例說明的情況是在產生的程式碼中，使用 WPF XAML 剖析器將 XAML 屬性的簡單字串值型別轉換成 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 型別 \(即 <xref:System.Windows.Media.Color>，經由 <xref:System.Windows.Media.SolidColorBrush>\)。  
  
 [!code-xml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]  
  
 XAML 支援各種設定屬性的語法型式。  而特定屬性該使用何種語法將取決於屬性所使用的實值型別以及其他因素，例如是否有型別轉換子存在。  如需屬性設定的 XAML 語法的詳細資訊，請參閱 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)和 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
 下列 XAML 範例則為非屬性 \(Attribute\) 語法範例，會顯示另一個按鈕背景。  這次不是設定簡單的純色，而是將背景設為影像，其中的項目代表該影像，而該影像來源則指定為巢狀項目的屬性 \(Attribute\)。  這是屬於屬性 \(Property\) 項目語法的範例。  
  
 [!code-xml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]  
  
<a name="setting_properties_code"></a>   
### 在程式碼中設定屬性  
 在程式碼中設定[相依性屬性](GTMT)值，通常只是簡單呼叫 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 包裝函式所公開的 set 實作。  
  
 [!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]  
  
 而取得屬性值基本上也只是呼叫 get 包裝函式實作：  
  
 [!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]  
  
 您也可以直接呼叫屬性系統 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A>。  在使用現有屬性時通常都不需要這樣做 \(包裝函式較為方便，並對於開發人員工具提供較好的屬性公開\)，但在某些情況下直接呼叫 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 則比較適當。  
  
 屬性也可以在 XAML 中設定，稍後再於程式碼中透過程式碼後置進行存取。  如需詳細資訊，請參閱[WPF 中的程式碼後置和 XAML](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)。  
  
<a name="functionality"></a>   
## 相依性屬性提供的屬性功能  
 相對於欄位所支援的屬性，相依性屬性所提供的功能可以擴充原來屬性的功能。  通常，每個這類的功能即代表或支援整體 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能集中的某個特定功能：  
  
-   [資源](#setting_properties_resources)  
  
-   [資料繫結](#setting_properties_data_binding)  
  
-   [樣式](#setting_properties_styles)  
  
-   [動畫](#animations)  
  
-   [中繼資料覆寫](#metadata)  
  
-   [屬性值繼承](#setting_properties_inheritance)  
  
-   [WPF 設計工具整合](#vs2008_integration)  
  
<a name="setting_properties_resources"></a>   
### 資源  
 相依性屬性的值可以藉由參考資源來設定。  資源通常都會指定做為頁面根項目的或是應用程式的 `Resources` 屬性值 \(這些位置可以提供最為方便的資源存取\)。  下列範例顯示如何定義 <xref:System.Windows.Media.SolidColorBrush> 資源。  
  
 [!code-xml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]  
  
 一旦定義好資源，您就可以參考資源並用來提供屬性值：  
  
 [!code-xml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]  
  
 這個特別的資源是當做 [DynamicResource 標記延伸](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)來參考 \(在 WPF XAML 中，您可以使用靜態或是動態資源參考\)。  若要使用動態資源參考，必須設定為相依性屬性，這樣就會是由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統所啟用的特別動態資源參考使用方式。  如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
> [!NOTE]
>  資源會視為是區域值，這代表如果您設定另一個區域值，就會排除該資源參考。  如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。  
  
<a name="setting_properties_data_binding"></a>   
### 資料繫結  
 相依性屬性可以透過資料繫結來參考值。  而資料繫結是透過 XAML 中的特定標記延伸語法，或是程式碼中的 <xref:System.Windows.Data.Binding> 物件運作。  藉由資料繫結，最後的屬性值決策會延後到執行階段，屆時會從資料來源取得值。  
  
 下列範例會使用 XAML 中宣告的繫結，設定 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.ContentControl.Content%2A> 屬性。  繫結使用繼承資料內容和 <xref:System.Windows.Data.XmlDataProvider> 資料來源 \(未顯示\)。  而繫結本身會在資料來源內藉由 <xref:System.Windows.Data.Binding.XPath%2A> 指定所要的來源屬性。  
  
 [!code-xml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]  
  
> [!NOTE]
>  繫結會視為是區域值，這代表如果您設定另一個區域值，就會排除該繫結。  如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。  
  
 為了要產生資料繫結作業的 <xref:System.Windows.DependencyObject> 來源屬性值的變更告知，相依性屬性或者是 <xref:System.Windows.DependencyObject> 類別本來就不支援 <xref:System.ComponentModel.INotifyPropertyChanged>。  如需如何建立用於資料繫結的屬性以回報資料繫結目標變更的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
<a name="setting_properties_styles"></a>   
### 樣式  
 樣式和樣板是兩個主要刺激使用相依性屬性的情況。  對於設定能夠定義應用程式 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 的屬性而言，樣式特別好用。  通常在 XAML 中樣式會定義為資源。  因為樣式通常包含特定屬性的 setter，以及包含會依據其他屬性的即時值來變更屬性值的 trigger，所以樣式會與屬性系統互動。  
  
 下列範例會建立很簡單的樣式 \(應該是定義在 <xref:System.Windows.FrameworkElement.Resources%2A> 字典內，在此未顯示\)，然後將該樣式直接套用到 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.FrameworkElement.Style%2A> 屬性。  樣式內的 setter 會將 <xref:System.Windows.Controls.Button> 樣式的 <xref:System.Windows.Controls.Control.Background%2A> 屬性設定為綠色。  
  
 [!code-xml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]  
  
 [!code-xml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]  
  
 如需詳細資訊，請參閱 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
<a name="animations"></a>   
### 動畫  
 相依性屬性可以使用動畫。  套用或執行動畫時，動畫值會比屬性所具有的其他任何值 \(例如區域值\) 擁有較高的優先順序。  
  
 下列範例會對 <xref:System.Windows.Controls.Button> 屬性使用動畫 <xref:System.Windows.Controls.Control.Background%2A> \(嚴格來說，<xref:System.Windows.Controls.Control.Background%2A> 使用動畫的方式是藉由使用屬性項目語法指定空白的 <xref:System.Windows.Media.SolidColorBrush> 做為 <xref:System.Windows.Controls.Control.Background%2A>，然後該 <xref:System.Windows.Media.SolidColorBrush> 的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 屬性是直接使用動畫的屬性\)。  
  
 [!code-xml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]  
  
 如需動畫屬性的詳細資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)和 [腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
<a name="metadata"></a>   
### 中繼資料覆寫  
 您可以變更[相依性屬性](GTMT)的某些行為，方法是在從原來註冊[相依性屬性](GTMT)的類別衍生時，覆寫該屬性的中繼資料。  覆寫中繼資料需要靠 <xref:System.Windows.DependencyProperty> 識別項。  覆寫中繼資料並不需要重新實作屬性。  中繼資料的變更本來就是由屬性系統處理的，基於以每個型別為基礎，每個類別很可能會持有繼承自基底類別的所有屬性的個別中繼資料。  
  
 下列範例會覆寫相依性屬性 <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> 的中繼資料。  覆寫這個特殊的相依性屬性中繼資料是實作模式的一部分，該實作模式會建立可以使用佈景主題的預設樣式的控制項。  
  
 [!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
 [!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]  
  
 如需覆寫或取得屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
<a name="setting_properties_inheritance"></a>   
### 屬性值繼承  
 項目可以從物件樹狀結構中的父項目繼承相依性屬性值。  
  
> [!NOTE]
>  屬性值的繼承行為並沒有針對所有相依性屬性全面啟用，因為繼承所需的計算時間的確會對效能造成某些影響。  通常只有在特定案例建議要有適當屬性值繼承時，才會啟用屬性的屬性值繼承。  您可以在 SDK 參考中查看該相依性屬性的＜**相依性屬性資訊**＞一節，以判斷相依性屬性是否可繼承。  
  
 下列範例顯示繫結，並會設定用於指定繫結來源的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性，這在稍早的繫結範例中沒有顯示。  子物件中任何後續繫結都不需要指定來源，可以使用父 <xref:System.Windows.Controls.StackPanel> 物件中 <xref:System.Windows.FrameworkElement.DataContext%2A> 的繼承值。  或者，子物件可以選擇在 <xref:System.Windows.Data.Binding> 中直接指定自己的 <xref:System.Windows.FrameworkElement.DataContext%2A> 或 <xref:System.Windows.Data.Binding.Source%2A>，並且刻意不使用其繫結之資料內容的繼承值。  
  
 [!code-xml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]  
  
 如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
<a name="vs2008_integration"></a>   
### WPF 設計工具整合  
 自訂控制項如果具有以相依性屬性實作的屬性，就會收到適當的 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 支援。  有一個範例是使用 \[**屬性**\] 視窗來編輯直接和附加相依性屬性的能力。  如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
<a name="value_determination"></a>   
## 相依性屬性值優先順序  
 在取得[相依性屬性](GTMT)的值時，您可能會透過參與 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統中的任何一項其他屬性輸入，取得該屬性上設定的值。  因為存有相依性屬性值優先順序，所以屬性如何取得其值的各種案例的互動方式就可以預測。  
  
 參考下列範例：  範例中包含的樣式可以套用到所有按鈕和其 <xref:System.Windows.Controls.Control.Background%2A> 屬性，但接著也會指定一個具有 <xref:System.Windows.Controls.Control.Background%2A> 區域設定值的按鈕。  
  
> [!NOTE]
>  SDK 說明文件在討論相依性屬性 \(Property\) 時會穿插使用詞彙「區域值」或「區域設定值」。  區域設定值這個屬性 \(Property\) 值，是以編寫程式碼的方式直接在物件執行個體中設定的，或是做為 XAML 的項目屬性 \(Attribute\)。  
  
 原則上，對第一個按鈕來說，屬性設定了兩次，但只會套用一個值：具有最高優先順序的值。  區域設定值具有最高優先順序 \(執行動畫時除外，但本範例中沒有套用動畫\)，因此會為第一個按鈕背景使用區域設定值，而非樣式 setter 值。  第二個按鈕沒有區域值 \(也沒有比樣式 setter 具有較高優先順序的其他值\)，因此該按鈕的背景來自樣式 setter。  
  
 [!code-xml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  
  
### 為什麼會存在相依性屬性優先順序  
 通常您不一定會想套用樣式，或是讓樣式混淆個別項目的區域設定值 \(否則，一般來說很難使用樣式或項目\)。  因此，來自樣式的值會比區域設定值的優先順序低。  如需更完整的相依性屬性清單，以及相依性屬性有效值的可能來源，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。  
  
> [!NOTE]
>  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 項目上定義的屬性有許多不是相依性屬性。  總結來說，只有在需要支援至少一個屬性系統所啟用的案例時，才要將屬性實作為相依性屬性，這些案例包括：資料繫結、樣式、動畫、預設值支援、繼承、附加屬性或失效。  
  
<a name="dp_implement_roadmap"></a>   
## 進一步了解相依性屬性  
  
-   [附加屬性](GTMT)是支援 XAML 中特製化語法的屬性型別。  附加屬性對 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性通常沒有一對一的對應，也不一定要是[相依性屬性](GTMT)。  [附加屬性](GTMT)的一般目的在於允許子項目回報屬性值給父項目，即使父項目和子項目的類別成員清單並沒有同時擁有該屬性。  一個主要的案例是讓子項目通知父項目在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 中呈現子項目的方式；如需範例，請參閱 <xref:System.Windows.Controls.DockPanel.Dock%2A> 或 <xref:System.Windows.Controls.Canvas.Left%2A>。  如需詳細資訊，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
-   元件開發人員或應用程式開發人員可能會想要建立自己的[相依性屬性](GTMT)，以啟用如資料繫結或樣式支援這類的功能，或是用於失效和值強制型轉 \(Coercion\) 支援。  如需詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
-   相依性屬性通常應該要考慮為公用屬性，可以讓能夠存取執行個體的任何呼叫端進行存取，或是至少可以發現該屬性。  如需詳細資訊，請參閱 [相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)。  
  
## 請參閱  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [唯讀相依性屬性](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [WPF 架構](../../../../docs/framework/wpf/advanced/wpf-architecture.md)