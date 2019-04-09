---
title: WPF 的 XAML 和自訂類別
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: e71946ec06eb1b4c75f30084dfdb863d8e3b093e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122352"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF 的 XAML 和自訂類別
[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 架構中所實作的 XAML 支援使用任何 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 語言定義自訂類別或結構，然後使用 XAML 標記來存取該類別。 您可以在相同的標記檔案內混用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 定義的類型與您的自訂類型，方法一般是透過將自訂類型對應至 XAML 命名空間前置詞。 本主題討論自訂類別必須滿足才能用作 XAML 項目的需求。  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>應用程式或組件中的自訂類別  
 可以使用兩種不同的方式來定義 XAML 中所使用的自訂類別︰在程式碼後置或產生主要 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式的其他程式碼內，或作為不同組件中的類別，例如用作類別庫的可執行檔或 DLL。 所有這些方法都會有特定優缺點。  
  
-   建立類別庫的優點是可以跨許多不同的可能應用程式來共用任何這類自訂類別。 不同的程式庫也方便控制應用程式的版本控制問題，並簡化如何建立所要類別用法作為 XAML 頁面上根項目的類別。  
  
-   在應用程式中定義自訂類別的優點在於這項技巧相當簡單，並將在引進主要應用程式可執行檔以外的個別組件時所遇到的部署和測試問題降到最少。  
  
-   不論定義於相同或不同組件中，都需要在 CLR 命名空間與 XML 命名空間之間對應自訂類別，才能當成項目用於 XAML 中。 請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>作為 XAML 項目之自訂類別的需求  
 若要可具現化為物件項目，您的類別必須符合下列需求︰  
  
-   自訂類別必須是公用，並支援預設 (無參數) 公用建構函式 (如需結構相關附註，請參閱下節)。  
  
-   自訂類別不能是巢狀類別。 巢狀類別以及其在具有其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 (或) XAML 功能之一般 CLR 使用語法介面中的「點」，例如附加屬性。  
  
 除了啟用物件項目語法之外，您的物件定義也會啟用採用該物件作為值類型之任何其他公用屬性的屬性項目語法。 這是因為物件現在可以具現化為物件項目，並且可以填入這類屬性的屬性項目值。  
  
### <a name="structures"></a>結構  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，一律可以使用 XAML 來建構可定義為自訂類型的結構。這是因為 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 編譯器隱含建立結構的預設建構函式，而結構會將所有屬性值初始化為其預設值。 在某些情況下，您可能不想要結構的預設建構行為和 (或) 物件項目用法。 這可能是因為結構是要填入值並在概念上當成聯集運作；其中，所包含的值可能會有互斥解譯，因此無法設定其屬性。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]這類結構的範例是<xref:System.Windows.GridLength>。 一般而言，這類結構應該實作類型轉換子；如此，使用可建立結構值的不同解譯或模式的字串慣例，即可透過屬性形式表示這些值。 此結構也應該透過非預設建構函式進行程式碼建構來公開類似行為。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>作為 XAML 屬性之自訂類別的屬性需求  
 屬性必須參考值類型 (例如基本類型)，或針對具有預設建構函式或 XAML 處理器可存取之專用類型轉換子的類型來使用類別。 在 CLR XAML 實作中，XAML 處理器尋找這類轉換子透過原生支援的語言基本類型，或藉由套用<xref:System.ComponentModel.TypeConverterAttribute>為型別或成員支援類型定義中  
  
 或者，屬性可以參考抽象類別類型或介面。 針對抽象類別或介面，XAML 剖析預期屬性值必須填入可實作介面的實體類別執行個體，或衍生自抽象類別之類型的執行個體。  
  
 屬性可以宣告於抽象類別上，但只可以設定於衍生自抽象類別的實值類別上。 這是因為建立類別的物件項目只需要類別上的公用預設建構函式。  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter 啟用屬性語法  
 如果您在類別層級提供專用屬性化類型轉換子，則套用的類型轉換可啟用任何需要具現化該類型之屬性 (property) 的屬性 (attribute) 語法。 類型轉換子不會啟用類型的物件項目用法；只有該類型的預設建構函式存在時，才可啟用物件項目用法。 因此，除非類型本身也支援物件項目語法，否則已啟用類型轉換子的屬性一般無法用於屬性語法。 這個的例外狀況是您可以指定屬性項目語法，但讓屬性項目包含字串。 該用法基本上等同於屬性語法用法，而這類用法不常見，除非需要屬性值的更強固空白字元處理。 例如，以下是取用字串的屬性 (property) 項目用法以及對等的屬性 (attribute) 用法︰  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 屬性允許屬性語法，但透過 XAML 不允許包含物件元素的屬性項目語法的範例是採用的各種屬性<xref:System.Windows.Input.Cursor>型別。 <xref:System.Windows.Input.Cursor>類別具有專用的類型轉換子<xref:System.Windows.Input.CursorConverter>，但不會公開預設建構函式，因此<xref:System.Windows.FrameworkElement.Cursor%2A>屬性可以設定只透過屬性語法即使實際<xref:System.Windows.Input.Cursor>型別是參考型別。  
  
### <a name="per-property-type-converters"></a>每個屬性的類型轉換子  
 或者，屬性本身可以宣告屬性層級的類型轉換子。 這可讓具現化內嵌屬性之型別的物件處理傳入的字串值的屬性做為輸入 「 迷你語言 」<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>作業根據適當的型別。 這項作業一般是要提供方便使用的存取子，而不是在 XAML 中設定屬性的唯一方法。 不過，您也可使用屬性的類型轉換子，其中，您要使用不提供預設建構函式或屬性化類型轉換子的現有 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 類型。 從範例[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]API 會採用特定屬性<xref:System.Globalization.CultureInfo>型別。 在此情況下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用現有的 Microsoft.NET Framework<xref:System.Globalization.CultureInfo>類型更恰當地處理舊版架構中所使用的相容性和移轉案例，但<xref:System.Globalization.CultureInfo>類型不支援必要建構函式或類型層級類型轉換用作 XAML 屬性值直接。  
  
 只要公開具有 XAML 用法的屬性，特別的是，如果您是控制項作者，則應該強烈考慮支援該屬性與相依性屬性。 這特別是當您使用現有[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]實作的 XAML 處理器資源，因為您可以使用，以改善效能<xref:System.Windows.DependencyProperty>備份。 相依性屬性會公開使用者預期 XAML 可存取屬性之屬性的屬性系統功能。 這包括動畫、資料繫結和樣式支援這類功能。 如需詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)和 [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)。  
  
