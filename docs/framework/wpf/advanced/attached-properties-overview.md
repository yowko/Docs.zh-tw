---
title: "附加屬性概觀 | Microsoft Docs"
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
  - "附加屬性 [WPF 設計工具]"
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 27
---
# 附加屬性概觀
「附加屬性」\(Aattached Property\) 是 XAML 所定義的概念。  附加屬性主要是當做一種全域屬性使用，可在任何物件上設定。  在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、 附加屬性通常會定義為特定形式的沒有傳統屬性 「 包裝函式 」 的相依性屬性。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已經從 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 類別上的現有相依性屬性的消費者觀點來了解相依性屬性，而且已閱讀過[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  若要遵循本主題中的範例，應該也了解 XAML 並知道如何撰寫[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。  
  
<a name="attached_properties_usage"></a>   
## 為什麼要使用附加屬性  
 附加屬性的其中一個用途，就是針對父項目中定義的屬性，讓不同的子項目能夠指定該屬性的唯一值。  這種案例的具體應用方式，就是讓子項目告知父項目其本身在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中的呈現方式。  其中一個例子就是 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 屬性。  <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 屬性會建立成附加屬性的原因在於，它是設計成要在 <xref:System.Windows.Controls.DockPanel> 所包含的項目上設定，而不是在 <xref:System.Windows.Controls.DockPanel> 本身設定。  <xref:System.Windows.Controls.DockPanel> 類別會定義名為 <xref:System.Windows.Controls.DockPanel.DockProperty> 的靜態 <xref:System.Windows.DependencyProperty> 欄位，然後提供 <xref:System.Windows.Controls.DockPanel.GetDock%2A> 和 <xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法做為[附加屬性](GTMT)的公用存取子。  
  
<a name="attached_properties_xaml"></a>   
## XAML 中的附加屬性  
 在 XAML 中，請使用 *AttachedPropertyProvider*.*PropertyName* 語法設定附加屬性。  
  
 下列範例顯示如何在 XAML 中設定 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>：  
  
 [!code-xml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 請注意，其用法有點類似於靜態屬性，但參考的是擁有和註冊[附加屬性](GTMT)的 <xref:System.Windows.Controls.DockPanel> 型別，而不是參考由名稱指定的任何執行個體。  
  
 同時，因為在 XAML 中的附加的屬性是您在標記中設定的屬性，只設定作業會有任何關聯性。  您無法直接取得屬性在 XAML 中，雖然有某些間接的機制，來比較值，例如樣式中的觸發程序 \(如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)\)。  
  
### WPF 中的附加屬性實作  
 在[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、 存在於這些附加屬性都是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] UI 呈現與相關的型別實作為相依性屬性。  附加的屬性是 XAML 概念，而相依性屬性就是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的概念。  因為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]附加的屬性是相依性屬性，它們支援相依性屬性概念，例如屬性中繼資料，且預設值，從該屬性的中繼資料。  
  
<a name="howused"></a>   
## 擁有者型別使用附加屬性的方式  
 雖然附加屬性可在任何物件上設定，但這並不表示設定了屬性就會產生明確的結果，也不表示會有另一個物件使用該值。  一般來說，使用附加屬性的目的是要讓來自各種不同的類別階層架構或邏輯關聯性的物件，都能對定義附加屬性的型別報告通用資訊。  定義附加屬性的型別通常遵循下列其中一種模型：  
  
-   定義附加屬性的型別會設計成父項目，做為會設定附加屬性值之項目的父項目。  此型別接著會透過內部邏輯對照某個物件樹狀結構逐一查看子物件、取得值，並且以某種方式操作這些值。  
  
-   定義附加屬性的型別會當做各種可能的父項目和內容模型的子項目使用。  
  
-   定義附加屬性的型別代表服務。  其他型別會設定附加屬性的值。  接著，當設定屬性的項目在服務的內容中被評估時，服務類別的內部邏輯會取得附加屬性值。  
  
### 父項目定義的附加屬性範例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義附加屬性最常見的案例是當父項目支援子項目集合並且實作行為時，其中每個子項目都會個別報告該行為的特性。  
  
 <xref:System.Windows.Controls.DockPanel> 會定義 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 附加屬性，而且 <xref:System.Windows.Controls.DockPanel> 有類別層級程式碼做為其轉譯邏輯的一部分 \(具體來說，就是 <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> 和 <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>\)。  <xref:System.Windows.Controls.DockPanel> 執行個體一定會檢查它是否有任何直接子項目設定了 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 的值。  若有，這些值就會成為套用到該特定子項目之轉譯邏輯的輸入。  巢狀 <xref:System.Windows.Controls.DockPanel> 執行個體會處理自己目前的子項目集合，不過該行為是根據 <xref:System.Windows.Controls.DockPanel> 處理 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 值的方式而定的實作專屬行為。  理論上，附加屬性可以影響目前父項目以外的項目。  如果在項目上設定 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 附加屬性，而該項目沒有對其執行動作的 <xref:System.Windows.Controls.DockPanel> 父項目，則不會引發錯誤或例外狀況。  這只是表示設定了全域屬性值，但目前沒有 <xref:System.Windows.Controls.DockPanel> 父項目可使用該資訊。  
  
<a name="attached_properties_code"></a>   
## 程式碼中的附加屬性  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的附加屬性沒有典型的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」方法可提供方便的取得\/設定存取。  這是因為附加屬性不一定是已設定屬性之執行個體的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 命名空間的一部分。  不過，XAML 處理器必須能夠剖析 XAML 時，設定這些值。  若要支援有效的附加的屬性使用方式，附加屬性的擁有者型別必須在表單中實作專用的存取子方法`取得`*PropertyName* 和`設定`*PropertyName*。  在程式碼中取得或設定附加屬性時，這些專屬的存取子方法也會相當實用。  從程式碼的角度來說，附加屬性類似於有方法存取子而非屬性存取子的支援欄位，而支援欄位可以存在於任何物件上，而無須特別定義。  
  
 下列範例顯示如何在程式碼中設定附加屬性。  在這個範例中，`myCheckBox` 是 <xref:System.Windows.Controls.CheckBox> 類別的執行個體。  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 對 XAML 的類似情況下，如果`myCheckBox`有尚未加入當成子元素的`myDockPanel`的第三行程式碼中，第四行程式碼就不會引發例外狀況，但屬性值就不會與互動<xref:System.Windows.Controls.DockPanel>父代，因此會執行任何動作。  只有在子項目上有設定 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> 值再加上有 <xref:System.Windows.Controls.DockPanel> 父項目存在，才會在轉譯的應用程式中產生有效的行為。  在此情況下，您可以設定附加屬性，然後將它附加至樹狀結構。  或者，您可以先附加至樹狀結構，再設定附加屬性。  這兩種順序的結果都一樣。  
  
<a name="attached_properties_metadata"></a>   
## 附加屬性中繼資料  
 註冊屬性時，會設定 <xref:System.Windows.FrameworkPropertyMetadata> 來指定屬性的特性，例如屬性是否會影響轉譯、測量等。  [附加屬性](GTMT)的中繼資料與[相依性屬性](GTMT)的中繼資料一般並無不同。  如果您覆寫附加屬性中繼資料時指定預設值，該值會成為覆寫類別之執行個體上的隱含附加屬性預設值。  具體來說，如果某個處理序透過附加屬性的 `Get` 方法存取子查詢該屬性的值，就會回報預設值，其中指出您所指定之中繼資料的類別執行個體，以及未設定之附加屬性的值。  
  
 如果您要在屬性上啟用屬性值繼承，請使用附加屬性，而不要使用非附加的相依性屬性。  如需詳細資訊，請參閱[屬性值繼承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)。  
  
<a name="custom"></a>   
## 自訂附加屬性  
  
<a name="create_attached_properties"></a>   
### 建立附加屬性的時機  
 當類別要以定義類別以外的方式來設定屬性時，就可以建立[附加屬性](GTMT)。  最常見的情形就是配置。  現有配置屬性的範例包括 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>、<xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=fullName> 和 <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=fullName>。  上述情形是指用來控制配置之項目的子項目，能夠各自將配置需求表達給其配置父項目，針對父項目定義為附加屬性的屬性，各子項目也會設定屬性值。  
  
 另一個使用附加屬性的情形是當類別代表服務，而您要其他類別能夠與該服務更緊密整合時。  
  
 另外還有一個情形是要獲得 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 支援，例如編輯 \[**屬性**\] 視窗。  如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 如前所述，若要使用屬性值繼承機制，請註冊成附加屬性。  
  
<a name="how_do_i_create_attached_properties"></a>   
### 如何建立附加屬性  
 如果類別定義[附加屬性](GTMT)僅供在其他型別上使用，那麼該類別就無須從 <xref:System.Windows.DependencyObject> 衍生。  不過，您需要以衍生自<xref:System.Windows.DependencyObject>如果您遵循整體[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]模型讓您附加的屬性也是相依性屬性。  
  
 藉由宣告 <xref:System.Windows.DependencyProperty> 型別的 `public` `static` `readonly` 欄位，將附加屬性定義為相依性屬性。  您可以使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 方法的傳回值來定義此欄位。  欄位名稱必須與後面附加字串 `Property` 的附加屬性名稱相符，以遵循辨識欄位與其所代表屬性的既定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 模式。  附加的屬性提供者也必須提供靜態`取得`*PropertyName* 和`設定`*PropertyName* 方法存取子為附加的屬性。 若要執行這項操作失敗，將會導致無法使用附加的屬性的屬性系統。  
  
> [!NOTE]
>  如果您省略附加屬性的 Get 存取子，則此屬性上的資料繫結在設計工具 \(如 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 和 Expression Blend\) 中會無法運作。  
  
#### Get 存取子  
 簽章`取得`*PropertyName* 存取子必須為：  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` 物件可在您的實作中指定為更特定的型別。  例如，<xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=fullName> 方法會將參數的型別設為 <xref:System.Windows.UIElement>，因為附加屬性只能在 <xref:System.Windows.UIElement> 執行個體上設定。  
  
-   傳回值可指定為實作中的特定型別。  例如，<xref:System.Windows.Controls.DockPanel.GetDock%2A> 方法會將該值的型別設為 <xref:System.Windows.Controls.Dock>，因為它只能設為該列舉型別。  
  
#### Set 存取子  
 簽章`設定`*PropertyName* 存取子必須為：  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` 物件可在您的實作中指定為更特定的型別。  例如，<xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法會將它的型別設為 <xref:System.Windows.UIElement>，因為附加屬性只能在 <xref:System.Windows.UIElement> 執行個體上設定。  
  
-   `value` 物件可在您的實作中指定為更特定的型別。  例如，<xref:System.Windows.Controls.DockPanel.SetDock%2A> 方法會將該值的型別設為 <xref:System.Windows.Controls.Dock>，因為它只能設為該列舉型別。  請記住，這個方法的值是來自 XAML 載入器，當它遇到附加的屬性的附加的屬性使用方式，在標記中的輸入。  輸入都是以 XAML 屬性值在標記中所指定的值。  因此，您所使用的型別必須有型別轉換、值序列化程式或標記延伸支援，以從屬性 \(Attribute\) 值 \(其最終只是字串\) 建立適當的型別。  
  
 下列範例顯示相依性屬性註冊 \(使用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法\)，以及`取得`*PropertyName* 和`設定`*PropertyName* 存取子。  在這個範例中，附加屬性名稱為 `IsBubbleSource`。  因此，存取子必須命名為 `GetIsBubbleSource` 和 `SetIsBubbleSource`。  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### 附加屬性 \(Property\) 的屬性 \(Attribute\)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義了數個 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)]，目的是要將附加屬性的相關資訊提供給反映 \(Reflection\) 處理序，以及反映和屬性資訊的一般使用者 \(例如設計人員\)。  由於附加的屬性的一種沒有範圍限制，因此設計人員需要方法來避免使用 XAML 的特定技術實作中所定義的所有附加屬性的全域清單，讓使用者無所適從。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 針對附加屬性所定義的 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] 可以限制屬性視窗的顯示範圍，只顯示特定的附加屬性。  您也可以考慮將這些屬性 \(Attribute\) 套用到您的自訂附加屬性 \(Property\)。  有關 [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] 的用途和語法說明，請參閱相關參考頁面：  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## 進一步了解附加屬性  
  
-   如需有關如何建立附加的屬性的詳細資訊，請參閱[註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)。  
  
-   如需相依性屬性和附加屬性的進階使用案例，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
-   您也可以將屬性註冊為附加屬性以及相依性屬性，但仍公開「包裝函式」實作。  在此情況下，屬性可以設定在該項目，或透過 XAML 的任意要素上附加屬性語法。  <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=fullName> 就是一個有標準和附加使用案例的屬性。  
  
## 請參閱  
 <xref:System.Windows.DependencyProperty>   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)