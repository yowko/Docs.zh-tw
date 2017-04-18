---
title: "自訂相依性屬性 | Microsoft Docs"
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
  - "自訂相依性屬性"
  - "相依性屬性, 自訂"
  - "實作, 包裝函式"
  - "中繼資料, 適用於屬性"
  - "屬性, 中繼資料"
  - "屬性, 註冊"
  - "註冊屬性"
  - "包裝函式, 實作"
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# 自訂相依性屬性
本主題描述 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式開發人員和元件作者會想要建立自訂的[相依性屬性](GTMT)的原因，並描述實作步驟，以及可以加強屬性的效能、可用性和全面性的一些實作選項。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已了解相依性屬性，知道如何使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別上的現有相依性屬性，而且已閱讀過[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)主題。  為了能夠理解本主題中的範例，您也應該了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，並知道如何撰寫 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。  
  
<a name="whatis"></a>   
## 相依性屬性是什麼  
 藉由將 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性實作為[相依性屬性](GTMT)，您可以讓屬性支援樣式、資料繫結、繼承、動畫和預設值。  相依性屬性是藉由呼叫 <xref:System.Windows.DependencyProperty.Register%2A> 方法 \(或 <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>\) 向 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統註冊的屬性，且該屬性受到 <xref:System.Windows.DependencyProperty> 識別項欄位的支援。  相依性屬性只能由 <xref:System.Windows.DependencyObject> 型別使用，但 <xref:System.Windows.DependencyObject> 位在很高層的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別階層架構，所以 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中大部分可用的類別都可以支援相依性屬性。  如需相依性屬性的詳細資訊，以及本 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 中用於描述相依性屬性的部分用語和慣例，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
<a name="example_dp"></a>   
## 相依性屬性範例  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別上實作的相依性屬性的範例包括 <xref:System.Windows.Controls.Control.Background%2A> 屬性、<xref:System.Windows.FrameworkElement.Width%2A> 屬性和 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性等等。  由類別公開的每個相依性屬性，在該相同類別上都具有公開的型別 <xref:System.Windows.DependencyProperty> 的對應公用靜態欄位。這是相依性屬性的識別項。  識別項的命名使用慣例：[相依性屬性](GTMT)名稱再附加上字串 `Property`。  舉例來說，<xref:System.Windows.Controls.Control.Background%2A> 屬性的對應 <xref:System.Windows.DependencyProperty> 識別項欄位是 <xref:System.Windows.Controls.Control.BackgroundProperty>。  識別項會儲存其註冊時的[相依性屬性](GTMT)資訊，然後牽涉到[相依性屬性](GTMT)的其他作業會於稍後使用識別項，例如呼叫 <xref:System.Windows.DependencyObject.SetValue%2A>。  
  
 如[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)中所述，因為「包裝函式」實作的關係，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的所有相依性屬性 \(除了大部分的[附加屬性](GTMT)以外\) 也都是 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性。  因此，您可以藉由從程式碼呼叫會以您對其他 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性使用的相同方式定義包裝函式的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 存取子，來取得或設定相依性屬性。  在使用建立好的相依性屬性時，通常不會使用 <xref:System.Windows.DependencyObject> 方法 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A>，這是對基礎屬性系統的連接點 \(Connection Point\)。  不過，現有的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性實作，藉由適當使用識別項欄位，在 `get` 和 `set` 包裝函式實作內會有已經呼叫過的 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A>。  如果您是實作自己的自訂相依性屬性，則要以相同方式定義包裝函式。  
  
<a name="backing_with_dp"></a>   
## 應該實作相依性屬性的時機  
 當您對類別實作屬性時，只要類別是衍生自 <xref:System.Windows.DependencyObject>，您就可以選擇使用 <xref:System.Windows.DependencyProperty> 識別項支援屬性，因而讓它成為相依性屬性。  讓屬性成為相依性屬性並不是永遠必要或適當的，且將依據您的案例需求而定。  有時候使用私用欄位來支援屬性的常用技術才是適當的。  然而，當您希望屬性支援下列一個或多個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能時，應該將屬性實作為[相依性屬性](GTMT)：  
  