### <a name="writing-and-attributing-a-type-converter"></a>撰寫並屬性化類型轉換子  
 您偶爾會需要撰寫自訂<xref:System.ComponentModel.TypeConverter>衍生類別，以提供屬性類型的類型轉換。 如需有關如何衍生和建立型別轉換子可支援 XAML 用法，以及如何套用<xref:System.ComponentModel.TypeConverterAttribute>，請參閱 < [TypeConverters 和 XAML](typeconverters-and-xaml.md)。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>自訂類別事件上 XAML 事件處理常式屬性語法的需求  
 若要可以用作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 事件，則必須在支援預設建構函式的類別上，或可在衍生類別上存取事件的抽象類別上，將事件公開為公用事件。 為了方便當成路由事件，您[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]事件應該實作明確`add`並`remove`方法，以新增和移除處理常式[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]事件簽章並將這些處理常式來<xref:System.Windows.UIElement.AddHandler%2A>和<xref:System.Windows.UIElement.RemoveHandler%2A>方法。 這些方法會在附加事件的執行個體上新增或移除路由事件處理常式存放區的處理常式。  
  
> [!NOTE]
>  可註冊處理常式直接使用的路由事件<xref:System.Windows.UIElement.AddHandler%2A>，以及故意不定義[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]公開路由的事件的事件。 通常不會建議您使用此方式，因為事件不會啟用用於附加處理常式的 XAML 屬性語法，而且產生的類別將針對該類型的功能提供較不容易明瞭的 XAML 檢視。  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>撰寫集合屬性  
 採用集合類型的屬性具有 XAML 語法，可讓您指定新增至集合的物件。 此語法有兩個值得注意的功能。  
  
-   本身為集合物件的物件不需要指定於物件項目語法中。 只要在 XAML 中指定採用集合類型的屬性，該集合類型的存在就是隱含的。  
  
