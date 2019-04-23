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
ms.openlocfilehash: bf4118c6e811f409715b7b6684851b8b3e8bbb25
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298886"
---
# <a name="xaml-syntax-in-detail"></a>XAML 語法詳細資料
本主題定義詞彙，用來說明 XAML 語法的項目。 這些詞彙常用的本文件中，WPF 文件的其餘具體來說，並使用 XAML 或啟用 System.Xaml 層級的 XAML 語言支援的基本 XAML 概念的架構。 本主題會詳述主題所介紹的基本術語[XAML 概觀 (WPF)](xaml-overview-wpf.md)。  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML 語言規格  
 此處定義的 XAML 語法術語也是定義，或在 XAML 語言規格參考。 XAML 是以 XML 為基礎的語言和後續動作，或進一步延伸了 XML 的結構化規則。 一些術語所共用，或為基礎時描述 XML 語言或 XML 文件物件模型的常用術語。  
  
 如需 XAML 語言規格的詳細資訊，請下載[ \[MS XAML\] ](https://go.microsoft.com/fwlink/?LinkId=114525)從 Microsoft 下載中心取得。  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML 和 CLR  
 XAML 是一種標記語言。 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、 依其名稱，可讓執行階段執行為隱含。 XAML 不是單獨使用其中一個通用的語言是直接由 CLR 執行階段。 相反地，您可以將 XAML 做為支援它自己的型別系統。 特定的 XAML 剖析系統，可由 WPF 的基礎 CLR 和 CLR 型別系統。 XAML 類型會對應至 CLR 型別，wpf XAML 剖析時，具現化的執行的階段表示法。 基於這個理由，即使在 XAML 語言規格中的對等語法討論不的語法，在這份文件中討論的其餘部分時，會包含 CLR 型別系統中，參考。 （每個 XAML 語言規格層級中，XAML 型別無法對應到任何其他型別系統，這不一定要在 CLR 中，但這將需要建立和使用不同的 XAML 剖析器。）  
  
#### <a name="members-of-types-and-class-inheritance"></a>類型和類別繼承的成員  
 屬性和事件，因為它們會顯示為 XAML 成員[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類型通常繼承自基底型別。 例如，請考慮這個範例： `<Button Background="Blue" .../>`。 <xref:System.Windows.Controls.Control.Background%2A>屬性不是立即宣告的屬性上<xref:System.Windows.Controls.Button>類別，如果您要查看的類別定義、 反映結果或文件。 相反地，<xref:System.Windows.Controls.Control.Background%2A>繼承自基底<xref:System.Windows.Controls.Control>類別。  
  
 類別繼承行為的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 項目是大的不同，從 XML 標記的結構描述強制執行解譯。 類別繼承會變得複雜，特別是當中繼的基底類別是抽象類別，或涉及介面時。 這是其中一個原因的 XAML 項目和其所允許的屬性集很難代表正確且完整地使用結構描述型別通常用於[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]程式設計，例如 DTD 或 XSD 格式。 另一個原因是該擴充性和類型對應的 XAML 語言功能本身會排除的任何固定的表示法，允許的類型和成員的完整性。  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>物件元素語法  
 *物件元素語法*是具現化 CLR 類別或結構宣告的 XML 元素的 XAML 標記語法。 此語法類似於其他標記語言，例如 HTML 項目語法。 物件元素語法的開頭是左角括號 (\<)，後面的類別或結構所產生的型別名稱。 零個以上的空間可以依照類型名稱，以及零個或多個屬性也可以宣告物件項目上有一或多個空格分隔每個屬性名稱 = 「 值 」 配對。 最後，下列其中一項必須為真：  
  
-   以正斜線 （/） 後面緊接跟著右角括弧 (>)，必須先關閉的項目和標籤。  
  
-   項目的開頭標記必須完成的右角括號 (>)。 其他物件項目、 屬性項目或內部文字，可以依照項目的開頭標記。 確切內容可能包含此處通常受到物件模型的項目。 對等項目結尾標記的物件項目也必須存在，在適當的巢狀結構，並且及其他的開頭和結尾標記組之間取得平衡。  
  
 XAML 由.NET 實作有一組規則，將物件項目對應至型別、 屬性或事件，和 CLR 命名空間加上組件的 XAML 命名空間的屬性。 如需 WPF 和.NET Framework，XAML 物件項目對應至[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]中所定義的類型參考的組件，和屬性會對應至這些類型的成員。 當您參考的 CLR 型別，在 XAML 中時，您會有該型別繼承成員的存取權。  
  
 比方說，下列範例會具現化的新執行個體的物件元素語法<xref:System.Windows.Controls.Button>類別，而且也會指定<xref:System.Windows.FrameworkElement.Name%2A>屬性以及該屬性的值：  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 下列範例是物件元素語法，其中也包含 XAML 內容屬性語法。 內含的內部文字會用以設定<xref:System.Windows.Controls.TextBox>XAML 內容屬性， <xref:System.Windows.Controls.TextBox.Text%2A>。  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>內容模型  
 類別可能會為 XAML 物件元素語法，以支援使用方式，但是該項目將只有正常運作中應用程式或頁面時它會放置在整體內容的模型或項目樹狀結構的預期位置。 例如，<xref:System.Windows.Controls.MenuItem>應該通常只會做為子系<xref:System.Windows.Controls.Primitives.MenuBase>衍生類別，例如<xref:System.Windows.Controls.Menu>。 內容模型的特定項目會記載為部分控制項和其他的類別頁面上的 < 備註 >[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別，可用作 XAML 項目。  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>物件元素的屬性  
 在 XAML 中的屬性會設定各種不同的可能語法。 哪種語法可用於特定的屬性而異，根據您要設定屬性的基礎類型系統特性。  
  
 藉由設定屬性的值，您加入功能或特性物件存在於執行的階段物件圖形中。 從物件項目所建立物件的初始狀態為基礎的預設建構函式行為。 一般而言，您的應用程式會使用完全預設執行任何的個體指定物件以外的項目。  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>屬性 (Attribute) 語法 (屬性(Property))  
 屬性語法是藉由在現有的物件項目上宣告屬性設定屬性值的 XAML 標記語法。 屬性名稱必須符合 CLR 成員名稱的備份相關的物件項目類別的屬性。 指派運算子 （=） 後面的屬性名稱。 屬性值必須以引號括住的字串。  
  
> [!NOTE]
>  您可以使用替代的引號將常值引號內的屬性。 比方說您可以使用單引號做為宣告包含在其中的雙引號字元的字串。 不論您使用單引號或雙引號時，您應該使用相符的配對，來開啟和關閉的屬性值的字串。 也有逸出序列或其他技術可用於解決任何特定的 XAML 語法所加諸的字元限制。 請參閱[XML 字元實體和 XAML](../../xaml-services/xml-character-entities-and-xaml.md)。  
  
 若要設定透過屬性語法，屬性必須是公用的因此必須要能寫入。 在支援型別系統中屬性的值必須是實值類型，或必須可具現化或存取相關時，XAML 處理器所參考的參考型別支援型別。  
  
 WPF XAML 事件物件，參考為屬性名稱必須是公用的並具有公用委派。  
  
 屬性或事件必須是類別或結構所包含的物件項目具現化的成員。  
  
### <a name="processing-of-attribute-values"></a>屬性值的處理  
 由 XAML 處理器處理內含的開頭和結尾引號的字串值。 屬性，預設的處理行為是由基礎的 CLR 屬性的型別決定。  
  
 下列步驟，其中一個會填入的屬性值使用此處理順序：  
  
1. 如果 XAML 處理器遇到大括號或物件項目衍生自<xref:System.Windows.Markup.MarkupExtension>、 然後參考的標記延伸模組會先評估而不是處理字串形式的值和標記延伸模組所傳回的物件做為值。 在許多情況下的標記延伸模組所傳回的物件會參考現有的物件或評估延後到執行階段，並不是新具現化的物件的運算式。  
  
2. 如果未宣告的屬性與屬性化<xref:System.ComponentModel.TypeConverter>，或實值型別，該屬性的宣告與屬性化<xref:System.ComponentModel.TypeConverter>、 屬性的字串值提交給型別轉換子，為轉換的輸入，並轉換子會傳回新的物件執行個體。  
  
3. 如果沒有任何<xref:System.ComponentModel.TypeConverter>，嘗試直接轉換成屬性型別。 此最後一個層級是在 XAML 語言基本類型或在列舉型別 （剖析器再存取相符的值） 中的具名常數的名稱檢查之間的剖析器原生值直接轉換。  
  
#### <a name="enumeration-attribute-values"></a>列舉型別屬性值  
 列舉型別在 XAML 中的處理的本質 XAML 剖析器，以及藉由指定的其中一個列舉的具名常數的字串名稱應指定列舉的成員。  
  
 （attribute） 的列舉值，原生的行為是處理屬性值的字串，並解析為其中一個列舉值。 您未指定格式的列舉型別*列舉型別*。*值*，就像您在程式碼中一樣。 相反地，只指定*值*，並*列舉*由您要設定屬性的型別推斷。 如果您指定的屬性*列舉型別*。*值*表單，它將不會解析正確。  
  
 旗標型列舉，行為會根據<xref:System.Enum.Parse%2A?displayProperty=nameWithType>方法。 您可以指定多個旗標型列舉的值，以逗號分隔每個值。 不過，您無法合併不旗標式的列舉值。 比方說，您無法使用逗點語法，以嘗試建立<xref:System.Windows.Trigger>，處理程式碼 （attribute） 列舉型別的多個條件：  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 支援可在 XAML 中可設定屬性的旗標型列舉很少在 WPF 中的。 不過，一個這類列舉型別是<xref:System.Windows.Media.StyleSimulations>。 您比方說，可以使用逗號分隔的旗標型屬性語法來修改提供的範例中的 < 備註 ><xref:System.Windows.Documents.Glyphs>類別;`StyleSimulations = "BoldSimulation"`可能會變得`StyleSimulations = "BoldSimulation,ItalicSimulation"`。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> 是另一個屬性可以在其中指定一個以上的列舉值。 不過，這個屬性是特殊的情況下，因為<xref:System.Windows.Input.ModifierKeys>列舉可支援它自己的型別轉換子。 修飾詞的類型轉換器會使用加號 （+），做為分隔符號，而不是逗號 （，）。 這項轉換支援更傳統的語法，來代表在 Microsoft Windows 程式設計中，例如"Ctrl + Alt"的索引鍵組合。  
  
### <a name="properties-and-event-member-name-references"></a>屬性和事件成員名稱參考  
 在指定的屬性時，您可以參考任何屬性或以您在包含的物件項目的具現化的 CLR 型別成員的形式存在的事件。  
  
 或者，您可以參考附加的屬性，或附加事件，獨立於包含的物件項目。 （附加的屬性會在後續章節中討論）。  
  
 您也可以將名稱從使用預設命名空間可存取的任何物件的任何事件*typeName*。*事件*部分限定的名稱; 此附加路由事件的處理常式的支援，處理常式的目的是要處理從子元素，但父項目路由事件也沒有該事件成員資料表中的語法。 此語法類似於附加的事件語法，但這裡的事件就不會，則為 true 的附加的事件。 相反地，您會參考具有限定名稱的事件。 如需詳細資訊，請參閱 <<c0> [ 路由事件概觀](routed-events-overview.md)。  
  
 某些情況下，有時會提供屬性名稱做為屬性 (attribute)，而不是屬性名稱的值。 該屬性名稱也可以包含辨識符號，例如在表單中指定的屬性*ownerType*。*dependencyPropertyName*。 在 XAML 中撰寫樣式或範本時，常會使用此案例。 提供做為屬性值的屬性名稱的處理規則不同，而且受到所設定之屬性的類型或特定 WPF 子系統的行為。 如需詳細資訊，請參閱 <<c0> [ 設定樣式和範本](../controls/styling-and-templating.md)。  
  
 屬性名稱的另一個使用方式時，屬性值描述屬性]-[屬性關聯性。 這項功能用於資料繫結，以及分鏡腳本目標，而且會啟用<xref:System.Windows.PropertyPath>類別和其型別轉換子。 查閱語意的更完整說明，請參閱[PropertyPath XAML 語法](propertypath-xaml-syntax.md)。  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>屬性元素語法  
 *屬性元素語法*稍有基本的 XML 語法規則的項目分出來，這樣的語法。 在 XML 中，屬性的值是實際的字串，唯一可能的變化正在使用哪一種字串的編碼格式。 在 XAML 中，您可以指派其他物件項目是屬性的值。 這項功能會啟用屬性元素語法。 而不是指定為元素標記中之屬性的屬性，指定的屬性是使用 開啟項目在標記*elementTypeName*。*propertyName*表單內，指定屬性的值，然後關閉屬性項目。  
  
 具體來說，語法開頭是左角括號 (\<)，後面的類別或結構內包含屬性項目語法的型別名稱。 這後面緊接跟著單一點 （.），然後依名稱的屬性，然後由右角括弧 (>)。 如同屬性語法，該屬性必須存在於指定的型別宣告的公用成員。 要指派給屬性的值會包含在屬性項目。 一般而言，指定為一個或多個 object 元素的值，指定做為值的物件是此案例因為該屬性元素語法是位址。 最後，指定相同的對等的結尾標記*elementTypeName*。*propertyName*組合中必須提供，適當的巢狀結構和與其他項目標記的平衡。  
  
 例如，以下是屬性的項目語法<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 Property 項目內的值也指定為內部的文字，萬一其中所指定的屬性型別是基本值類型，例如<xref:System.String>，或列舉型別在指定的名稱。 這些兩種用法是有點不常見，因為每個案例也可以使用更簡單的屬性語法。 填入屬性項目使用字串的其中一個案例是針對不是 XAML 內容屬性，但是仍然用於 UI 文字表示法的屬性，才會出現在該 UI 文字所需的特定的泛空白字元項目，例如換行字元。 屬性語法無法保留換行符號，但屬性元素語法可以只要顯著泛空白字元的保留是作用中 (如需詳細資訊，請參閱 <<c0> [ 處理在 XAML 中的泛空白字元](../../xaml-services/whitespace-processing-in-xaml.md))。 另一個案例是讓[X:uid 指示詞](../../xaml-services/x-uid-directive.md)可以套用至 property 項目，並應該當地語系化 WPF 中的值輸出 BAML 或其他技術，因此將標記內的值。  
  
 WPF 的邏輯樹狀結構中未表示的屬性項目。 Property 項目是只設定屬性，一個特定語法，而且不具有執行個體或物件支援它的項目。 (如需邏輯樹狀結構概念的詳細資訊，請參閱[WPF 中的樹狀結構](trees-in-wpf.md)。)  
  
 對於受到屬性和屬性的項目語法的屬性，兩種語法通常會有相同的結果，即使微妙之處，例如泛空白字元處理可以語法之間稍有不同。  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>集合語法  
 XAML 規格要求 XAML 處理器實作識別其中的實值型別是集合的屬性。 在.NET 中的一般 XAML 處理器實作根據 managed 程式碼與 CLR，用來識別集合型別，透過下列其中一項：  
  
-   型別會實作<xref:System.Collections.IList>。  
  
-   型別會實作<xref:System.Collections.IDictionary>。  
  
-   型別衍生自<xref:System.Array>(如需 XAML 中陣列的詳細資訊，請參閱[X:array 標記延伸](../../xaml-services/x-array-markup-extension.md)。)  
  
 如果屬性的型別是集合，然後推斷的集合型別不必做為物件元素標記中指定。 相反地，要成為的項目集合中的項目會指定為一或多個屬性項目的子項目。 每個這類項目評估的物件，在載入期間，以及藉由呼叫加入至集合`Add`隱含集合的方法。 例如，<xref:System.Windows.Style.Triggers%2A>屬性<xref:System.Windows.Style>採用特製化的集合型別<xref:System.Windows.TriggerCollection>，它會實作<xref:System.Collections.IList>。 您不需要具現化<xref:System.Windows.TriggerCollection>在標記中的物件項目。 相反地，您指定一或多個<xref:System.Windows.Trigger>做為項目內的項目`Style.Triggers`property 項目，其中<xref:System.Windows.Trigger>（或衍生的類別） 為的型別做為項目類型的強型別和隱含<xref:System.Windows.TriggerCollection>。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 屬性可能是集合型別和該類型的 XAML 內容屬性，衍生型別，本主題的下一節已討論過。  
  
 隱含的集合項目邏輯樹狀結構表示法中建立的成員，即使它不會出現在為元素標記。 父類型的建構函式通常是其屬性，其中的集合執行具現化，一開始是空的集合會成為物件樹狀結構的一部分。  
  
> [!NOTE]
>  List 與 dictionary 的泛型介面 (<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>) 的集合偵測不支援。 不過，您可以使用<xref:System.Collections.Generic.List%601>類別做為基底類別，因為它會實作<xref:System.Collections.IList>直接，或是<xref:System.Collections.Generic.Dictionary%602>做為基底類別，因為它會實作<xref:System.Collections.IDictionary>直接。  
  
 在集合型別的.NET 參考頁面中，此語法，刻意省略的集合物件項目與偶爾中註明 XAML 語法 」 一節做為隱含的集合語法。  
  
 除了根項目，做為另一個項目的子項目巢狀的 XAML 檔案中的每個物件項目其實是一或兩個下列案例中的項目： 其父項目的隱含集合屬性的成員或指定的父項目 (可透過 XAML 內容屬性將在後續章節中討論) 的 XAML 內容屬性值的項目。 換句話說，其實根目錄中，單一物件的父項目和子項目，在 [標記] 頁面中的關聯性。 和根目錄下的每個物件項目會提供其父代的屬性值的單一執行個體，或是其中一個資料行中的項目lection，同時也是父系的集合型別屬性值。 這個單一根目錄概念中常見的 XML，並經常會進行的 Api，例如載入 XAML 的行為<xref:System.Windows.Markup.XamlReader.Load%2A>。  
  
 下列範例是使用集合的物件項目語法 (<xref:System.Windows.Media.GradientStopCollection>) 明確地指定。  
  
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
  
 請注意，它不一定能夠明確宣告集合。 比方說，嘗試宣告<xref:System.Windows.TriggerCollection>明確地在先前所示<xref:System.Windows.Style.Triggers%2A>範例將會失敗。 明確宣告集合需要集合類別必須支援的預設建構函式，和<xref:System.Windows.TriggerCollection>沒有預設建構函式。  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML 內容屬性  
 XAML 內容的語法是在指定的類別才會啟用語法<xref:System.Windows.Markup.ContentPropertyAttribute>其類別宣告的一部分。 <xref:System.Windows.Markup.ContentPropertyAttribute>參考該類型的項目 （包括衍生的類別） 的內容屬性的屬性名稱。 由 XAML 處理器處理時，任何子項目或找到的開頭和結尾標記的物件項目之間的內部文字會指派給該物件的 XAML 內容屬性的值。 您可以指定明確的屬性項目之內容的屬性，但這種用法通常不會顯示在 XAML 語法 」 一節中的.NET 參考。 明確/詳細的資訊技術有偶爾標記為了清楚起見，或視為標記樣式的值，但通常 content 屬性的目的是要簡化標記，以便為父子式直覺的方式相關的項目可以直接巢狀。 未指派項目上的其他屬性的屬性項目標記為 「 內容 」，每個嚴格的 XAML 語言定義;他們先前處理中 XAML 剖析器的處理順序，不被視為 「 內容 」。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>必須是連續的 XAML 內容屬性值  
 XAML 內容屬性的值必須完全之前或任何其他的屬性項目之後指定該物件元素上。 是否將 XAML 內容屬性的值指定為字串，或做為一或多個物件，也是如此。 例如，下列標記不會剖析：  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 基本上，這是不合法因為如果此語法明確使用之內容屬性的屬性元素語法，然後內容屬性會設定兩次：  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 如果內容屬性是集合，而且項目子系會穿插屬性項目，就會是類似的不合法的範例：  
  
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
 多個單一物件項目，做為內容，以接受內容屬性的型別必須特別會是集合型別。 類似於屬性集合類型的項目語法，XAML 處理器必須識別集合型別的型別。 如果項目都具有 XAML 內容屬性，而 XAML 內容屬性的型別是集合，然後隱含的集合型別不需要指定做為物件元素標記中並不需要指定為屬性 el XAML 內容屬性ement。 因此顯而易見的內容模型，在標記中現在可以有一個以上的子元素，指派為內容。 以下是內容語法<xref:System.Windows.Controls.Panel>衍生的類別。 所有<xref:System.Windows.Controls.Panel>衍生的類別建立 XAML 內容屬性，才能<xref:System.Windows.Controls.Panel.Children%2A>，其需要的值為類型<xref:System.Windows.Controls.UIElementCollection>。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 請注意，沒有的屬性項目<xref:System.Windows.Controls.Panel.Children%2A>的項目也不<xref:System.Windows.Controls.UIElementCollection>需要在標記中。 這是 XAML 設計功能，以便以遞迴方式包含定義的項目[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]會更直覺的方式表示為具有直屬父系-子系項目關聯性，而不需要介入的屬性項目標記的巢狀項目樹狀結構或集合物件。 事實上，<xref:System.Windows.Controls.UIElementCollection>不能指定明確標記為物件項目，所設計。 因為其唯一用途是隱含的集合，即<xref:System.Windows.Controls.UIElementCollection>不會公開公用預設建構函式，因此無法具現化為物件項目。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>混合內容項目和具有內容屬性之物件的物件項目  
 XAML 規格宣告 XAML 處理器可以強制執行的用來填滿 XAML 內容屬性的物件項目內的物件項目必須是連續的，和不能混合。 針對混合屬性項目和內容的這項限制會強制執行[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 處理器。  
  
 您可以有子物件項目做為物件項目中第一個立即的標記。 然後您可以採用屬性元素。 或者，您可以指定一或多個屬性項目的內容，然後更多的屬性項目。 但是，一旦屬性項目後面的內容，您不能引入任何進一步的內容，您只能新增屬性項目。  
  
 此內容 / 屬性項目順序需求不適用於做為內容的內部文字。 不過，它仍然是因為顯著泛空白字元會難以在標記中以視覺化方式偵測，如果屬性項目會穿插內部文字保留內部文字是連續的很好的標記樣式。  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML 命名空間  
 沒有任何上述語法範例會指定預設 XAML 命名空間以外的 XAML 命名空間。 在典型[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，預設 XAML 命名空間指定為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]命名空間。 您可以指定非預設 XAML 命名空間的 XAML 命名空間，並仍使用類似的語法。 但是，然後，任何一處類別名為無法存取預設 XAML 命名空間內的類別名稱前面必須加的 XAML 命名空間前置詞對應至對應的 CLR 命名空間。 例如，`<custom:Example/>`具現化的執行個體的物件元素語法`Example`類別，其中包含該類別 （和可能的外部組件資訊，其中包含支援型別） 的 CLR 命名空間先前已對應至`custom`前置詞。  
  
 如需有關 XAML 命名空間的詳細資訊，請參閱 < [XAML 命名空間和命名空間對應 WPF XAML](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>標記延伸  
 XAML 定義的程式設計實體，可讓一般的 XAML 處理器處理的字串屬性值或物件項目，從逸出，並會延後至支援類別處理的標記延伸模組。 識別 XAML 處理器的標記延伸模組時使用屬性語法是左大括號 （{}），後面接著右大括號 （}） 以外的任何字元的字元。 下列的左大括弧的第一個字串必須參考類別，提供特定的擴充功能的行為，參考可能會略過子字串"Extension"，如果子字串是真正的類別名稱的一部分。 因此，可能會出現一個空格，，然後每個後續字元做為輸入延伸模組實作中，直到遇到右大括號。  
  
 .NET XAML 實作會使用<xref:System.Windows.Markup.MarkupExtension>抽象類別，做為所有支援之標記延伸模組的基礎[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以及其他架構或技術。 標記延伸，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]特別實作通常要提供方法，以參考其他現有的物件，或是要延後將會在執行階段評估的物件參考。 例如，簡單的 WPF 資料繫結藉由指定達成`{Binding}`標記延伸來取代特定的屬性通常會接受的值。 許多 WPF 標記延伸模組啟用屬性語法，其中屬性語法所不可能的屬性。 比方說，<xref:System.Windows.Style>物件是相當複雜的型別，其中包含巢狀的一連串的物件和屬性。 在 WPF 中的樣式通常會定義為在資源<xref:System.Windows.ResourceDictionary>，然後透過其中一種要求資源的兩個 WPF 標記延伸參考。 標記延伸會延後評估的資源查閱的屬性值，並可讓您提供的值<xref:System.Windows.FrameworkElement.Style%2A>屬性，採用類型<xref:System.Windows.Style>，請在屬性語法，如下列範例所示：  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 在這裡，`StaticResource`識別<xref:System.Windows.StaticResourceExtension>提供標記延伸實作的類別。 下一個字串`MyStyle`做為輸入做為非預設值<xref:System.Windows.StaticResourceExtension>建構函式，因為從延伸模組的字串參數會要求宣告<xref:System.Windows.ResourceKey>。 `MyStyle` 預期要[X:key](../../xaml-services/x-key-directive.md)的值<xref:System.Windows.Style>定義為資源。 [StaticResource 標記延伸](staticresource-markup-extension.md)使用量要求資源用來提供<xref:System.Windows.Style>透過靜態資源查閱邏輯，在載入時的屬性值。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。 如需參考的標記延伸和其他 XAML 程式設計在一般的.NET XAML 實作中啟用的功能，請參閱[XAML 命名空間 （x:）語言功能](../../xaml-services/xaml-namespace-x-language-features.md)。 WPF 特定標記延伸模組，請參閱[WPF XAML 擴充功能](wpf-xaml-extensions.md)。  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>附加屬性  
 附加的屬性是一種程式設計概念，藉此屬性可擁有，並定義是以特定類型的 XAML 中導入而設定為屬性或屬性項目上的任何項目。 主要案例附加的屬性是針對已啟用標記結構要報告其資訊的父項目中的子元素，而不需要廣泛共用的物件模型，所有項目。 相反地，項目子系的報表資訊的父項目可以使用附加的屬性。 如需附加的屬性，以及如何建立您自己的目的附加屬性，請參閱 <<c0> [ 附加屬性概觀](attached-properties-overview.md)。  
  
 附加的屬性使用的語法上類似屬性元素語法，，，您也指定*typeName*。*propertyName*組合。 有兩個重大差異：  
  
-   您可以使用*typeName*。*propertyName*即使設定透過屬性語法的附加的屬性的組合。 附加的屬性是唯一的案例，其中限定屬性名稱是屬性語法的需求。  
  
-   您也可以使用附加屬性的屬性元素語法。 不過，一般的屬性項目語法，對於*typeName*您指定的物件項目，其中包含屬性項目。 如果您指附加屬性，則*typeName*是定義類別，該附加的屬性，而不包含的物件項目。  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>附加事件  
 附加的事件是在特定的類型，可以定義事件，但可能在任何物件項目上附加處理常式的 XAML 中引進的另一個程式設計概念。 在 WOF 實作中，可定義附加的事件的類型通常是靜態型別定義的服務，並有時候這些附加的事件公開公開服務的型別中路由的事件的別名。 附加事件處理常式會透過屬性語法來指定。 因為附加事件，透過屬性語法擴充附加事件，以允許*typeName*。*eventName*使用量，其中*typeName*是類別，提供`Add`並`Remove`附加的事件基礎結構的事件處理常式存取子和*eventName*是事件名稱。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML 根元素的結構  
 下表顯示典型 XAML 根項目細分，顯示的特定屬性的根項目：  
  
|||  
|-|-|  
|`<Page`|開啟物件元素的根項目|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|預設值 ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML 命名空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 語言 XAML 命名空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|標記連接到任何程式碼後置的部分類別宣告為部分類別定義|  
|`>`|根的物件項目的結尾。 因為項目包含子項目沒有尚未關閉物件|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>選擇性的而且非建議的 XAML 用法  
 下列各節說明 XAML 用法就技術上而言由 XAML 處理器支援，但會產生詳細資訊或其他美觀的問題可能會影響當您開發包含 XAML 來源應用程式時，剩餘人類看得懂的 XAML 檔案。  
  
### <a name="optional-property-element-usages"></a>選擇性的屬性項目使用方式  
 選擇性的屬性項目使用方式包括明確地寫出項目內容的屬性，XAML 處理器會將視為隱含。 例如，當您宣告的內容<xref:System.Windows.Controls.Menu>，您可以選擇明確宣告<xref:System.Windows.Controls.ItemsControl.Items%2A>的集合<xref:System.Windows.Controls.Menu>作為`<Menu.Items>`屬性項目標記，以及發生每個<xref:System.Windows.Controls.MenuItem>內`<Menu.Items>`，而不是比使用隱含的 XAML 處理器行為的所有子項目的<xref:System.Windows.Controls.Menu>必須是<xref:System.Windows.Controls.MenuItem>放在<xref:System.Windows.Controls.ItemsControl.Items%2A>集合。 有時候以視覺化方式在標記中所示，釐清物件結構的選擇性的使用方式可以幫助。 或者，有時明確的屬性項目使用方式可以避免技術上正常運作，但在視覺上令人困惑，例如屬性值內的巢狀的標記延伸的標記。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完整限定的 typeName.memberName 屬性  
 *TypeName*。*memberName*形成屬性實際上運作更普遍比只是路由的事件的案例。 但是在其他情況下，該表單是多餘，而且您應該避免，如果只基於的標記樣式和可讀性。 在下列範例中，每三個參考<xref:System.Windows.Controls.Control.Background%2A>屬性完全相等：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` 能夠運作是因為該屬性的限定的查閱<xref:System.Windows.Controls.Button>成功 (<xref:System.Windows.Controls.Control.Background%2A>繼承自控制項) 和<xref:System.Windows.Controls.Button>物件元素的類別或基底類別。 `Control.Background` 有效的原因<xref:System.Windows.Controls.Control>類別實際上會定義<xref:System.Windows.Controls.Control.Background%2A>並<xref:System.Windows.Controls.Control>是<xref:System.Windows.Controls.Button>基底類別。  
  
 不過，下列*typeName*。*memberName*表單範例無法運作，並因此顯示加上註解：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> 另一個衍生類別<xref:System.Windows.Controls.Control>，如果有指定的話`Label.Background`內<xref:System.Windows.Controls.Label>物件項目，會處理這種使用方式。 不過，因為<xref:System.Windows.Controls.Label>不是類別或基底類別<xref:System.Windows.Controls.Button>，然後處理為指定的 XAML 處理器行為`Label.Background`為附加屬性。 `Label.Background` 不是可用的附加的屬性，且這種用法就會失敗。  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName 屬性項目  
 如何以類似方式*typeName*。*memberName*形式的運作方式的屬性語法*基*。*memberName*語法適用於屬性元素語法。 比方說，適用於下列語法：  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 Property 項目，指定的`Control.Background`即使屬性項目所包含之`Button`。  
  
 但就像*typeName*。*memberName*的屬性，格式*基*。*memberName*是不佳的樣式，在標記中，而且您應該避免它。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [XAML 命名空間 （x:）語言功能](../../xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML 延伸](wpf-xaml-extensions.md)
- [相依性屬性概觀](dependency-properties-overview.md)
- [TypeConverter 和 XAML](typeconverters-and-xaml.md)
- [WPF 的 XAML 和自訂類別](xaml-and-custom-classes-for-wpf.md)