-   您希望屬性在樣式中是可設定的。  如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
-   您希望屬性支援資料繫結。  如需資料繫結相依性屬性的詳細資訊，請參閱 [繫結兩個控制項的屬性](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md)。  
  
-   您希望屬性可以使用動態資源參考設定。  如需詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
-   您希望自動繼承項目樹狀結構中父項目的屬性值。  在這個情況下，使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 方法進行註冊，即使您也有建立用於 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 存取的屬性包裝函式。  如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
-   您希望屬性是可建立動畫的。  如需詳細資訊，請參閱 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
-   您希望屬性系統能夠在下列原因而變更屬性的前一個值時回報：屬性系統、環境或使用者所採取的動作，或是讀取和使用樣式。  藉由使用屬性中繼資料，您的屬性可以指定每當屬性系統判斷出屬性值肯定經過變更時叫用的回呼 \(Callback\) 方法。  有個相關的概念是屬性值強制型轉 \(Coercion\)。  如需詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  
  
-   您想要使用的建立好的中繼資料慣例，也由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 處理序所使用，例如回報變更屬性值是否需要配置系統重新撰寫項目的視覺效果。  或者是您希望能夠使用中繼資料覆寫，這樣衍生類別可以變更中繼資料的特性，例如預設值。  
  
-   您希望自訂控制項的屬性接收 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]支援，例如 \[**屬性**\] 視窗編輯。  如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 當您檢視這些案例時，也應該考慮是否可以藉由覆寫現有[相依性屬性](GTMT)的中繼資料，來達成您的案例，而不用實作全新的屬性。  中繼資料覆寫是否實用，取決於您的案例以及該案例與現有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 相依性屬性和類別的實作的相似度。  如需覆寫現有屬性中繼資料的詳細資訊，請參閱[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
<a name="checklist"></a>   
## 定義相依性屬性的檢查清單  
 定義相依性屬性包含四個主要概念。  這些概念不一定是絕對的程序步驟，因為其中幾個在實作上最後會結合成為單一程式碼行。  
  
-   \(選擇項\) 建立相依性屬性的屬性中繼資料。  
  
-   向屬性系統註冊屬性名稱，指定擁有者型別和屬性值的型別。  如果有使用屬性中繼資料的話，同時也要指定。  
  
-   將 <xref:System.Windows.DependencyProperty> 識別項定義為擁有者型別上的 `public` `static` `readonly` 欄位。  
  
-   定義 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」屬性，名稱要符合相依性屬性的名稱。  實作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」屬性的 `get` 和 `set` 存取子，以連接支援它的相依性屬性。  
  
<a name="registering"></a>   
### 向屬性系統註冊屬性  
 為了讓屬性成為[相依性屬性](GTMT)，您必須將該屬性註冊到屬性系統所維護的資料表中，並給它唯一識別項做為後續屬性系統作業的限定詞 \(Qualifier\)。  這些作業可能是內部作業，或是您自己的程式碼呼叫屬性系統 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]。  若要註冊屬性，要在類別主體內 \(類別內，但任何成員定義以外的地方\) 呼叫 <xref:System.Windows.DependencyProperty.Register%2A> 方法。  識別項欄位也是由 <xref:System.Windows.DependencyProperty.Register%2A> 方法呼叫提供為傳回值的。  之所以將 <xref:System.Windows.DependencyProperty.Register%2A> 呼叫置於其他成員定義外，是因為您會使用這個傳回值，將型別 <xref:System.Windows.DependencyProperty> 的 `public` `static` `readonly` 欄位指派和建立為類別的一部分。  這個欄位會成為相依性屬性的識別項。  
  
 [!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
 [!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]  
  
<a name="nameconventions"></a>   
### 相依性屬性名稱慣例  
 有些與相依性屬性相關的建立好的命名慣例，是您在例外情況外所必須全部遵守的。  
  
 相依性屬性本身具有基本的名稱，如本範例中的 "AquariumGraphic"，這是提供來做為 <xref:System.Windows.DependencyProperty.Register%2A> 的第一個參數。  該名稱在每個註冊型別內必須是唯一的。  透過基底型別繼承的相依性屬性會視為已經是註冊型別的一部分，繼承屬性的名稱不能再次註冊。  然而有一個技巧可以將類別加入做為相依性屬性的擁有者，即使該相依性屬性不是繼承的，如需詳細資訊，請參閱[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
 建立識別項欄位時，請以您註冊的屬性名稱命名這個欄位，再加上後置字元 `Property`。  這個欄位是您的相依性屬性識別項，且稍後會用來做為您放入包裝函式中的 <xref:System.Windows.DependencyObject.SetValue%2A> 和 <xref:System.Windows.DependencyObject.GetValue%2A> 呼叫的輸入，供任何其他程式碼存取您自己程式碼的屬性、供任何您允許的外部程式碼存取、供屬性系統，以及也可能供 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器使用。  
  
> [!NOTE]
>  在類別主體中定義相依性屬性是典型的實作，但也可以在類別靜態建構函式中定義相依性屬性。  在您需要一行以上的程式碼初始化相依性屬性時，這個方式比較合理。  
  
<a name="wrapper1"></a>   
### 實作「包裝函式」  
 包裝函式實作在 `get` 實作中應該呼叫 <xref:System.Windows.DependencyObject.GetValue%2A>，在 `set` 實作中應該呼叫 <xref:System.Windows.DependencyObject.SetValue%2A> \(這裡也顯示原始註冊呼叫和欄位以避免困擾\)。  
  
 在除了例外情況外的所有情況中，包裝函式實作只應該執行對應的 <xref:System.Windows.DependencyObject.GetValue%2A> 和 <xref:System.Windows.DependencyObject.SetValue%2A> 動作。  主題 [XAML 載入和相依性屬性](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)中會詳細討論其原因。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類別提供的所有現有公用相依性屬性，都使用這個簡單的包裝函式實作模型，相依性屬性運作的大部分複雜度在於屬性系統本身的行為、或是透過其他概念 \(例如透過屬性中繼資料的強制型轉或屬性變更回呼\) 而實作的。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
 同樣地，依據慣例，包裝函式屬性名稱必須與選擇和給予做為註冊屬性的 <xref:System.Windows.DependencyProperty.Register%2A> 呼叫的第一個參數相同。  如果屬性沒有遵循這個慣例，不一定會停用所有可能的使用，但您會遇到幾個值得注意的問題：  
  
-   某些方面的樣式和樣板無法運作。  
  
-   大部分的工具和設計工具必須仰賴命名慣例才能正確序列化 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，或是才能針對每個屬性層級提供設計工具環境協助。  
  
-   目前的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 載入器實作會略過整個包裝函式，並在處理屬性值時仰賴命名慣例。  如需詳細資訊，請參閱 [XAML 載入和相依性屬性](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)。  
  
<a name="metadata"></a>   
### 新相依性屬性的屬性中繼資料  
 註冊相依性屬性時，透過屬性系統的註冊會建立儲存屬性特性的中繼資料物件。  如果屬性是使用 <xref:System.Windows.DependencyProperty.Register%2A> 的簡單簽章註冊的，許多這些特性就會設定好預設值。  <xref:System.Windows.DependencyProperty.Register%2A> 的其他簽章允許您在註冊屬性時指定所要的中繼資料。  最常提供給相依性屬性的中繼資料，是會提供在使用屬性的新執行個體上套用的預設值。  
  
 如果建立的相依性屬性是在 <xref:System.Windows.FrameworkElement> 的衍生類別上，您可以使用更為特製化的中繼資料類別 <xref:System.Windows.FrameworkPropertyMetadata>，而非基底 <xref:System.Windows.PropertyMetadata> 類別。  <xref:System.Windows.FrameworkPropertyMetadata> 類別的建構函式有幾種簽章，您可以在其中指定各種中繼資料特性的組合。  如果您只想要指定預設值，請使用採用型別 <xref:System.Object> 的單一參數的簽章。  將該物件參數貼為屬性的型別專用預設值 \(提供的預設值型別必須是您在 <xref:System.Windows.DependencyProperty.Register%2A> 呼叫中提供做為`propertyType` 參數的\)。  
  
 對於 <xref:System.Windows.FrameworkPropertyMetadata>，也可以指定屬性的中繼資料選項旗標。  這些旗標在註冊後會轉換成屬性中繼資料上的不同屬性，並用於與配置引擎這類的其他處理序通訊某些條件。  
  
#### 設定適當的中繼資料旗標  
  
-   如果屬性 \(或是其值的變更\) 會影響[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]，特別是在影響配置系統對頁面項目的調整大小和轉譯方式，請設定一個或多個下列旗標：<xref:System.Windows.FrameworkPropertyMetadataOptions>、<xref:System.Windows.FrameworkPropertyMetadataOptions>、<xref:System.Windows.FrameworkPropertyMetadataOptions>。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> 表示這個屬性的變更需要 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 轉譯的變更，因為當中的包含物件在父項目內可能需要較多或較少的空間。  舉例來說，"Width" 屬性應該要設定這個旗標。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> 表示這個屬性的變更需要 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 轉譯的變更，這項變更通常不需要專用空間的變更，但的確表示空間內的位置已經變更過。  舉例來說，"Alignment" 屬性應該要設定這個旗標。  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions> 表示發生某個不會影響配置和度量的其他變更，但的確需要另一個轉譯。  一個範例是會變更現有項目色彩的屬性，例如 "Background"。  
  
    -   對於您自己的屬性系統的覆寫實作或配置回呼，這些旗標通常是用來做為中繼資料的通訊協定 \(Protocol\)。  例如，您的 <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> 回呼，可能會在執行個體的任何屬性回報值變更，且中繼資料中的 <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> 為 `true` 時，呼叫 <xref:System.Windows.UIElement.InvalidateArrange%2A>。  
  
-   有些屬性可能會影響包含父項目的轉譯特性，包括以上的影響方式，以及上述必要大小變更外的影響方式。  非固定格式文件模式中所使用的 <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> 屬性即是一個範例，該屬性的變更可以變更到包含段落的非固定格式文件的整體轉譯。  您可以在自己的屬性中使用 <xref:System.Windows.FrameworkPropertyMetadataOptions> 或 <xref:System.Windows.FrameworkPropertyMetadataOptions> 來識別類似的案例。  
  
-   根據預設，相依性屬性支援資料繫結。  對於沒有實際資料繫結的案例，或是當大型物件的資料繫結效能認定會有問題時，您可以刻意停用資料繫結。  
  
-   根據預設，相依性屬性的資料繫結 <xref:System.Windows.Data.Binding.Mode%2A> 預設為 <xref:System.Windows.Data.BindingMode>。  您隨時可以針對每個繫結執行個體，將繫結變更為 <xref:System.Windows.Data.BindingMode>，如需詳細資訊，請參閱 [指定繫結的方向](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md)。  然而身為相依性屬性的作者，您可以選擇讓屬性預設使用 <xref:System.Windows.Data.BindingMode> 繫結模式。  一個現有的相依性屬性範例是 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=fullName>，應用的案例是 <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> 設定邏輯和複合的 <xref:System.Windows.Controls.MenuItem> 會與預設主題樣式互動。  <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> 屬性邏輯原本就使用資料繫結，對應其他狀態屬性和方法呼叫以維護屬性的狀態。  另一個預設會繫結 <xref:System.Windows.Data.BindingMode> 的範例屬性是 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName>。  
  
-   您也可以藉由設定 <xref:System.Windows.FrameworkPropertyMetadataOptions> 旗標，啟用自訂相依性屬性的屬性繼承。  當父項目和子項目具有相同屬性，且子項目的該特定屬性值設定應該要與父項目的設定值相同時，屬性繼承就很好用。  可繼承屬性的範例有 <xref:System.Windows.FrameworkElement.DataContext%2A>，用於啟用資料展示的重要主從式案例的繫結作業。  藉由讓 <xref:System.Windows.FrameworkElement.DataContext%2A> 可繼承，任何子項目也會繼承資料內容。  由於有屬性值繼承，您可以在頁面或應用程式根項目指定資料內容，而不需要在所有可能的子項目針對繫結重新指定。  <xref:System.Windows.FrameworkElement.DataContext%2A> 也是一個示範繼承會覆寫預設值的很好範例，但它可以隨時在任何特定子項目上進行區域設定，如需詳細資訊，請參閱 [使用含階層式資料的主從式模式](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。  屬性值繼承的確要考量可能的效能影響，因此盡量不要使用，如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
-   設定 <xref:System.Windows.FrameworkPropertyMetadataOptions> 旗標以表示您的相依性屬性是否要讓巡覽日誌服務偵測到或使用。  相關範例有 <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> 屬性，選取控制項中選取的任何項目都應該在巡覽日誌記錄時持續保持。  
  
<a name="RODP"></a>   
## 唯讀相依性屬性  
 您可以定義唯讀的相依性屬性。  然而，您將屬性定義為唯讀的原因，會因每個案例而多少有所不同，向屬性系統註冊屬性和公開識別項的程序也是。  如需詳細資訊，請參閱[唯讀相依性屬性](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)。  
  
<a name="CTDP"></a>   
## 集合型別相依性屬性  
 集合型別相依性屬性有一些要額外考慮的實作問題。  如需詳細資訊，請參閱[集合類型相依性屬性](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)。  
  
<a name="SecurityC"></a>   
## 相依性屬性安全性考量  
 相依性屬性應該宣告為公用屬性。  相依性屬性識別項欄位應該宣告為公用靜態欄位。  即使您嘗試宣告其他的存取層級 \(例如保護\)，還是一定可以透過識別項結合屬性系統 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 存取相依性屬性。  即使是保護的識別項欄位，還是有可能可以存取，因為中繼資料回報或值判斷 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 為屬性系統的一部分，例如 <xref:System.Windows.LocalValueEnumerator>。  如需詳細資訊，請參閱 [相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)。  
  
<a name="DPCtor"></a>   
## 相依性屬性和類別建構函式  
 Managed 程式碼程式設計有個一般原則 \(通常是由 FxCop 這類的程式碼分析工具所強制\)：類別建構函式不該呼叫虛擬方法。  這是因為建構函式可以呼叫做為衍生類別建構函式的初始化，而透過建構函式進入虛擬方法，可能會發生在要建構的物件執行個體還在未完成初始化的狀態時。  當您要從已經衍生自 <xref:System.Windows.DependencyObject> 的任何類別衍生時，應該要注意屬性系統本身會在內部呼叫和公開虛擬方法。  這些虛擬方法屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 屬性系統服務。  覆寫方法能夠讓衍生類別參與值判斷。  若要避免執行階段初始化的可能問題，應該不要在類別建構函式內設定相依性屬性值，除非您是遵循非常專有的建構函式模式。  如需詳細資訊，請參閱 [DependencyObject 的安全建構函式模式](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)。  
  
## 請參閱  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [集合類型相依性屬性](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)   
 [相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)   
 [XAML 載入和相依性屬性](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)   
 [DependencyObject 的安全建構函式模式](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)