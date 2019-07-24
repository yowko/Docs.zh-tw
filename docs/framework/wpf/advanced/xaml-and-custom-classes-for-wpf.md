---
title: WPF 的 XAML 和自訂類別
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 8b47c43e897004a6c7eb3d2f8b2a2b9bb625e158
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400829"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF 的 XAML 和自訂類別
通用語言執行平臺 (CLR) 架構中所實做的 XAML 支援以任何 common language runtime (CLR) 語言定義自訂類別或結構, 然後使用 XAML 標記存取該類別的功能。 您可以在相同的標記檔案內混用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 定義的類型與您的自訂類型，方法一般是透過將自訂類型對應至 XAML 命名空間前置詞。 本主題討論自訂類別必須滿足才能用作 XAML 項目的需求。  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>應用程式或組件中的自訂類別  
 可以使用兩種不同的方式來定義 XAML 中所使用的自訂類別︰在程式碼後置或產生主要 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式的其他程式碼內，或作為不同組件中的類別，例如用作類別庫的可執行檔或 DLL。 所有這些方法都會有特定優缺點。  
  
- 建立類別庫的優點是可以跨許多不同的可能應用程式來共用任何這類自訂類別。 不同的程式庫也方便控制應用程式的版本控制問題，並簡化如何建立所要類別用法作為 XAML 頁面上根項目的類別。  
  
- 在應用程式中定義自訂類別的優點在於這項技巧相當簡單，並將在引進主要應用程式可執行檔以外的個別組件時所遇到的部署和測試問題降到最少。  
  
