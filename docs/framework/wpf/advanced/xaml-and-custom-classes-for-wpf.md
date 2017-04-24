---
title: "WPF 的 XAML 和自訂類別 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "類別, XAML 的自訂類別"
  - "XAML 的自訂類別"
  - "XAML, 自訂類別"
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# WPF 的 XAML 和自訂類別
在中實作時的 XAML [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]架構支援能夠定義自訂的類別或結構中任何[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]語言中，然後存取該類別使用 XAML 標記。  您可以在同一個標記檔內混合使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 所定義的類型以及您的自訂類型，通常可藉由將自訂類型對應至 XAML 命名空間前置字元的方式達到此目的。  本主題討論自訂類別才能做為 XAML 項目都必須滿足的需求。  
  
   
  
<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## 應用程式或組件中的自訂類別  
 在 XAML 中使用的自訂類別可以定義兩種不同的方式： 在程式碼後置或其他程式碼產生主要[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式，或為另一個組件，例如可執行檔中的類別或做為類別庫的 DLL。  這兩種方式各有其優缺點。  
  
-   建立類別庫的好處是不同應用程式可共用自訂類別。  另一個儲存庫也至控制項，方便版本控制的應用程式的問題，並能簡化建立為 XAML 頁面上根項目的預期的類別使用方式的類別。  
  
-   在應用程式中定義自訂類別的好處是，這種方式相對精簡，可減少在主要應用程式可執行檔以外加入個別組件時遇到的部署和測試問題。  
  
-   是否在相同或不同的組件中定義，自訂類別必須對應 CLR 命名空間和 XML 命名空間之間，為了能在 XAML 中做為項目。  請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## 自訂類別當做 XAML 項目使用的要求  
 要能夠具現化為物件項目，類別必須符合下列要求：  
  
-   自訂類別必須為公用並支援預設的 \(無參數\) 公用建構函式   \(如需有關結構的注意事項，請參閱下一節\)。  
  
-   您的自訂類別不能是巢狀類別。  巢狀類別及其一般 CLR 使用語法中的「點號」\(Dot\) 會妨礙其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和\/或 XAML 功能，例如附加屬性。  
  
 除了啟用物件項目語法，針對接受該物件做為實值型別的任何其他公用屬性，您的物件定義也會啟用屬性項目語法。  這是因為物件現在可具現化為物件項目，並可填入這種屬性的屬性項目值。  
  
### 結構  
 因為自訂型別永遠能夠建構在 XAML 中定義的結構[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。這是因為[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]編譯器會隱含建立的預設建構函式會初始化為其預設值的所有屬性值的結構。  在某些情況中，您可能不想要結構的預設建構行為和\/或物件項目使用方式。  這可能是因為在概念上，結構原意是要將值和函式以等位方式填入，其中包含的值可能有互斥 \(Mutually Exclusive\) 解譯，因此其中沒有可設定的屬性。  <xref:System.Windows.GridLength> 是一個這類型結構的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 範例。  一般而言，這類型的結構應該實作型別轉換子，以使用為結構的值建立不同解譯或模式的字串慣例，讓值能夠以屬性表單表達。  而結構也應該透過非預設的建構函式，公開程式碼建構的類似行為。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## 自訂類別的屬性 \(Property\) 當做 XAML 屬性 \(Attribute\) 使用的要求  
 屬性必須參考傳值 \(By\-Value\) 型別 \(例如基本型別\)，或使用擁有 XAML 處理器可存取的預設建構函式或專屬型別轉換子之型別的類別。  在 CLR XAML 實作中，XAML 處理器不是透過語言基本型別的原生支援，就是透過將 <xref:System.ComponentModel.TypeConverterAttribute> 應用至備份型別定義中的型別或成員來尋找這類轉換子。  
  
 或者，屬性可參考抽象類別型別或介面。  針對抽象類別或介面，對 XAML 剖析的期望是屬性值必須填入實作介面的實體類別執行個體，或衍生自抽象類別之型別的執行個體。  
  
 屬性可以在抽象類別上宣告，但是只能在衍生自抽象類別的實體類別上設定。  這是因為建立類別的物件項目需要在類別上擁有公用預設建構函式。  
  
### 啟用 TypeConverter 的屬性語法  
 如果您在類別層級提供專用的且使用屬性 \(Attribute\) 的型別轉換子，套用的型別轉換可供需要具現化該型別的任何屬性 \(Property\) 啟用屬性 \(Attribute\) 語法。  型別轉換子不會啟用型別的物件項目使用方式；唯該型別有預設建構函式存在時，才能啟用物件項目的使用方式。  因此，一般而言，啟用型別轉換子的屬性 \(Property\) 不能在屬性 \(Property\) 語法中使用，除非型別本身也支援物件項目語法。  例外的是，您可以指定屬性 \(Property\) 項目語法，但屬性 \(Property\) 項目要包含字串。  這種使用方式基本上相當於屬性 \(Attribute\) 語法使用方式，且並不常見，除非需要以更嚴格的方式處理屬性 \(Attribute\) 值的空白區。  例如，以下是接受字串的屬性 \(Property\) 項目使用方式，以及對等的屬性 \(Attribute\) 使用方式：  
  
 [!code-xml[XamlOvwSupport#GoofyTCPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xml[XamlOvwSupport#GoofyTCPE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 在允許屬性語法，但屬性項目語法，其中包含物件項目不允許透過 XAML 屬性的範例所採取的各種屬性<xref:System.Windows.Input.Cursor>型別。  <xref:System.Windows.Input.Cursor> 類別有專用型別轉換子 <xref:System.Windows.Input.CursorConverter>，但不會公開預設建構函式，因此 <xref:System.Windows.FrameworkElement.Cursor%2A> 屬性 \(Property\) 只能透過屬性 \(Attribute\) 語法設定，即使實際 <xref:System.Windows.Input.Cursor> 型別為參考型別也一樣。  
  
### 個別屬性的型別轉換子  
 此外，屬性本身可以在屬性層級宣告型別轉換子。  這可提供「迷你語言」 \(Mini Language\)，以具現化屬性 \(Property\) 的型別物件，方式是根據適當的型別，將屬性 \(Attribute\) 的傳入字串值處理成 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 作業的輸入。  通常這為了提供一個方便的存取子，而不是只表示允許在 XAML 中設定屬性。  不過，若屬性 \(Attribute\) 要使用不提供預設建構函式或屬性型別轉換子的現有 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 型別，您也可以使用型別轉換子。  範例從[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API 所採取的特定屬性<xref:System.Globalization.CultureInfo>型別。  如此一來， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用現有的[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]<xref:System.Globalization.CultureInfo>更完善地處理較早版本的架構中所用的相容性和移轉案例的型別，但<xref:System.Globalization.CultureInfo>型別並不支援所需的建構函式或型別層級的型別轉換，您應該為 XAML 屬性值直接。  
  
 每當您公開有 XAML 使用方式的屬性 \(Property\) 時，尤其如果您是控制項作者時，則應認真考慮使用相依性屬性 \(Property\) 支援該屬性 \(Property\)。  特別是如果您使用現有的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]實作的 XAML 處理器，因為您可以使用，以改善效能，所以<xref:System.Windows.DependencyProperty>備份。  相依性屬性會公開屬性的屬性系統功能，這些功能是使用者預期 XAML 可存取屬性會具備的功能。  這包括如動畫、資料繫結和樣式支援等功能。  如需詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)和 [XAML 載入和相依性屬性](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)。  
  
### 撰寫型別轉換子並設定其屬性  
 您偶爾需要撰寫自訂 <xref:System.ComponentModel.TypeConverter> 衍生類別，以便為屬性型別提供型別轉換。  如需如何建立支援 XAML 使用方式的型別轉換子、如何從其進行衍生作業，以及如何套用 <xref:System.ComponentModel.TypeConverterAttribute> 的指示，請參閱 [TypeConverter 和 XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## 自訂類別事件上的 XAML 事件處理常式屬性語法的要求  
 若要能當做 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件使用，則此事件必須在支援預設建構函式的類別上公開為公用事件，或在抽象類別上公開為公用事件。該抽象類別的事件可讓衍生類別存取。  為方便當做[路由事件](GTMT)使用，[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件應實作明確的 `add` 和 `remove` 方法。這兩個方法會加入和移除 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件簽章的處理常式，並將這些處理常式轉送到 <xref:System.Windows.UIElement.AddHandler%2A> 和 <xref:System.Windows.UIElement.RemoveHandler%2A> 方法。  這些方法會將處理常式加入到事件附加所在的執行個體上的路由事件處理常式存放區，或從存放區移除事件處理常式。  
  
> [!NOTE]
>  您可以使用 <xref:System.Windows.UIElement.AddHandler%2A> 直接註冊路由事件的處理常式，並刻意不定義公開[路由事件](GTMT)的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件。  通常建議您不要因為事件並不會啟動 XAML 屬性語法，讓您附加處理常式，而且產生的類別會提供較不透明的 \[XAML\] 檢視的型別之能力。  
  
<a name="Collection_Properties"></a>   
## 撰寫集合屬性  
 接受集合型別的屬性 \(Property\) 有 XAML 語法，可讓您指定要加入到集合的物件。  此語法有兩個值得注意的功能。  
  
-   屬於集合物件的物件不需要在物件項目語法中指定。  每當您在 XAML 中指定接受集合型別的屬性時，集合型別的存在是隱含的。  
  
-   標記中集合屬性的子項目會處理成為集合的成員。  一般而言，以程式碼存取集合成員是透過清單\/字典方法 \(例如 `Add`\) 或透過索引子執行。  但 XAML 語法不支援的方法或索引子 \(例外狀況: XAML 2009 可以支援的方法，但使用 XAML 2009 限制可能的 WPF 使用方式。 see [XAML 2009 語言功能](../../../../docs/framework/xaml-services/xaml-2009-language-features.md)\).  集合很明顯是建立項目樹狀結構的基本要求，您需要想辦法在宣告式 XAML 中填入這些集合。  因此，集合屬性子項目的處理方式是將它們加入到屬於集合屬性型別值的集合。  
  
 。NET 架構的 XAML 服務實作，因此 WPF XAML 處理器會使用下列的定義是由什麼組成的集合屬性。  屬性的屬性型別必須實作下列其中一項：  
  
-   實作 <xref:System.Collections.IList>。  
  
-   實作 <xref:System.Collections.IDictionary> 或泛型對應項 \(<xref:System.Collections.Generic.IDictionary%602>\)。  
  
-   衍生自<xref:System.Array> \(如需有關在 XAML 中的陣列的詳細資訊，請參閱[x:Array 標記延伸](../../../../docs/framework/xaml-services/x-array-markup-extension.md)。\)  
  
-   實作 <xref:System.Windows.Markup.IAddChild> \([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義的介面\)。  
  
 每一種類型，在 CLR 中具有`Add`方法，供 XAML 處理器用來建立物件的圖形時，將項目加入基礎集合。  
  
> [!NOTE]
>  一般`List`和`Dictionary`介面 \(<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>\) 不支援集合偵測的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器。  然而您可以使用 <xref:System.Collections.Generic.List%601> 類別做為基底類別，因為它直接實作 <xref:System.Collections.IList>，或是使用 <xref:System.Collections.Generic.Dictionary%602> 做為基底類別，因為它直接實作 <xref:System.Collections.IDictionary>。  
  
 當您宣告接受集合的屬性時，請務必注意屬性值如何在型別的新執行個體中初始化。  如果您不將屬性實作為相依性屬性，那麼讓屬性使用會呼叫集合型別建構函式的支援欄位即已足夠。  如果屬性是相依性屬性，則可能需要將集合屬性初始化設為預設型別建構函式的一部分。  這是因為相依性屬性會從中繼資料取得預設值，而您一般不會想要集合屬性的初始值是靜態的共用集合。  每個包含的型別執行個體都應有一個集合執行個體。  如需詳細資訊，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。  
  
 您可以為集合屬性實作自訂集合型別。  由於集合屬性會視為隱含，自訂集合型別不需要提供預設建構函式，就能在 XAML 中隱含使用。  不過，您可以選擇性提供集合型別的預設建構函式。  這可能是值得的做法。  除非您提供預設建構函式，否則無法將集合明確宣告為物件項目。  部分標記作者可能會因為標記樣式的關係，希望看到明確的集合。  此外，當您建立使用集合型別做為屬性值的新物件時，預設建構函式也可簡化初始化要求。  
  
<a name="XAMLCONtent"></a>   
## 宣告 XAML 內容屬性  
 XAML 語言定義的概念[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]內容屬性。  可在物件語法中使用的每個類別都能有一個 XAML 內容屬性。  若要將屬性宣告為類別的 XAML 內容屬性，請將 <xref:System.Windows.Markup.ContentPropertyAttribute> 套用為類別定義的一部分。  將所要的 XAML 內容屬性 \(Property\) 的名稱指定為屬性 \(Attribute\) 中的 <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A>。  指定屬性做為字串名稱，不是以反映的建構類似<xref:System.Reflection.PropertyInfo>。  
  
 您可以將集合屬性 \(Property\) 指定為 XAML 內容屬性。  如此一來，該屬性的使用方式就變成是物件項目可有一個或多個子項目，中間沒有任何集合物件項目或屬性項目標記。  這些項目接著會視為是 XAML 內容屬性的值，並會加入到支援的集合執行個體中。  
  
 某些現有的 XAML 內容屬性使用的屬性型別`物件`。  這會啟用可接受基本值 \(例如 <xref:System.String>\) 以及接受單一參考物件值的 XAML 內容屬性。  如果遵循此模型，您的型別會負責判斷型別以及處理可能的型別。  <xref:System.Object> 內容型別通常是用來支援將物件當做字串加入 \(這會接收預設展示處理\) 的簡單用法，或加入指定非預設展示或額外資料之物件內容的進階用法。  
  
<a name="Serializing"></a>   
## 序列化 XAML  
 針對特定的案例，例如，如果您是控制項作者，您也可以確保它可以具現化在 XAML 中任何物件表示也序列化回相同的 XAML 標記。  此序列化作業的要求不在本主題討論之列。  請參閱 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md) 和 [項目樹狀結構和序列化](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md)。  
  
## 請參閱  
 [XAML 概觀 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [基底項目概觀](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [XAML 載入和相依性屬性](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)