-   標記中集合屬性的子項目會處理成集合的成員。 一般而言，是透過 `Add` 這類清單/字典方法，或透過索引子，執行對集合成員的程式碼存取。 但是 XAML 語法不支援方法或索引子 (例外狀況：XAML 2009 可支援的方法，但使用 XAML 2009 限制可能的 WPF 用法;請參閱[XAML 2009 語言功能](../../xaml-services/xaml-2009-language-features.md))。 集合很明顯是建置項目樹狀結構的很常見需求，而且您需要某個方法在宣告式 XAML 中填入這些集合。 因此，會處理集合屬性的子項目，方法是將它們新增至為集合屬性類型值的集合。  
  
 .NET Framework XAML 服務實作，因此 WPF XAML 處理器會使用下列構成集合屬性的定義。 屬性的屬性類型必須實作下列其中一項：  
  
-   實作<xref:System.Collections.IList>。  
  
-   Implements<xref:System.Collections.IDictionary>或泛型對等項目 (<xref:System.Collections.Generic.IDictionary%602>)。  
  
-   衍生自<xref:System.Array>(如需 XAML 中陣列的詳細資訊，請參閱[X:array 標記延伸](../../xaml-services/x-array-markup-extension.md)。)  
  
-   Implements <xref:System.Windows.Markup.IAddChild> (所定義的介面[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)])。  
  
 CLR 中的所有這些類型都會有 `Add` 方法，而 XAML 處理器使用此方法，在建立物件圖形時，將項目新增至基礎集合。  
  
> [!NOTE]
>  泛型`List`並`Dictionary`介面 (<xref:System.Collections.Generic.IList%601>並<xref:System.Collections.Generic.IDictionary%602>) 不支援的集合偵測[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 處理器。 不過，您可以使用<xref:System.Collections.Generic.List%601>類別做為基底類別，因為它會實作<xref:System.Collections.IList>直接，或是<xref:System.Collections.Generic.Dictionary%602>做為基底類別，因為它會實作<xref:System.Collections.IDictionary>直接。  
  
 當您宣告採用集合的屬性時，請注意如何在類型的新執行個體中初始化該屬性值。 如果您未將屬性實作為相依性屬性，則讓屬性使用可呼叫集合類型建構函式的支援欄位就已足夠。 如果您的屬性是相依性屬性，則可能需要將集合屬性初始化為預設類型建構函式的一部分。 這是因為相依性屬性會從中繼資料取得其預設值，而且您通常不想要集合屬性的初始值成為靜態共用集合。 一個包含類型執行個體應該要有一個集合執行個體。 如需詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。  
  
 您可以實作集合屬性的自訂集合類型。 因為將集合屬性視為隱含，所以自訂集合類型不需要提供預設建構函式，即可隱含地用於 XAML 中。 不過，您可以選擇性地提供集合類型的預設建構函式。 這是相當實用的做法。 除非您提供預設建構函式，否則無法將集合明確宣告為物件項目。 部分標記作者可能會想要將明確集合視為標記樣式。 此外，當您建立新物件以使用集合類型作為屬性值時，預設建構函式可以簡化初始化需求。  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>宣告 XAML 內容屬性  
 XAML 語言定義 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 內容屬性的概念。 每個可用於物件語法中的類別都只能有一個 XAML 內容屬性。 若要宣告類別的 XAML 內容屬性的屬性，套用<xref:System.Windows.Markup.ContentPropertyAttribute>為類別定義的一部分。 指定做為預期的 XAML 內容屬性的名稱<xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A>屬性中。 屬性會指定為字串名稱，不是反映建構這類<xref:System.Reflection.PropertyInfo>。  
  
 您可以將集合屬性指定為 XAML 內容屬性。 這會導致使用該屬性，藉此，物件項目可以有一或多個子項目，而不需要任何中介集合物件項目或屬性項目標記。 這些項目則是視為 XAML 內容屬性的值，並新增至支援集合執行個體。  
  
 一些現有的 XAML 內容屬性使用 `Object` 屬性類型。 這可讓內容可以採用基本的屬性值，例如 XAML<xref:System.String>以及採用單一參考物件值。 如果您遵循此模型，則您的類型會負責類型判斷，以及可能類型的處理。 常見的原因<xref:System.Object>內容型別是為了支援這兩個簡單的方法加入物件內容當做字串 （它會接收預設呈現處理），或進階的方式來新增的物件指定非預設呈現的內容或其他資料。  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>序列化 XAML  
 在特定情況下，例如，如果您是控制項作者，則可能也要確保可在 XAML 中具現化的任何物件表示也都可以序列化回對等的 XAML 標記。 本主題未描述序列化需求。 請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)和[項目樹狀結構和序列化](element-tree-and-serialization.md)。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [基底項目概觀](base-elements-overview.md)
- [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)