- 不論定義於相同或不同組件中，都需要在 CLR 命名空間與 XML 命名空間之間對應自訂類別，才能當成項目用於 XAML 中。 請參閱 [WPF XAML 的 XAML 命名空間和命名空間對應](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>作為 XAML 項目之自訂類別的需求  
 若要可具現化為物件項目，您的類別必須符合下列需求︰  
  
- 自訂類別必須是公用，並支援預設 (無參數) 公用建構函式 (如需結構相關附註，請參閱下節)。  
  
- 自訂類別不能是巢狀類別。 巢狀類別以及其在具有其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 (或) XAML 功能之一般 CLR 使用語法介面中的「點」，例如附加屬性。  
  
 除了啟用物件項目語法之外，您的物件定義也會啟用採用該物件作為值類型之任何其他公用屬性的屬性項目語法。 這是因為物件現在可以具現化為物件項目，並且可以填入這類屬性的屬性項目值。  
  
### <a name="structures"></a>結構  
 您定義為自訂類型的結構, 一律可以在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的 XAML 內進行構造。這是因為 CLR 編譯器會隱含地為結構建立無參數的函式, 以將所有屬性值初始化為其預設值。 在某些情況下，您可能不想要結構的預設建構行為和 (或) 物件項目用法。 這可能是因為結構是要填入值並在概念上當成聯集運作；其中，所包含的值可能會有互斥解譯，因此無法設定其屬性。 這類結構的<xref:System.Windows.GridLength>範例是。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 一般而言，這類結構應該實作類型轉換子；如此，使用可建立結構值的不同解譯或模式的字串慣例，即可透過屬性形式表示這些值。 結構也應該透過非無參數的函式來公開程式碼結構的類似行為。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>作為 XAML 屬性之自訂類別的屬性需求  
 屬性必須參考傳值型別 (例如基本類型), 或針對具有無參數的函式或可存取 XAML 處理器之專用類型轉換器的類型使用類別。 在 CLR XAML 的執行中, XAML 處理器會透過對語言基本類型的原生支援<xref:System.ComponentModel.TypeConverterAttribute>來尋找這類轉換器, 或透過的應用程式來執行支援類型定義中的型別或成員。  
  
 或者，屬性可以參考抽象類別類型或介面。 針對抽象類別或介面，XAML 剖析預期屬性值必須填入可實作介面的實體類別執行個體，或衍生自抽象類別之類型的執行個體。  
  
 屬性可以宣告於抽象類別上，但只可以設定於衍生自抽象類別的實值類別上。 這是因為建立類別的物件專案時, 必須在類別上有公用無參數的函式。  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter 啟用屬性語法  
 如果您在類別層級提供專用屬性化類型轉換子，則套用的類型轉換可啟用任何需要具現化該類型之屬性 (property) 的屬性 (attribute) 語法。 類型轉換器不會啟用類型的物件元素使用方式;只有該類型的無參數函式存在, 才會啟用物件元素的使用方式。 因此，除非類型本身也支援物件項目語法，否則已啟用類型轉換子的屬性一般無法用於屬性語法。 這個的例外狀況是您可以指定屬性項目語法，但讓屬性項目包含字串。 這種用法基本上等同于屬性語法使用方式, 而這種用法並不常見, 除非需要更健全的屬性值的空白字元處理。 例如，以下是取用字串的屬性 (property) 項目用法以及對等的屬性 (attribute) 用法︰  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 允許屬性語法的屬性範例, 但不允許透過 XAML 使用包含物件元素的屬性專案語法, 這是採用<xref:System.Windows.Input.Cursor>類型的各種屬性。 類別具有專用類型轉換器<xref:System.Windows.Input.CursorConverter>, 但不會公開<xref:System.Windows.FrameworkElement.Cursor%2A>無參數的函式, 因此屬性只能透過屬性語法來設定, 即使實際<xref:System.Windows.Input.Cursor>類型是參考型別也是如此。 <xref:System.Windows.Input.Cursor>  
  
### <a name="per-property-type-converters"></a>每個屬性的類型轉換子  
 或者，屬性本身可以宣告屬性層級的類型轉換子。 這會啟用「迷你語言」, 藉由處理屬性的傳入字串值作為以適當類型為基礎之作業的輸入<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> , 來具現化屬性 (inline) 之類型的物件。 這項作業一般是要提供方便使用的存取子，而不是在 XAML 中設定屬性的唯一方法。 不過, 如果您想要使用未提供無參數的函式或屬性化型別轉換器的現有 CLR 型別, 則也可以針對屬性使用類型轉換器。 API 的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]範例是<xref:System.Globalization.CultureInfo>採用類型的某些屬性。 在此情況下[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , 使用現有的 Microsoft <xref:System.Globalization.CultureInfo> .NET Framework 類型來更有效地解決舊版架構中使用的相容性和遷移案例, 但<xref:System.Globalization.CultureInfo>類型不支援必要的可直接當做 XAML 屬性值使用的構造函式或類型層級類型轉換。  
  
 只要公開具有 XAML 用法的屬性，特別的是，如果您是控制項作者，則應該強烈考慮支援該屬性與相依性屬性。 如果您使用現有[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的 XAML 處理器執行, 這特別適用, 因為您可以使用<xref:System.Windows.DependencyProperty>支援來改善效能。 相依性屬性會公開使用者預期 XAML 可存取屬性之屬性的屬性系統功能。 這包括動畫、資料繫結和樣式支援這類功能。 如需詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)和 [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)。  
  
### <a name="writing-and-attributing-a-type-converter"></a>撰寫並屬性化類型轉換子  
 您偶爾會需要撰寫自訂<xref:System.ComponentModel.TypeConverter>的衍生類別, 以提供屬性類型的類型轉換。 如需如何衍生自並建立可支援 XAML 用法的類型轉換器, 以及如何套用的<xref:System.ComponentModel.TypeConverterAttribute>指示, 請參閱[TypeConverters 和 XAML](typeconverters-and-xaml.md)。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>自訂類別事件上 XAML 事件處理常式屬性語法的需求  
 若要以 CLR 事件的形式使用, 必須在支援無參數的函式的類別上, 或在可于衍生類別上存取事件的抽象類別上, 將事件公開為公用事件。 為了方便地當做路由事件使用, 您的 clr 事件應該`add`會執行明確的和`remove`方法, 這會新增和移除 CLR 事件簽章的處理常式, 並將這些處理常式<xref:System.Windows.UIElement.AddHandler%2A>轉送至和<xref:System.Windows.UIElement.RemoveHandler%2A>方法. 這些方法會在附加事件的執行個體上新增或移除路由事件處理常式存放區的處理常式。  
  
> [!NOTE]
>  您可以使用<xref:System.Windows.UIElement.AddHandler%2A>來直接為路由事件註冊處理常式, 並故意不要定義會公開路由事件的 CLR 事件。 通常不會建議您使用此方式，因為事件不會啟用用於附加處理常式的 XAML 屬性語法，而且產生的類別將針對該類型的功能提供較不容易明瞭的 XAML 檢視。  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>撰寫集合屬性  
 採用集合類型的屬性具有 XAML 語法，可讓您指定新增至集合的物件。 此語法有兩個值得注意的功能。  
  
- 本身為集合物件的物件不需要指定於物件項目語法中。 只要在 XAML 中指定採用集合類型的屬性，該集合類型的存在就是隱含的。  
  
- 標記中集合屬性的子項目會處理成集合的成員。 一般而言，是透過 `Add` 這類清單/字典方法，或透過索引子，執行對集合成員的程式碼存取。 但 XAML 語法不支援方法或索引子 (例外狀況:XAML 2009 可以支援方法, 但是使用 XAML 2009 會限制可能的 WPF 使用方式;請參閱[XAML 2009 語言功能](../../xaml-services/xaml-2009-language-features.md))。 集合很明顯是建置項目樹狀結構的很常見需求，而且您需要某個方法在宣告式 XAML 中填入這些集合。 因此，會處理集合屬性的子項目，方法是將它們新增至為集合屬性類型值的集合。  
  
 .NET Framework XAML 服務實作，因此 WPF XAML 處理器會使用下列構成集合屬性的定義。 屬性的屬性類型必須實作下列其中一項：  
  
- Implements <xref:System.Collections.IList>。  
  
- Implements <xref:System.Collections.IDictionary>或泛型對等 (<xref:System.Collections.Generic.IDictionary%602>)。  
  
- 衍生自<xref:System.Array> (如需 XAML 中陣列的詳細資訊, 請參閱[x:Array 標記延伸](../../xaml-services/x-array-markup-extension.md))。  
  
- Implements <xref:System.Windows.Markup.IAddChild> (由定義的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]介面)。  
  
 CLR 中的所有這些類型都會有 `Add` 方法，而 XAML 處理器使用此方法，在建立物件圖形時，將項目新增至基礎集合。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器`List`不`Dictionary`支援泛型<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>介面 (和) 進行集合偵測。 不過, <xref:System.Collections.Generic.List%601>您可以使用類別作為基類, 因為<xref:System.Collections.IList>它會直接執行, 或<xref:System.Collections.Generic.Dictionary%602>當做基類, 因為它會<xref:System.Collections.IDictionary>直接實作為。  
  
 當您宣告採用集合的屬性時，請注意如何在類型的新執行個體中初始化該屬性值。 如果您未將屬性實作為相依性屬性，則讓屬性使用可呼叫集合類型建構函式的支援欄位就已足夠。 如果您的屬性是相依性屬性，則可能需要將集合屬性初始化為預設類型建構函式的一部分。 這是因為相依性屬性會從中繼資料取得其預設值，而且您通常不想要集合屬性的初始值成為靜態共用集合。 一個包含類型執行個體應該要有一個集合執行個體。 如需詳細資訊，請參閱[自訂相依性屬性](custom-dependency-properties.md)。  
  
 您可以實作集合屬性的自訂集合類型。 因為有隱含的集合屬性處理, 所以自訂集合類型不需要提供無參數的函式, 就能以隱含方式在 XAML 中使用。 不過, 您可以選擇性地為集合類型提供無參數的函式。 這是相當實用的做法。 除非您提供無參數的函式, 否則無法將集合明確宣告為 object 元素。 部分標記作者可能會想要將明確集合視為標記樣式。 此外, 當您建立使用集合類型做為屬性值的新物件時, 無參數的函式也可以簡化初始化需求。  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>宣告 XAML 內容屬性  
 XAML 語言定義 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 內容屬性的概念。 每個可用於物件語法中的類別都只能有一個 XAML 內容屬性。 若要將屬性宣告為類別的 XAML 內容屬性, 請<xref:System.Windows.Markup.ContentPropertyAttribute>套用做為類別定義的一部分。 <xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A>在屬性中, 將 [預期的 XAML 內容] 屬性的名稱指定為。 屬性會依名稱指定為字串, 而不是當做反映結構 (例如<xref:System.Reflection.PropertyInfo>)。  
  
 您可以將集合屬性指定為 XAML 內容屬性。 這會導致使用該屬性，藉此，物件項目可以有一或多個子項目，而不需要任何中介集合物件項目或屬性項目標記。 這些項目則是視為 XAML 內容屬性的值，並新增至支援集合執行個體。  
  
 一些現有的 XAML 內容屬性使用 `Object` 屬性類型。 這可讓 XAML 內容屬性使用基本值 (例如<xref:System.String> ), 以及取得單一參考物件值。 如果您遵循此模型，則您的類型會負責類型判斷，以及可能類型的處理。 <xref:System.Object>內容類型的一般原因是支援將物件內容新增為字串的簡單方法 (接收預設的呈現法), 或加入物件內容的先進方法來指定非預設的呈現方式, 或其他資料。  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>序列化 XAML  
 在特定情況下，例如，如果您是控制項作者，則可能也要確保可在 XAML 中具現化的任何物件表示也都可以序列化回對等的 XAML 標記。 本主題未描述序列化需求。 請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)和[項目樹狀結構和序列化](element-tree-and-serialization.md)。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [控制項撰寫概觀](../controls/control-authoring-overview.md)
- [基底項目概觀](base-elements-overview.md)
- [XAML 載入和相依性屬性](xaml-loading-and-dependency-properties.md)
