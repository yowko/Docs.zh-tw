---
title: XAML 語法詳細資料
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
ms.openlocfilehash: d98141c0ad96ef1bd3958ae8d3166aedde76f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-syntax-in-detail"></a>XAML 語法詳細資料
本主題中定義的詞彙用於描述 XAML 語法的項目。 這些條款常用的這份文件，WPF 文件的其餘具體而言，適用於其他使用 XAML 或啟用 System.Xaml 層級的 XAML 語言支援的基本 XAML 概念的架構。 本主題詳述主題所介紹的基本術語[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML 語言規格  
 此處定義的 XAML 語法術語也定義，或者參考 XAML 語言規格中。 XAML 是 XML 為基礎的語言會遵循及基礎 XML 結構的規則。 一些用語所共用，或描述 XML 語言或 XML 文件物件模型時常用的詞彙為基礎。  
  
 如需 XAML 語言規格的詳細資訊，請下載[ \[MS-XAML\] ](http://go.microsoft.com/fwlink/?LinkId=114525)從 Microsoft 下載中心取得。  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML 和 CLR  
 XAML 是一種標記語言。 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、 為隱含的名稱可讓執行階段執行。 XAML 不是單獨使用其中一個直接由 CLR 執行階段的常見語言。 相反地，您可以將 XAML 視為支援它自己的型別系統。 特定的 XAML 剖析系統，以供 WPF 是建置在 CLR 與 CLR 型別系統。 XAML 類型會對應至 CLR 型別，wpf XAML 剖析時，具現化的執行的階段表示法。 基於這個理由，即使對等的語法中的討論區 XAML 語言規格不相符的語法，在這份文件中討論的其餘部分時，將包含 CLR 型別系統中，參考。 （每 XAML 語言規格層級中，XAML 類型無法對應到任何其他型別系統，沒有是 CLR 中，但是，就必須建立和使用不同的 XAML 剖析器。）  
  
#### <a name="members-of-types-and-class-inheritance"></a>型別和類別繼承的成員  
 屬性和事件，您會看到顯示的 XAML 成員為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類型通常都繼承自基底型別。 例如，請考量以下範例： `<Button Background="Blue" .../>`。 <xref:System.Windows.Controls.Control.Background%2A>屬性不是立即宣告的屬性上<xref:System.Windows.Controls.Button>類別，如果您要查看的類別定義，反映結果或文件。 相反地，<xref:System.Windows.Controls.Control.Background%2A>繼承自基底<xref:System.Windows.Controls.Control>類別。  
  
 類別的繼承行為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 項目是重要出發，從結構描述強制執行的解譯 XML 標記。 類別繼承會變得複雜，特別是當中繼的基底類別是抽象類別，或當牽涉到介面時。 這是一個原因的 XAML 項目和其所允許的屬性集是難以表示精確且完全使用結構描述型別，通常用於[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]程式設計，例如 DTD 或 XSD 格式。 另一個原因是該擴充性和 XAML 語言本身的類型對應功能不允許的類型和成員的任何固定表示法的完整性。  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>物件元素語法  
 *物件項目語法*是藉由宣告的 XML 項目執行個體化 CLR 類別或結構的 XAML 標記語法。 這個語法類似於其他標記語言，例如 HTML 項目語法。 物件項目語法的開頭是左角括號 (\<)，後面接著立即在類別或結構所產生的型別名稱。 零個或多個空格，可以遵循的型別名稱，以及零個或多個屬性也可以宣告物件項目上有一或多個空格分隔每個屬性名稱 = 「 值 」 配對。 最後，下列其中一項必須為真：  
  
-   此項目和標記必須先關閉以正斜線 （/） 後面緊接跟著右角括弧 (>)。  
  
-   開頭標記必須完成的右角括號 (>)。 其他物件項目、 屬性項目或內部文字，可以遵循的開頭標記。 完全內容可能包含以下通常受到物件模型的項目。 對等項目結尾標記的物件項目也必須位於正確的巢狀，並使用其他的開頭和結尾標記配對之間取得平衡。  
  
 由.NET 實作 XAML 有一組對應物件項目型別，屬性至屬性或事件和 XAML 命名空間到 CLR 命名空間加上組件的規則。 如需 WPF 和.NET Framework，XAML 物件項目對應至[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]參考的組件中所定義的型別和屬性會對應至這些型別的成員。 當您參考的 CLR 型別，在 XAML 中時，您可以存取該型別繼承的成員。  
  
 例如，下列範例是會具現化的新執行個體的物件項目語法<xref:System.Windows.Controls.Button>類別，以及也會指定<xref:System.Windows.FrameworkElement.Name%2A>屬性和該屬性的值：  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 下列範例是物件也包含 XAML 內容屬性語法的項目語法。 中包含的內部文字會用來設定<xref:System.Windows.Controls.TextBox>XAML 內容屬性， <xref:System.Windows.Controls.TextBox.Text%2A>。  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>內容模型  
 類別可能會以 XAML 物件項目語法，以支援使用，但是該項目只正常運作的應用程式或頁面放在整體內容模型或項目樹狀結構之預期的位置時。 例如，<xref:System.Windows.Controls.MenuItem>通常只可出現的子系<xref:System.Windows.Controls.Primitives.MenuBase>衍生類別，例如<xref:System.Windows.Controls.Menu>。 內容模型的特定項目會記載為控制項和其他類別頁面上的 「 註解的一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別，可以用做為 XAML 項目。  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>物件元素的屬性  
 在 XAML 中的屬性會設定各種可能的語法。 何種語法可用於特定的屬性而異，根據您要設定之屬性的基礎類型系統特性。  
  
 藉由設定屬性的值，您加入功能或特性物件存在於執行的階段物件圖形中。 從物件項目所建立物件的初始狀態為基礎的預設建構函式的行為。 一般而言，應用程式將使用完全預設執行任何的個體指定的物件以外的項目。  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>屬性 (Attribute) 語法 (屬性(Property))  
 屬性語法是藉由宣告屬性的現有物件項目上設定屬性值的 XAML 標記語法。 屬性名稱必須符合 CLR 成員名稱的類別之備份的相關物件元素的屬性。 指派運算子 （=） 後面的屬性名稱。 屬性值必須括在引號內的字串。  
  
> [!NOTE]
>  您可以使用替代的引號，放置在屬性中的常值引號。 例如您可以使用單引號來宣告包含在其中的雙引號字元的字串。 不論您使用單引號或雙引號時，您應該使用相符的配對，來開啟和關閉屬性值字串。 也有逸出序列或其他技術可用來解決任何特定的 XAML 語法所加諸的字元限制。 請參閱[XML 字元實體和 XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)。  
  
 若要設定透過屬性的語法，屬性必須是公用的而且必須可寫入。 在支援類型系統中屬性的值必須是實值類型，或必須可具現化或存取相關時，XAML 處理器所參考的參考型別備份類型。  
  
 WPF XAML 事件之事件的參考做為屬性名稱必須具有公用和具有公用委派。  
  
 屬性或事件必須是類別或結構所包含的物件項目執行個體化的成員。  
  
### <a name="processing-of-attribute-values"></a>屬性值的處理  
 XAML 處理器會處理包含在開頭和結尾引號的字串值。 屬性，預設的處理行為是取決於基礎的 CLR 屬性的類型。  
  
 下列程式碼，其中會填入屬性值使用此處理順序：  
  
1.  如果 XAML 處理器發現了大括號或物件項目衍生自<xref:System.Windows.Markup.MarkupExtension>、 然後參考的標記延伸會先評估而不是處理字串形式的值，標記延伸模組所傳回的物件做為值。 在許多情況下的標記延伸模組所傳回的物件會參考現有的物件或評估延後到執行階段，並不是新具現化的物件的運算式。  
  
2.  如果屬性宣告的屬性化<xref:System.ComponentModel.TypeConverter>，或在宣告該屬性的值類型與屬性化<xref:System.ComponentModel.TypeConverter>、 屬性的字串值送出至做為轉換輸入中，類型轉換器和轉換器會傳回新的物件執行個體。  
  
3.  如果沒有任何<xref:System.ComponentModel.TypeConverter>，嘗試直接轉換成屬性型別。 這個最後一個層級是直接在 XAML 語言基本類型或列舉型別 （剖析器再存取相符的值） 的具名常數的名稱檢查之間的剖析器原生值轉換。  
  
#### <a name="enumeration-attribute-values"></a>列舉型別屬性值  
 列舉型別在 XAML 中的處理的內容本質上並 XAML 剖析器，以及藉由指定列舉的具名常數的其中一個的字串名稱應指定列舉的成員。  
  
 原生的行為是屬性值的字串處理，並將它解析為其中一個列舉值 （attribute） 的列舉值。 您不指定格式列舉*列舉*。*值*、 與您在程式碼。 相反地，只指定*值*，和*列舉*由您要設定屬性的型別推斷。 如果您指定屬性在*列舉*。*值*表單中，它將不會解析正確。  
  
 若是旗列舉型別，行為根據<xref:System.Enum.Parse%2A?displayProperty=nameWithType>方法。 您可以使用逗號區隔每個值指定多個旗列舉值。 不過，您無法結合不旗標式的列舉值。 比方說，您無法使用逗號語法來嘗試建立<xref:System.Windows.Trigger>，充當 （attribute） 的列舉型別的多個條件：  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 在 WPF 中於旗列舉型別支援可在 XAML 中設定的屬性。 不過，這類列舉是<xref:System.Windows.Media.StyleSimulations>。 您執行個體，可以使用逗點分隔旗屬性語法來修改的 「 備註 」 中所提供的範例<xref:System.Windows.Documents.Glyphs>類別;`StyleSimulations = "BoldSimulation"`可能會變得`StyleSimulations = "BoldSimulation,ItalicSimulation"`。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> 是另一個屬性可在其中指定一個以上的列舉值。 不過，這個屬性剛好是特殊案例中，因為<xref:System.Windows.Input.ModifierKeys>列舉型別支援它自己的型別轉換子。 修飾詞的類型轉換器會使用加號 （+），做為分隔符號，而不是逗號 （，）。 此轉換支援更傳統的語法，以代表索引鍵的組合，在 Microsoft Windows 程式設計中，例如 「 Ctrl + Alt。  
  
### <a name="properties-and-event-member-name-references"></a>屬性和事件成員名稱參考  
 在指定屬性時，您可以參考任何屬性或您所包含的物件項目針對具現化的 CLR 型別成員的事件。  
  
 或者，您可以參考附加的屬性或附加的包含物件項目獨立事件。 （附加的屬性會在後續的章節中討論）。  
  
 您也可以名稱是透過預設命名空間存取使用的所有物件的任何事件*typeName*。*事件*部分限定的名稱; 此附加的路由事件的處理常式的支援此處理常式要處理事件的路由從子項目，但父項目也沒有該事件在其成員資料表中的語法。 這個語法類似於附加的事件的語法，但這裡的事件不是，則為 true 的附加的事件。 相反地，您會參考具有限定名稱的事件。 如需詳細資訊，請參閱[路由傳送事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 某些情況下，有時會提供屬性名稱做為屬性，而不是屬性名稱的值。 該屬性的名稱也可以包含辨識符號，例如表單中指定的屬性*ownerType*。*dependencyPropertyName*。 在 XAML 中撰寫樣式或範本時，常會使用此案例。 提供做為屬性值的屬性名稱的處理規則不同，而且依所設定的屬性類型或特定 WPF 子系統的行為會控管。 如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
 屬性值描述屬性屬性關聯性時的屬性名稱的另一個使用方式。 這項功能會使用資料繫結和分鏡腳本的目標，且已啟用<xref:System.Windows.PropertyPath>類別和其型別轉換子。 查閱語意的更完整描述，請參閱[PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)。  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>屬性元素語法  
 *屬性項目語法*是一個值稍有基本的 XML 語法規則的項目與值的語法。 在 XML 中，屬性值的既定的字串，唯一可能的變化是正在使用哪一種字串編碼格式。 在 XAML 中，您可以指定其他物件項目是屬性的值。 屬性項目語法會啟用這項功能。 而不是做為屬性項目標記中所指定的屬性，指定的屬性是使用開啟元素標記*elementTypeName*。*propertyName*表單內，所指定屬性的值和屬性項目已關閉。  
  
 具體來說，語法開頭是左角括號 (\<)，後面接著立即類別或結構屬性項目語法內所包含的型別名稱。 這後面緊接跟著單一點 （.），然後由屬性的名稱，然後的右角括號 (>)。 如同屬性語法，該屬性必須存在於指定的類型宣告的公用成員。 要指派給屬性的值會包含在屬性項目。 一般而言，指定以一個或多個物件元素的值，指定做為值的物件是案例，因為該屬性的項目語法為了位址。 最後，指定相同的對等的結尾標記*elementTypeName*。*propertyName*組合必須，以提供適當的巢狀結構和平衡與其他項目標籤。  
  
 例如，下列是屬性的項目語法<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 屬性項目內的值也指定為內部文字，在案例中所指定的屬性類型的基本值類型，例如<xref:System.String>，或列舉型別指定名稱的位置。 這些兩種用法是稍微不常見，因為每個案例也可以使用簡單的屬性語法。 屬性項目填入字串的其中一個案例是針對不是 XAML 內容屬性，但仍會用於 UI 文字表示法的內容，並出現在該 UI 文字中所需的特定的空白項目，例如換行字元。 屬性語法無法保留換行字元，但可以屬性項目語法，只要保留重要的空白字元為作用中 (如需詳細資訊，請參閱[XAML 中的空白字元處理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md))。 另一個案例是讓[X:uid 指示詞](../../../../docs/framework/xaml-services/x-uid-directive.md)可以套用至屬性項目和值應該當地語系化 WPF 中，輸出 BAML 或其他技術，因此標記內的值。  
  
 屬性項目不會呈現 WPF 邏輯樹狀結構中。 屬性項目是只設定屬性，特定語法，而且不具有執行個體或物件支援的項目。 (如邏輯樹狀結構的詳細資訊，請參閱[中 WPF 樹狀架構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。)  
  
 對於屬性和屬性的項目語法其中受支援的屬性，兩個語法通常具有相同的結果，雖然微妙例如空白字元處理方式稍之間的語法。  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>集合語法  
 XAML 規格要求 XAML 處理器實作識別其中實值型別是集合的屬性。 在.NET 中的一般 XAML 處理器實作根據 managed 程式碼與 CLR，用來識別集合型別，透過下列其中一項：  
  
-   型別會實作<xref:System.Collections.IList>。  
  
-   型別會實作<xref:System.Collections.IDictionary>。  
  
-   型別衍生自<xref:System.Array>(如需 XAML 中的陣列的詳細資訊，請參閱[X:array 標記延伸](../../../../docs/framework/xaml-services/x-array-markup-extension.md)。)  
  
 如果屬性的型別是集合，然後推斷的集合型別不必做為物件元素的標記中指定。 相反地，即將成為的項目集合中的項目會指定為一或多個屬性項目的子項目。 每個這類項目物件評估在載入期間，以及加入至集合，藉由呼叫`Add`默示集合的方法。 例如，<xref:System.Windows.Style.Triggers%2A>屬性<xref:System.Windows.Style>採用特製化的集合型別<xref:System.Windows.TriggerCollection>，它會實作<xref:System.Collections.IList>。 不需要具現化<xref:System.Windows.TriggerCollection>物件標記中的項目。 相反地，您指定一個或多個<xref:System.Windows.Trigger>做為項目內的項目`Style.Triggers`屬性項目，其中<xref:System.Windows.Trigger>（或衍生的類別） 是預期的項目類型的強型別和隱含的類型<xref:System.Windows.TriggerCollection>。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 屬性可以是集合型別以及該類型的 XAML 內容屬性，並且衍生型別，本主題的下一節中討論。  
  
 隱含的集合項目邏輯樹狀結構表示法中建立的成員，即使它不會顯示為元素標記中。 父類型的建構函式通常會為集合的其中一個內容中，執行具現化，一開始是空的集合會成為物件樹狀結構的一部分。  
  
> [!NOTE]
>  泛型清單和字典介面 (<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>) 不支援集合偵測。 不過，您可以使用<xref:System.Collections.Generic.List%601>類別做為基底類別，因為它實作<xref:System.Collections.IList>直接或<xref:System.Collections.Generic.Dictionary%602>做為基底類別，因為它實作<xref:System.Collections.IDictionary>直接。  
  
 在 集合類型的.NET 參考頁集合的物件項目在故意省略與這個語法是偶爾 XAML 語法 」 一節中標示為隱含的集合語法。  
  
 除了以外的根項目，為另一個元素的子元素會巢狀的 XAML 檔案中的每個物件項目都是真正的項目是一或兩個下列情況下： 其父項目的已隱含的集合屬性的成員或指定的父項目 (XAML 內容屬性將在後續的章節中討論) 的 XAML 內容屬性值的項目。 換句話說，關聯性的父項目和標記頁面中的子項目實際上是單一物件的根目錄，而且根目錄下的每個物件項目為提供的父代，屬性值的單一執行個體或其中一個資料行內的項目lection，同時也是父系的集合型別屬性值。 此單一根目錄概念是常見的 XML，並經常加強的 Api，例如載入 XAML 行為中<xref:System.Windows.Markup.XamlReader.Load%2A>。  
  
 下列範例是集合的物件項目語法 (<xref:System.Windows.Media.GradientStopCollection>) 明確地指定。  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 請注意，它不一定可以明確宣告集合。 例如，嘗試宣告<xref:System.Windows.TriggerCollection>明確中先前所示<xref:System.Windows.Style.Triggers%2A>範例將會失敗。 集合類別必須支援的預設建構函式，明確宣告集合需要和<xref:System.Windows.TriggerCollection>沒有預設建構函式。  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML 內容屬性  
 XAML 內容語法就是在指定的類別才會啟用語法<xref:System.Windows.Markup.ContentPropertyAttribute>做為其類別宣告的一部分。 <xref:System.Windows.Markup.ContentPropertyAttribute>參考該類型的項目 （包括衍生的類別） 的內容屬性的屬性名稱。 時由 XAML 處理器所處理，該物件的 XAML 內容屬性的值會指派任何子項目或找到的開頭和結尾標記的物件項目之間的內部文字。 允許您指定明確的屬性項目之內容的屬性，但這種用法通常不會顯示在 XAML 語法 」 一節中的.NET 參考。 明確/詳細的資訊技術有偶爾標記的清晰度或的標記樣式的值，但通常內容屬性的目的是簡化標記，以便可以直接巢狀直覺的方式為父子式關聯的項目。 屬性項目標記為項目上的其他屬性不被指派為 「 內容 」，每個嚴格的 XAML 語言定義。它們的先前處理 XAML 剖析器的處理順序並不會被視為是 「 內容 」。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>必須是連續的 XAML 內容屬性值  
 XAML 內容屬性的值必須完全之前或任何其他屬性項目之後的完全指定該物件項目。 XAML 內容屬性的值會指定為字串，或一或多個物件是否也是如此。 例如，下列標記不會剖析：  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 基本上，這是不合法因為此語法所使用之內容屬性的屬性項目語法進行明確，然後內容屬性會設定兩次：  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 類似的不合法的範例為內容屬性是集合，並子項目會穿插屬性項目：  
  
```xml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>內容屬性和集合語法合併  
 多個單一物件項目，做為內容，才能接收內容屬性的型別必須特別會是集合型別。 類似於集合型別的屬性項目語法，XAML 處理器必須識別集合型別的型別。 如果項目具有 XAML 內容屬性，XAML 內容屬性的型別是集合，然後隱含的集合型別不需要指定為物件項目在標記中並不需要指定為屬性 el XAML 內容屬性ement。 因此的明顯的內容模型，在標記中現在有一個以上的子元素，指派為內容。 下列是內容語法<xref:System.Windows.Controls.Panel>衍生的類別。 所有<xref:System.Windows.Controls.Panel>衍生的類別建立 XAML 內容屬性設為<xref:System.Windows.Controls.Panel.Children%2A>，這需要類型的值<xref:System.Windows.Controls.UIElementCollection>。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 請注意，都沒有的屬性項目<xref:System.Windows.Controls.Panel.Children%2A>的項目也不<xref:System.Windows.Controls.UIElementCollection>需要在標記中。 這是 XAML 設計功能，以便以遞迴方式包含的項目會定義[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]會更直覺的方式表示的直屬父系-子系項目關聯性，而不插入屬性項目標記與巢狀項目樹狀結構或集合物件。 事實上，<xref:System.Windows.Controls.UIElementCollection>中不能指定明確標記為物件項目所設計。 其唯一用途是做為隱含的集合，因為<xref:System.Windows.Controls.UIElementCollection>不會公開公用預設建構函式，因此無法具現化為物件項目。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>混合屬性項目和物件具有內容屬性之物件中的項目  
 XAML 規格會宣告用來填滿 XAML 物件項目內內容屬性的物件項目必須是連續的並不混合 XAML 處理器可以強制執行。 針對屬性項目及內容混用這項限制由強制執行[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 處理器。  
  
 您可以為物件項目內的第一個立即標記的子物件項目。 然後您可以引入屬性項目。 或者，您可以指定一或多個屬性項目，然後內容，然後再多個屬性的項目。 但是，一旦屬性項目後面的內容，不能進行任何進一步的內容，您只能新增屬性項目。  
  
 此內容 / 屬性項目的順序要求不適用於做為內容的內部文字。 不過，它仍然是因為必要的空白字元很難偵測到以視覺化方式在標記中如果屬性項目會穿插內部文字保留內部文字是連續的好的標記樣式。  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML 命名空間  
 指定 XAML 命名空間的預設 XAML 命名空間以外任何上述語法範例。 在一般[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，預設 XAML 命名空間指定為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]命名空間。 您可以指定非預設 XAML 命名空間的 XAML 命名空間，並仍然使用類似的語法。 但是，任何位置類別名為無法存取預設 XAML 命名空間中的類別名稱前面必須有的 XAML 命名空間前置詞對應到對應的 CLR 命名空間。 例如，`<custom:Example/>`物件具現化的執行個體的項目語法`Example`類別，先前來對應 CLR 命名空間包含該類別 （和可能的外部組件資訊，包含支援的型別）`custom`前置詞。  
  
 如需 XAML 命名空間的詳細資訊，請參閱[XAML 命名空間和 WPF XAML 命名空間對應](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>標記延伸  
 XAML 定義標記延伸，以程式設計的實體，可讓從字串屬性值或物件項目，一般 XAML 處理器處理逸出，並會延後至支援類別處理。 識別標記延伸是 XAML 處理器時，使用屬性語法是左大括號 （{}），後面接著右大括號 （}） 以外的任何字元的字元。 第一個字串後面的左大括號必須參考類別，提供特定的擴充功能的行為，參考可能會略過子字串"Extension"子字串是否為 true 的類別名稱的一部分。 因此，可能會出現一個空格，，然後每個後續字元做為輸入的延伸模組實作中，直到遇到右大括號。  
  
 .NET XAML 實作會使用<xref:System.Windows.Markup.MarkupExtension>抽象類別，做為所有支援之標記延伸模組的基礎[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以及其他架構或技術。 標記延伸的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]特別實作通常要提供一種方式來參照其他現有的物件，或為延後將會在執行階段評估的物件參考。 例如，簡單的 WPF 資料繫結透過指定`{Binding}`來取代，通常會採用特定的屬性值的標記延伸。 許多 WPF 標記延伸可讓其中屬性的語法不否則可能是屬性的屬性語法。 例如，<xref:System.Windows.Style>物件是相當複雜類型，其中包含巢狀的一連串的物件和屬性。 為中的資源通常會定義 WPF 中的樣式<xref:System.Windows.ResourceDictionary>，然後透過要求資源的兩個 WPF 標記延伸的其中一個參考。 標記延伸會延後評估的資源查閱的屬性值，並可讓您提供的值<xref:System.Windows.FrameworkElement.Style%2A>屬性，取得型別<xref:System.Windows.Style>，請在屬性語法，如下列範例所示：  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 在這裡，`StaticResource`識別<xref:System.Windows.StaticResourceExtension>提供標記延伸實作類別。 下一個字串`MyStyle`做為非預設的輸入<xref:System.Windows.StaticResourceExtension>建構函式，從擴充字串的參數會要求宣告<xref:System.Windows.ResourceKey>。 `MyStyle` 必須是[X:key](../../../../docs/framework/xaml-services/x-key-directive.md)值<xref:System.Windows.Style>定義為資源。 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)使用量要求資源用來提供<xref:System.Windows.Style>透過靜態資源查閱邏輯，在載入時間屬性值。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。 如需參考的標記延伸和其他 XAML 程式設計的一般的.NET XAML 實作中啟用的功能，請參閱[XAML 命名空間 （x:）語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。 WPF 專屬標記延伸，請參閱[WPF XAML 延伸](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)。  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>附加屬性  
 附加的屬性是屬性可以讓擁有和特定的類型，所定義的 XAML 中引進的程式設計概念但設定為屬性或屬性項目上的任何項目。 主要案例附加的屬性用來為啟用標記結構要報告其資訊的父項目中的子項目，而不需要廣泛共用的物件模型之間的所有項目。 相反地，附加的屬性可由子元素的報表資訊的父項目。 如需附加的屬性，以及如何建立您自己的目的附加屬性，請參閱 <<c0> [ 附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
 附加的屬性會使用表面上類似於屬性的項目語法的語法，您也指定*typeName*。*propertyName*組合。 有兩個重大差異：  
  
-   您可以使用*typeName*。*propertyName*即使設定透過屬性語法附加的屬性的組合。 附加的屬性會唯一情況的限定屬性名稱是屬性語法的需求。  
  
-   您也可以使用屬性項目語法為附加屬性。 不過，對於典型的屬性項目語法， *typeName*您指定的物件項目，其中包含屬性的項目。 如果您參照到附加的屬性，則*typeName*是附加的屬性，而不包含的物件項目會定義的類別。  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>附加事件  
 附加的事件的另一個 XAML 可以透過特定的類型，定義事件，但可能會處理常式附加的任何物件項目中引進的程式設計概念。 在 WOF 實作中，定義附加的事件的型別通常是靜態的型別定義服務，而且有時候這些附加的事件公開路由的事件的別名中公開服務的類型。 附加事件的處理常式會指定透過屬性的語法。 因為附加的事件，以允許附加事件的擴充屬性語法*typeName*。*eventName*使用方式，其中*typeName*是提供的類別，`Add`和`Remove`附加的事件基礎結構的事件處理常式存取子和*eventName*事件名稱。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML 根項目結構  
 下表顯示一般 XAML 根項目細分，顯示的特定屬性的根項目：  
  
|||  
|-|-|  
|`<Page`|開啟物件的根元素的項目|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|預設值 ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML 命名空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|在 XAML 語言 XAML 命名空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|標記連接到任何程式碼後置的部分類別宣告為部分類別定義|  
|`>`|根物件項目結尾。 物件尚未關閉因為項目包含子項目|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>選擇性的非建議的 Xaml  
 下列章節說明 XAML 用法技術上來說由 XAML 處理器支援，但會產生詳細等級或剩餘人類看得懂的時機的 XAML 檔案會干擾其他美觀問題您開發包含 XAML 來源的應用程式.  
  
### <a name="optional-property-element-usages"></a>選擇性的屬性項目使用方式  
 選擇性的屬性項目使用方式包含明確寫出項目內容的屬性，XAML 處理器會將視為隱含。 例如，當您宣告的內容<xref:System.Windows.Controls.Menu>，您可以選擇明確宣告<xref:System.Windows.Controls.ItemsControl.Items%2A>集合<xref:System.Windows.Controls.Menu>為`<Menu.Items>`屬性項目標記，以及發生每個<xref:System.Windows.Controls.MenuItem>內`<Menu.Items>`，而不是比使用隱含 XAML 處理器的行為，所有子項目的<xref:System.Windows.Controls.Menu>必須<xref:System.Windows.Controls.MenuItem>並放置於<xref:System.Windows.Controls.ItemsControl.Items%2A>集合。 有時候以視覺化方式在標記中所示，釐清物件結構的選擇性的使用方式可以幫助。 或明確的屬性項目用法有時可以避免技術上正常運作，但以視覺化方式令人困惑，例如巢狀的標記延伸模組屬性值內的標記。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完整限定的 typeName.memberName 屬性  
 *TypeName*。*memberName*形成只路由的事件的大小寫比通用屬性實際運作的。 但在其他情況下，該表單是多餘，且您應該避免，如果僅基於標記樣式及可讀性。 在下列範例中，這三個每個參考<xref:System.Windows.Controls.Control.Background%2A>屬性是完全相同：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` 可以運作，因為該屬性的限定的查閱<xref:System.Windows.Controls.Button>成功 (<xref:System.Windows.Controls.Control.Background%2A>繼承自控制項) 和<xref:System.Windows.Controls.Button>物件項目之類別或基底類別。 `Control.Background` 因為<xref:System.Windows.Controls.Control>類別實際定義<xref:System.Windows.Controls.Control.Background%2A>和<xref:System.Windows.Controls.Control>是<xref:System.Windows.Controls.Button>基底類別。  
  
 不過，下列*typeName*。*memberName*表單範例中無法運作，而且會因此顯示加上註解：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> 是另一個衍生的類別<xref:System.Windows.Controls.Control>，而且如果已指定`Label.Background`內<xref:System.Windows.Controls.Label>物件項目，會處理這種使用方式。 不過，因為<xref:System.Windows.Controls.Label>不是類別或基底類別<xref:System.Windows.Controls.Button>，在 XAML 處理器的行為是再處理`Label.Background`為附加屬性。 `Label.Background` 不是可用的附加的屬性，而且這種用法會失敗。  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName 屬性項目  
 如何以類似方式*typeName*。*memberName*形式的運作方式的屬性語法*產生*。*memberName*語法適用於屬性項目語法。 例如，下列語法運作方式：  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 屬性項目，指定做為`Control.Background`即使屬性項目所包含之`Button`。  
  
 但就像*typeName*。*memberName*表單的屬性，*產生*。*memberName*是不佳的樣式，在標記中，而且您應該避免這樣。  
  
## <a name="see-also"></a>另請參閱  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [XAML 命名空間 (x:) 語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)  
 [WPF XAML 延伸](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [TypeConverter 和 XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)  
 [WPF 的 XAML 和自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
