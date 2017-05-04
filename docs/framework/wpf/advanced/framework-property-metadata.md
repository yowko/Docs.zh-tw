---
title: "架構屬性中繼資料 | Microsoft Docs"
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
  - "架構屬性中繼資料"
  - "中繼資料, 架構屬性"
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 架構屬性中繼資料
若系統認為物件項目的屬性位於 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [WPF 架構層級](GTMT)，便會針對這些屬性回報架構屬性中繼資料選項。  [WPF 架構層級](GTMT)的指定通常代表呈現、資料繫結和屬性系統更新這類功能，都是由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 簡報、[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 和可執行檔負責處理。  這些系統會查詢架構屬性中繼資料，以判斷特定項目屬性的功能相關特性。  
  
   
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已經從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別上的現有相依性屬性的消費者觀點來了解[相依性屬性](GTMT)，而且已閱讀過[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  另外，您也應該已經閱讀過[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## 架構屬性中繼資料傳達的資訊  
 架構屬性中繼資料可分成下列幾種類別：  
  
-   影響項目的報告配置屬性 \(<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>、<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>、<xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>\)。  如果屬性分別影響這些設定，而且您也正在類別中實作 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> \/ <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法以提供特定呈現行為和資訊給配置系統，您可以在中繼資料中設定這些旗標。  這類實作通常會在屬性中繼資料中這些配置屬性為 true 的相依性屬性中，檢查屬性是否失效，而且只有這些失效屬性需要要求新的配置傳遞。  
  
-   影響項目之父項目的報告配置屬性 \(<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>、<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>\)。  預設設定這些旗標的範例包括 <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=fullName> 和 <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=fullName>。  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>.  相依性屬性預設不會繼承值。  <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> 也容許繼承路徑進入視覺化樹狀結構，而這在某些控制項複合案例中是必要的。  
  
    > [!NOTE]
    >  「繼承」一詞在屬性值的內容中代表相依性屬性專用的特性，其表示由於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統的 [WPF 架構層級](GTMT)功能，使得子項目可以從父項目繼承實際的相依屬性值。  它和 Managed 程式碼型別以及透過衍生型別 \(Derived Type\) 的成員繼承並無任何直接關聯。  如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
-   報告資料繫結特性 \(<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>、<xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>\)。  依據預設，架構中的相依性屬性支援單向繫結行為的資料繫結。  如果沒有任何資料繫結的案例，您可以停用資料繫結 \(因為它們較具彈性和擴充性，所以預設 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 中沒有很多這類屬性的範例\)。  您可以設定讓繫結擁有雙向預設值，以用於可在控制項元件片段間結合控制項行為的屬性 \(<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> 即為一個範例\)，或者雙向繫結是使用者常見或預期案例的情況 \(<xref:System.Windows.Controls.TextBox.Text%2A> 即為一個範例\)。  變更資料繫結相關中繼資料只會影響預設值；若以個別繫結為基準，則可隨時變更預設值。  如需繫結模型和一般繫結的詳細資訊，請參閱[資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)。  
  
-   報告支援日誌記錄的應用程式或服務是否應該記錄屬性日誌 \(<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>\)。  在一般項目中，日誌記錄並非預設啟用的功能，而是針對特定使用者控制項選擇性啟用的功能。  這個屬性主要是供日誌記錄服務讀取，包括日誌記錄的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作，而且通常是在使用者控制項上設定，例如在巡覽步驟間應該保留之清單內的使用者選取項目。  如需日誌的詳細資訊，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## 讀取 FrameworkPropertyMetadata  
 前面連結的各個屬性都是 <xref:System.Windows.FrameworkPropertyMetadata> 加入至其即時基底類別 <xref:System.Windows.UIPropertyMetadata> 的特定屬性。  根據預設，每一個屬性都是 `false`。  在屬性的中繼資料要求時，知道這些屬性的值非常重要，因此應該嘗試將傳回的中繼資料轉換成 <xref:System.Windows.FrameworkPropertyMetadata>，然後再視需要檢視個別屬性的值。  
  
<a name="Specifying_Metadata"></a>   
## 指定中繼資料  
 當您為了將中繼資料套用到新的相依性屬性註冊作業，而建立新的中繼資料執行個體時，您可以選擇所要使用的中繼資料類別：基底 <xref:System.Windows.PropertyMetadata> 或某個衍生類別 \(Derived Class\) \(例如 <xref:System.Windows.FrameworkPropertyMetadata>\)。  一般來說，您應該使用 <xref:System.Windows.FrameworkPropertyMetadata>，尤其是如果您的屬性與屬性系統和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能 \(例如配置和資料繫結\) 有任何互動。  另一個情況較複雜的選擇是從 <xref:System.Windows.FrameworkPropertyMetadata> 衍生，以自行建立成員中具有額外資訊的中繼資料報告類別。  或者，您也可以使用 <xref:System.Windows.PropertyMetadata> 或 <xref:System.Windows.UIPropertyMetadata> 以傳達實作功能的支援等級。  
  
 對於現有的屬性 \(<xref:System.Windows.DependencyProperty.AddOwner%2A> 或 <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> 呼叫\)，您應該一律覆寫為原始註冊作業所使用的中繼資料型別。  
  
 如果您要建立 <xref:System.Windows.FrameworkPropertyMetadata> 執行個體，有兩種方法可以填入 \(Populate\) 傳達架構屬性特性的特定屬性值：  
  
1.  使用容許 `flags` 參數的 <xref:System.Windows.FrameworkPropertyMetadata> 建構函式簽章 \(Signature\)。  這個參數應該填入 <xref:System.Windows.FrameworkPropertyMetadataOptions> 列舉型別旗標的所有必要組合值。  
  
2.  使用其中一個沒有 `flags` 參數的簽章，然後針對需要的每個特性變更，將 <xref:System.Windows.FrameworkPropertyMetadata> 上的每個報告布林 \(Boolean\) 值設定為 `true`。  如果使用這種方法，您必須在建構具有此相依性屬性的任何項目之前設定這些屬性；布林值屬性為讀寫屬性，如此才能讓這項行為避免使用 `flags` 參數，而且仍然會填入中繼資料，但是中繼資料必須在使用屬性之前加以有效密封。  因此，嘗試在要求中繼資料之後設定屬性是無效的作業。  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## 架構屬性中繼資料合併行為  
 覆寫架構屬性中繼資料時，不同的中繼資料特性會被合併或取代。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 會合併。  如果您加入新的 <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，該回呼會儲存在中繼資料裡。  如果沒有在覆寫中指定 <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 的值會從中繼資料裡參考最接近它的祖系。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> 的實際屬性系統行為如下：階層架構中所有中繼資料擁有者的實作都會保留並加入到資料表，屬性系統的執行順序為最深層衍生類別的回呼會最先叫用 \(Invoke\)。  繼承回呼只會執行一次，而中繼資料則會將發出回呼的類別視為其擁有者。  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> 會被取代。  如果沒有在覆寫中指定 <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>，<xref:System.Windows.PropertyMetadata.DefaultValue%2A> 的值會取自在中繼資料裡指定它的最接近祖系。  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 實作會被取代。  如果您加入新的 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>，該回呼會儲存在中繼資料裡。  如果沒有在覆寫中指定 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>，<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 的值會從中繼資料裡指定它的最接近祖系升級為參考。  
  
-   屬性系統行為是只會叫用直接中繼資料裡的 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>。  階層架構中其他 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 實作的參考都不會保留。  
  
-   <xref:System.Windows.FrameworkPropertyMetadataOptions> 列舉的旗標會結合為位元 OR 作業。  如果您指定 <xref:System.Windows.FrameworkPropertyMetadataOptions>，則不會覆寫原始選項。  若要變更選項，請在 <xref:System.Windows.FrameworkPropertyMetadata> 上設定對應的屬性。  例如，如果原始 <xref:System.Windows.FrameworkPropertyMetadata> 物件設定 <xref:System.Windows.FrameworkPropertyMetadataOptions?displayProperty=fullName> 旗標，則您可以將 <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=fullName> 設為 `false` 以變更該旗標。  
  
 此行為是由 <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A> 實作，可在衍生的中繼資料類別上覆寫。  
  
## 請參閱  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>   
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)