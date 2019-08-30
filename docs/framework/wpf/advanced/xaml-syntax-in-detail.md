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
ms.openlocfilehash: 09f0a1b34e88be995fb9a386161a930457e4bb56
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168995"
---
# <a name="xaml-syntax-in-detail"></a>XAML 語法詳細資料
本主題定義用來描述 XAML 語法元素的詞彙。 本檔的其餘部分會經常使用這些詞彙, 這兩者都是針對 WPF 檔, 特別是針對使用 XAML 的其他架構, 或是在 .xaml 層級由 XAML 語言支援啟用的基本 XAML 概念。 本主題將針對[XAML 總覽 (WPF)](xaml-overview-wpf.md)主題中引進的基本術語進行擴充。  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML 語言規格  
 在此定義的 XAML 語法詞彙也會在 XAML 語言規格中定義或參考。 XAML 是以 XML 為基礎的語言, 並在 XML 結構化規則之後遵循或擴充。 有些術語是從共用, 或是以描述 XML 語言或 XML 檔物件模型時常用的術語為基礎。  
  
 如需 XAML 語言規格的詳細資訊, 請從 Microsoft 下載中心下載[ \[MS-XAML\] ](https://go.microsoft.com/fwlink/?LinkId=114525) 。  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML 和 CLR  
 XAML 是一種標記語言。 Common language runtime (CLR) (如其名稱所隱含) 可啟用執行時間執行。 XAML 本身不是 CLR 執行時間直接取用的其中一個通用語言。 取而代之的是, 您可以將 XAML 視為支援它自己的型別系統。 WPF 使用的特定 XAML 剖析系統建基於 CLR 和 CLR 型別系統。 XAML 類型會對應至 CLR 類型, 以在剖析 WPF 的 XAML 時具現化運行時程表示。 基於這個理由, 本檔中語法討論的其餘部分將包含 CLR 型別系統的參考, 即使 XAML 語言規格中的對等語法討論不是如此。 (根據 XAML 語言規格層級, XAML 類型可以對應到任何其他類型系統, 這不一定是 CLR, 但這需要建立和使用不同的 XAML 剖析器)。  
  
#### <a name="members-of-types-and-class-inheritance"></a>類型和類別繼承的成員  
 當做[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類型的 XAML 成員出現的屬性和事件, 通常會繼承自基底類型。 例如, 請考慮下列範例: `<Button Background="Blue" .../>`。 如果您要查看類別定義、反映結果或<xref:System.Windows.Controls.Button>檔,屬性在類別上不是立即宣告的屬性。<xref:System.Windows.Controls.Control.Background%2A> 相反地<xref:System.Windows.Controls.Control.Background%2A> , 是繼承自基類<xref:System.Windows.Controls.Control> 。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 元素的類別繼承行為, 是從 XML 標記的架構強制式轉譯中大幅出發。 類別繼承可能會變得複雜, 特別是當中繼基類是抽象的, 或涉及介面時。 這是一項原因, 那就是 XAML 元素的集合及其允許的屬性, 很難正確地表示, 而且使用一般用於程式[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]設計的架構類型, 例如 DTD 或 XSD 格式。 另一個原因是 XAML 語言本身的擴充性和類型對應功能, 會排除所允許之類型和成員的任何固定標記法的完整性。  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>物件元素語法  
 *物件元素語法*是 XAML 標記語法, 會藉由宣告 XML 專案來具現化 CLR 類別或結構。 此語法類似其他標記語言 (例如 HTML) 的元素語法。 物件元素語法以左角括弧 (\<) 開頭, 後面緊接著要具現化之類別或結構的類型名稱。 零或多個空格可以遵循類型名稱, 而且也可以在 object 元素上宣告零個或多個屬性, 並以一或多個空格分隔每個屬性名稱 = "value" 配對。 最後, 必須符合下列其中一項條件:  
  
- 元素和標記必須以正斜線 (/) 關閉, 後面緊接著右角括弧 (>)。  
  
- 開頭標記必須以右角括弧 (>) 完成。 其他物件元素、屬性專案或內部文字則可以跟隨在開頭標記之後。 此處所包含的內容, 通常會受到元素的物件模型所限制。 物件元素的對等結束記號也必須存在, 以適當的對應, 並與其他開頭和結束記號配對進行平衡。  
  
 .NET 所實作為的 XAML 具有一組規則, 可將物件元素對應至類型、屬性為屬性或事件, 以及 XAML 命名空間與 CLR 命名空間加上元件。 針對 WPF 和 .NET, XAML 物件專案會對應至所參考元件中所定義的 .NET 類型, 而屬性會對應至這些類型的成員。 當您在 XAML 中參考 CLR 型別時, 您也可以存取該型別的繼承成員。  
  
 例如, 下列範例是物件專案語法, 可具現化<xref:System.Windows.Controls.Button>類別的新實例, 也會<xref:System.Windows.FrameworkElement.Name%2A>指定屬性和該屬性的值:  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 下列範例是物件元素語法, 其中也包含 XAML 內容屬性語法。 包含在內的內部文字將用來設定<xref:System.Windows.Controls.TextBox> XAML 內容<xref:System.Windows.Controls.TextBox.Text%2A>屬性。  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>內容模型  
 在語法方面, 類別可能支援使用當做 XAML 物件專案, 但當應用程式或頁面放在整體內容模型或專案樹狀結構的預期位置時, 該專案將只能在該元素中正常運作。 例如, <xref:System.Windows.Controls.MenuItem>通常應該只放在<xref:System.Windows.Controls.Primitives.MenuBase>衍生類別的子系, 例如<xref:System.Windows.Controls.Menu>。 特定專案的內容模型會記載為控制項的類別頁面上的備註一部分, 以及可當做[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 專案使用的其他類別。  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>物件元素的屬性  
 XAML 中的屬性是由各種可能的語法所設定。 根據您所設定之屬性的基礎類型系統特性而定, 特定屬性可以使用哪種語法會有所不同。  
  
 藉由設定屬性的值, 您可以將功能或特性加入至物件, 因為它們存在於執行時間物件圖形中。 從物件元素建立之物件的初始狀態是以無參數的函式行為為基礎。 一般來說, 您的應用程式會使用任何指定物件的完全預設實例以外的專案。  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>屬性 (Attribute) 語法 (屬性(Property))  
 屬性語法是 XAML 標記語法, 會藉由宣告現有物件專案上的屬性來設定屬性的值。 屬性名稱必須符合可支援相關物件專案之類別的屬性 (property) 的 CLR 成員名稱。 屬性名稱後面接著指派運算子 (=)。 屬性值必須是括在引號內的字串。  
  
> [!NOTE]
> 您可以使用替代引號將常值引號放在屬性中。 例如, 您可以使用單引號來宣告字串, 其中包含其中的雙引號字元。 無論您使用單引號或雙引號, 都應該使用相符的配對來開啟和關閉屬性值字串。 還有其他可用來處理任何特定 XAML 語法所加上之字元限制的逸出序列或其他技術。 請參閱[XML 字元實體和 XAML](../../xaml-services/xml-character-entities-and-xaml.md)。  
  
 若要透過屬性語法設定, 屬性必須是公用的, 而且必須是可寫入的。 支援型別系統中的屬性值必須是實值型別, 或必須是參考型別, 而且在存取相關的支援型別時, XAML 處理器可以加以具現化或參照。  
  
 針對 WPF XAML 事件, 當做屬性名稱參考的事件必須是公用的, 而且具有公用委派。  
  
 屬性或事件必須是包含物件元素所具現化之類別或結構的成員。  
  
### <a name="processing-of-attribute-values"></a>屬性值的處理  
 開頭和結尾引號中包含的字串值是由 XAML 處理器處理。 對於屬性, 預設的處理行為取決於基礎 CLR 屬性的類型。  
  
 屬性值是以下列其中一種方式填入, 使用此處理順序:  
  
1. 如果 XAML 處理器遇到大括弧, 或衍生自<xref:System.Windows.Markup.MarkupExtension>的物件專案, 則會先評估參考的標記延伸, 而不是將值當做字串來處理, 而且標記延伸所傳回的物件會當做value. 在許多情況下, 標記延伸所傳回的物件將會是現有物件的參考, 或是延遲評估到執行時間的運算式, 而且不是新具現化的物件。  
  
2. 如果屬性是以屬性化<xref:System.ComponentModel.TypeConverter>的方式宣告, 或該屬性的實值型別是以屬性化<xref:System.ComponentModel.TypeConverter>, 則會將屬性的字串值提交至型別轉換器做為轉換輸入, 而轉換器會傳回新的物件實例。  
  
3. 如果沒有<xref:System.ComponentModel.TypeConverter>, 則會嘗試直接轉換為屬性類型。 這個最終層級是 XAML 語言基本型別之間的剖析器原生值直接轉換, 或在列舉中檢查已命名常數的名稱 (剖析器接著會存取相符的值)。  
  
#### <a name="enumeration-attribute-values"></a>列舉屬性值  
 Xaml 中的列舉是由 XAML 剖析器在本質上進行處理, 而且您應該指定其中一個列舉的已命名常數的字串名稱, 來指定列舉的成員。  
  
 針對 nonflag 列舉值, 原生行為是處理屬性值的字串, 並將其解析為其中一個列舉值。 您未在格式*列舉*中指定列舉。*值*, 如同您在程式碼中所做的一樣。 相反地, 您只指定*值*, 而*列舉*是由您所設定之屬性的型別推斷。 如果您在*列舉*中指定屬性, 則為。*值*形式, 將無法正確解析。  
  
 針對旗標型列舉, 行為是以<xref:System.Enum.Parse%2A?displayProperty=nameWithType>方法為基礎。 您可以使用逗號分隔每個值, 以指定旗標型列舉的多個值。 不過, 您無法結合未旗標型的列舉值。 例如, 您不能使用逗號語法來嘗試建立, 其<xref:System.Windows.Trigger>作用於 nonflag 列舉的多個條件:  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 在 WPF 中, 支援可在 XAML 中設定之屬性的旗標型列舉很罕見。 不過, 其中一個列舉是<xref:System.Windows.Media.StyleSimulations>。 例如, 您可以使用逗點分隔的旗標型屬性語法來修改<xref:System.Windows.Documents.Glyphs>類別備註中提供的範例;可能會`StyleSimulations = "BoldSimulation,ItalicSimulation"`變成。 `StyleSimulations = "BoldSimulation"` <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>是另一個可指定多個列舉值的屬性。 不過, 這個屬性剛好是特殊案例, 因為<xref:System.Windows.Input.ModifierKeys>列舉支援它自己的型別轉換器。 修飾詞的類型轉換子會使用加號 (+) 做為分隔符號, 而不是逗號 (,)。 這項轉換支援更傳統的語法來表示 Microsoft Windows 程式設計中的主要組合, 例如 "Ctrl + Alt"。  
  
### <a name="properties-and-event-member-name-references"></a>屬性和事件成員名稱參考  
 當指定屬性時, 您可以參考任何屬性或事件, 該專案會以您為包含物件專案所具現化之 CLR 類型的成員形式存在。  
  
 或者, 您可以參考附加屬性或附加事件, 而不受包含物件元素的影響。 (後續章節將討論附加的屬性)。  
  
 您也可以使用*typeName*, 從任何可透過預設命名空間存取的物件來命名任何事件。*事件*的部分限定名稱;此語法支援附加路由事件的處理常式, 其中處理常式是用來處理從子專案路由的事件, 但父項目在其 members 資料表中也不會有該事件。 此語法類似附加事件語法, 但此處的事件不是真正的附加事件。 相反地, 您會參考具有限定名稱的事件。 如需詳細資訊, 請參閱[路由事件總覽](routed-events-overview.md)。  
  
 在某些情況下, 有時會提供屬性名稱做為屬性的值, 而不是屬性名稱。 該屬性名稱也可以包含限定詞, 例如以 [類型名稱] 格式指定的屬性。*dependencyPropertyName*。 這種情況在 XAML 中撰寫樣式或範本時很常見。 當做屬性值提供之屬性名稱的處理規則會不同, 而且是由所設定的屬性類型或特定 WPF 子系統的行為所控制。 如需詳細資訊, 請參閱設定[樣式和範本](../controls/styling-and-templating.md)。  
  
 屬性名稱的另一個用法是當屬性值描述屬性屬性關聯性時。 這項功能是用於資料系結和分鏡腳本目標, 而且是由<xref:System.Windows.PropertyPath>類別和其類型轉換器所啟用。 如需查閱語義的更完整描述, 請參閱[PROPERTYPATH XAML 語法](propertypath-xaml-syntax.md)。  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>屬性元素語法  
 *屬性專案語法*是分歧的語法, 與元素的基本 XML 語法規則有點類似。 在 XML 中, 屬性的值是一種實際的字串, 唯一可能的變化是使用的字串編碼格式。 在 XAML 中, 您可以將其他物件元素指派為屬性的值。 此功能是由屬性元素語法所啟用。 屬性會使用*elementTypeName*中的開頭專案標記來指定, 而不是指定為元素標記中的屬性。*propertyName*形式, 屬性的值會在內指定, 然後屬性專案就會關閉。  
  
 具體而言, 語法是以左角括弧 (\<) 開頭, 後面緊接著屬性元素語法所包含之類別或結構的類型名稱。 後面緊接著單一點 (.), 然後依屬性的名稱, 再接著右角括弧 (>)。 如同屬性語法, 該屬性必須存在於所指定類型的宣告公用成員中。 要指派給屬性的值會包含在 property 元素中。 一般來說, 此值會指定為一或多個物件專案, 因為將物件指定為值, 就是屬性專案語法的目的是要處理的案例。 最後, 指定相同*elementTypeName*的對等結束標記。必須提供*propertyName*組合, 以適當的方式與其他專案標記進行嵌套和平衡。  
  
 例如, 下列是的<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性<xref:System.Windows.Controls.Button>的屬性專案語法。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 如果指定的屬性類型是基本實數值型別 (例如<xref:System.String>) 或列舉 (其中已指定名稱), 則屬性專案中的值也可以指定為內部文字。 這兩種用法並不常見, 因為每個案例也都可以使用較簡單的屬性語法。 以字串填滿屬性專案的其中一個案例是針對不是 XAML 內容屬性, 但仍用於表示 UI 文字的屬性, 而特定的空白字元 (例如, 分行符號) 必須出現在該 UI 文字中。 屬性語法無法保留分行符號, 但屬性專案語法可以, 只要有效的空白字元保留作用 (如需詳細資料, 請參閱[XAML 中的空白字元處理](../../xaml-services/whitespace-processing-in-xaml.md))。 另一個情況是, 可以將[x:Uid](../../xaml-services/x-uid-directive.md)指示詞套用至 property 專案, 因此會將中的值標示為應該在 WPF 輸出 BAML 或其他技術中當地語系化的值。  
  
 屬性元素不會在 WPF 邏輯樹狀結構中表示。 Property 元素只是用來設定屬性的特定語法, 而且不是具有實例或物件支援的元素。 (如需邏輯樹狀概念的詳細資訊, 請參閱[WPF 中](trees-in-wpf.md)的樹狀結構)。  
  
 對於支援屬性和屬性專案語法的屬性而言, 這兩個語法通常會有相同的結果, 但微妙差異 (例如空白字元處理) 可能會在語法上稍有不同。  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>集合語法  
 XAML 規格需要 XAML 處理器執行, 以識別實值型別為集合的屬性。 .NET 中的一般 XAML 處理器執行是以 managed 程式碼和 CLR 為基礎, 而且它會透過下列其中一項來識別集合類型:  
  
- 類型 implements <xref:System.Collections.IList>。  
  
- 類型 implements <xref:System.Collections.IDictionary>。  
  
- 類型衍生自<xref:System.Array> (如需 XAML 中陣列的詳細資訊, 請參閱[x:Array 標記延伸](../../xaml-services/x-array-markup-extension.md))。  
  
 如果屬性的類型是集合, 則不需要在標記中將推斷的集合類型指定為 object 元素。 相反地, 要做為集合中專案的元素會指定為 property 元素的一或多個子項目。 每個這類專案會在載入時評估為物件, 並藉由呼叫`Add`隱含集合的方法來新增至集合。 例如, <xref:System.Windows.Style.Triggers%2A>的<xref:System.Windows.Style>屬性會採用特殊化的<xref:System.Collections.IList>集合型<xref:System.Windows.TriggerCollection>別, 它會執行。 不需要在標記中具現<xref:System.Windows.TriggerCollection>化物件元素。 相反地, 您會將一個<xref:System.Windows.Trigger>或多個專案指定`Style.Triggers`為 property 元素中<xref:System.Windows.Trigger>的元素, 其中 (或衍生類別) 是預期為強型別和隱含<xref:System.Windows.TriggerCollection>之專案類型的類型。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 屬性可以是集合類型, 以及該類型和衍生類型的 XAML 內容屬性, 這會在本主題的下一節中討論。  
  
 隱含的集合元素會在邏輯樹狀結構標記法中建立成員, 即使它不會以專案形式出現在標記中。 通常, 父類型的函式會針對屬於其屬性之一的集合執行具現化, 而初始空集合會成為物件樹狀結構的一部分。  
  
> [!NOTE]
> 不支援泛型清單和字典介面<xref:System.Collections.Generic.IList%601> ( <xref:System.Collections.Generic.IDictionary%602>和) 進行集合偵測。 不過, <xref:System.Collections.Generic.List%601>您可以使用類別作為基類, 因為<xref:System.Collections.IList>它會直接執行, 或<xref:System.Collections.Generic.Dictionary%602>當做基類, 因為它會<xref:System.Collections.IDictionary>直接實作為。  
  
 在集合類型的 .NET 參考頁面中, XAML 語法區段偶爾會以隱含的集合語法的形式, 將此語法視為集合的 object 元素。  
  
 除了根項目之外, XAML 檔案中作為另一個專案之子專案的每個物件專案, 實際上都是一個專案, 也就是其父元素的隱含集合屬性的成員。, 或指定父元素之 XAML 上下文屬性值的元素 (即將在後續章節中討論 XAML 內容屬性)。 換句話說, 在標記頁面中, 父元素和子專案的關聯性實際上是根目錄中的單一物件, 而根目錄底下的每個物件專案都是單一實例, 可提供父系的屬性值或一欄內的其中一個元素。observabledependencyobjectcollection 也是父系的集合型別屬性值。 這個單一根目錄概念在 XML 中很常見, 而且通常會在載入 XAML (例如) <xref:System.Windows.Markup.XamlReader.Load%2A>的 api 行為中加強。  
  
 下列範例是明確指定集合 (<xref:System.Windows.Media.GradientStopCollection>) 之 object 元素的語法。  
  
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
  
 請注意, 不一定可以明確宣告集合。 例如, 嘗試<xref:System.Windows.TriggerCollection>在先前顯示<xref:System.Windows.Style.Triggers%2A>的範例中明確宣告會失敗。 明確宣告集合需要集合類別必須支援無參數的函式, 而且<xref:System.Windows.TriggerCollection>沒有無參數的函式。  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML 內容屬性  
 XAML 內容語法是一種語法, 只有在將<xref:System.Windows.Markup.ContentPropertyAttribute>指定為其類別宣告一部分的類別上才會啟用。 會<xref:System.Windows.Markup.ContentPropertyAttribute>參考屬於該元素類型 (包括衍生類別) 之內容屬性的屬性名稱。 由 XAML 處理器處理時, 在物件專案的開頭和結束記號之間找到的任何子專案或內部文字, 都會指派為該物件的 XAML 內容屬性值。 您可以指定 content 屬性的明確屬性專案, 但這種用法通常不會顯示在 .NET 參考的 XAML 語法區段中。 明確/詳細的技巧偶爾會出現標記清晰度或標記樣式的值, 但是內容屬性的目的通常是為了簡化標記, 讓直覺相關的專案可以直接嵌套。 專案上其他屬性的屬性專案標記不會根據嚴格的 XAML 語言定義指派為「內容」;這些是先前在 XAML 剖析器的處理順序中處理, 而且不會被視為「內容」。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML 內容屬性值必須是連續的  
 XAML 內容屬性的值必須在該物件元素上的任何其他屬性專案之前或之後完整指定。 不論 XAML 內容屬性的值是指定為字串, 還是一或多個物件, 都是如此。 例如, 下列標記不會剖析:  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 基本上, 這是不合法的, 因為如果使用 content 屬性的屬性專案語法來明確設定此語法, 則會將 content 屬性設為兩次:  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 同樣不合法的範例是, 如果 content 屬性是一個集合, 而子項目與屬性專案交錯:  
  
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
 為了接受一個以上的物件元素做為內容, content 屬性的類型必須特別是集合類型。 類似于集合類型的屬性元素語法, XAML 處理器必須識別屬於集合類型的類型。 如果專案具有 XAML 內容屬性, 而且 XAML 內容屬性的類型是集合, 則隱含的集合類型不需要在標記中指定為物件元素, 而且 XAML 內容屬性不需要指定為 el 屬性。& e). 因此, 標記中的明顯內容模型現在可以將一個以上的子項目指派為內容。 下列為<xref:System.Windows.Controls.Panel>衍生類別的內容語法。 所有<xref:System.Windows.Controls.Panel>衍生類別都會將<xref:System.Windows.Controls.Panel.Children%2A>XAML 內容屬性建立為, 這需要類型<xref:System.Windows.Controls.UIElementCollection>的值。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 請注意, 標記中不需要<xref:System.Windows.Controls.Panel.Children%2A>的屬性專案和的<xref:System.Windows.Controls.UIElementCollection>元素。 這是 XAML 的設計功能, 因此, 定義的[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]以遞迴方式包含的元素會以具有直接父子式專案關聯性的嵌套元素樹狀結構來表示, 而不會有中間的屬性專案標記或集合物件。 事實上, <xref:System.Windows.Controls.UIElementCollection>根據設計, 無法在標記中明確地指定為物件元素。 因為其僅適用于隱含集合, <xref:System.Windows.Controls.UIElementCollection>所以不會公開公用無參數的函式, 因此無法將它具現化為物件元素。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>使用 Content 屬性來混合物件中的屬性元素和物件元素  
 XAML 規格宣告 XAML 處理器可以強制執行用來填入物件專案內 XAML 內容屬性的物件專案, 必須是連續的, 而且不能是混合的。 對混合屬性專案和內容的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]這項限制會由 XAML 處理器強制執行。  
  
 您可以將子物件元素做為物件元素中的第一個立即標記。 然後您可以引進屬性元素。 或者, 您可以指定一或多個屬性專案、[內容]、[其他] 屬性專案。 但是一旦屬性專案遵循內容, 您就無法再引進任何進一步的內容, 您只能加入屬性專案。  
  
 此內容/屬性專案順序需求不適用於作為內容的內部文字。 不過, 它仍然是讓內部文字保持連續的良好標記樣式, 因為如果屬性專案與內部文字交錯, 明顯的空白字元將難以在標記中以視覺方式偵測。  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML 命名空間  
 上述語法範例都不會指定預設 XAML 命名空間以外的 XAML 命名空間。 在一般[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中, 預設的 XAML 命名空間會指定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]為命名空間。 除了預設的 XAML 命名空間以外, 您還可以指定 XAML 命名空間, 而且仍然會使用類似的語法。 但是, 在預設的 XAML 命名空間中無法存取名為的類別的任何地方, 該類別名稱前面必須加上 XAML 命名空間的前置詞, 以便對應至對應的 CLR 命名空間。 例如, `<custom:Example/>`是物件專案語法, 用來具現化`Example`類別的實例, 其中包含該類別的 CLR 命名空間 (可能是包含支援類型的外部元件資訊) 先前已對應至`custom`前置詞。  
  
 如需 XAML 命名空間的詳細資訊, 請參閱[WPF xaml 的 Xaml 命名空間和命名空間對應](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>標記延伸  
 XAML 會定義標記延伸程式設計實體, 讓您可以從標準的 XAML 處理器處理字串屬性值或物件專案, 並將處理延遲到支援類別。 使用屬性語法時, 識別 XAML 處理器之標記延伸的字元是左大括弧 ({), 後面接著右大括弧 (}) 以外的任何字元。 左大括弧後面的第一個字串必須參考提供特定延伸模組行為的類別, 如果該子字串是真正類別名稱的一部分, 參考可能會省略子字串 "Extension"。 之後, 就會出現一個空格, 然後將每個後續字元當做延伸模組實作為輸入使用, 直到遇到右大括弧為止。  
  
 .Net XAML 執行會使用<xref:System.Windows.Markup.MarkupExtension>抽象類別做為所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援之標記延伸的基礎, 以及其他架構或技術。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]特別執行的標記延伸通常是用來提供參考其他現有物件的方法, 或對將在執行時間評估的物件進行延遲參考。 例如, 簡單的 WPF 資料系結是藉由指定`{Binding}`標記延伸來取代特定屬性通常會採用的值來完成。 許多 WPF 標記延伸都會啟用屬性的屬性語法, 在此情況下不可能發生屬性語法。 例如, <xref:System.Windows.Style>物件是相當複雜的類型, 其中包含一組嵌套的物件和屬性。 WPF 中的樣式通常會定義為中的資源<xref:System.Windows.ResourceDictionary>, 然後透過要求資源的兩個 WPF 標記延伸中的其中一個來參考。 標記延伸會將屬性值的評估延遲到資源查閱, 並在屬性語法中提供<xref:System.Windows.FrameworkElement.Style%2A>屬性的值 (採用類型<xref:System.Windows.Style>), 如下列範例所示:  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 在此`StaticResource` , 會<xref:System.Windows.StaticResourceExtension>識別提供標記延伸實作為的類別。 下一個字串`MyStyle`會當做非預設<xref:System.Windows.StaticResourceExtension>的函式的輸入使用, 其中從延伸模組字串取得的參數會宣告所要求<xref:System.Windows.ResourceKey>的。 `MyStyle`應該是<xref:System.Windows.Style>定義為資源之的[x:Key](../../xaml-services/x-key-directive.md)值。 [StaticResource 標記延伸](staticresource-markup-extension.md)使用方式會要求資源用來在載入時透過<xref:System.Windows.Style>靜態資源查閱邏輯提供屬性值。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。 如需在一般 .net XAML 執行中啟用的標記延伸和其他 XAML 程式設計功能的參考[, 請參閱 XAML 命名空間 (x:)語言功能](../../xaml-services/xaml-namespace-x-language-features.md)。 如需 WPF 特定的標記延伸, 請參閱[WPF XAML 延伸](wpf-xaml-extensions.md)模組。  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>附加屬性  
 附加屬性是 XAML 中引進的程式設計概念, 其中的屬性可由特定類型所擁有和定義, 但設定為任何專案上的屬性或屬性專案。 附加屬性的主要案例是讓標記結構中的子專案向父項目報告資訊, 而不需要在所有專案上有廣泛的共用物件模型。 相反地, 父元素也可以使用附加屬性, 將資訊報告至子項目。 如需附加屬性的用途, 以及如何建立您自己的附加屬性的詳細資訊, 請參閱[附加屬性總覽](attached-properties-overview.md)。  
  
 附加屬性會使用表面上類似屬性專案語法的語法, 您也可以指定*typeName*。*propertyName*組合。 有兩個重大差異：  
  
- 您可以使用*typeName*。*propertyName*組合, 即使是透過屬性語法設定附加屬性時也一樣。 附加屬性是限定屬性名稱是屬性語法需求的唯一案例。  
  
- 您也可以使用附加屬性的屬性專案語法。 不過, 針對一般屬性專案語法, 您指定的*typeName*是包含 property 專案的 object 元素。 如果您要參考附加屬性, 則*typeName*是定義附加屬性的類別, 而不是包含的 object 元素。  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>附加事件  
 附加事件是 XAML 中引進的另一種程式設計概念, 其中事件可以由特定類型定義, 但處理常式可以附加至任何物件元素。 在 WOF 的執行中, 定義附加事件的類型通常是定義服務的靜態類型, 有時這些附加事件是由公開服務之類型中的路由事件別名所公開。 附加事件的處理常式是透過屬性語法來指定。 如同附加事件, 已針對附加事件展開屬性語法以允許*typeName*。事件名稱的用法, 其中*typeName*是提供`Add`和 `Remove`附加事件基礎結構之事件處理常式存取子的類別, 而引發者則是事件名稱。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML 根項目的剖析  
 下表顯示一般 XAML 根項目的細分, 其中顯示根項目的特定屬性:  
  
|||  
|-|-|  
|`<Page`|開啟根項目的 object 元素|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|預設 ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML 命名空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 語言 XAML 命名空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|將標記連接至為部分類別定義之任何程式碼後置的部分類別宣告|  
|`>`|根之物件元素的結尾。 物件尚未關閉, 因為元素包含子項目|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>選擇性和非建議 XAML 用法  
 下列各節描述 XAML 處理器在技術上支援的 XAML 用法, 但會產生詳細資訊或其他美觀問題, 當您開發包含 XAML 來源的應用程式時, 會干擾 XAML 檔案的其餘部分。  
  
### <a name="optional-property-element-usages"></a>選擇性的屬性元素使用方式  
 選擇性的屬性專案用法包括明確地寫出 XAML 處理器視為隱含的元素內容屬性。 例如, 當您宣告的內容<xref:System.Windows.Controls.Menu>時, 您可以選擇將的<xref:System.Windows.Controls.ItemsControl.Items%2A> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.Menu> `<Menu.Items>`集合明確宣告為屬性專案標記, 並將其放在內`<Menu.Items>`, 而非除了使用隱含 XAML 處理器行為, 所有的子<xref:System.Windows.Controls.Menu>專案都必須<xref:System.Windows.Controls.MenuItem>是<xref:System.Windows.Controls.ItemsControl.Items%2A> , 而且會放在集合中。 有時候選擇性的用法有助於以視覺化方式澄清標記中所表示的物件結構。 或有時明確的屬性專案使用方式可以避免在技術上功能上的標記, 但在視覺上令人困惑, 例如屬性值內的嵌套標記延伸。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完整 typeName。成員資格限定屬性  
 *TypeName*。屬性的*成員名稱*格式實際上比路由事件案例的運作方式更為普遍。 但在其他情況下, 表單是多餘的, 而且您應該避免這種情況, 因為這是因為標記樣式和可讀性的原因。 在下列範例中, <xref:System.Windows.Controls.Control.Background%2A>屬性的三個參考完全相同:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`適用的原因是, 上<xref:System.Windows.Controls.Button>該屬性的限定查閱成功 (<xref:System.Windows.Controls.Control.Background%2A>繼承自 Control), <xref:System.Windows.Controls.Button>而且是物件元素或基類的類別。 `Control.Background`適用于, <xref:System.Windows.Controls.Control>因為類別實際上<xref:System.Windows.Controls.Control.Background%2A>會<xref:System.Windows.Controls.Control>定義, <xref:System.Windows.Controls.Button>而是基類。  
  
 不過, 下列*類型名稱*為。*成員名稱*表單範例無法運作, 因此會顯示為批註:  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>是的<xref:System.Windows.Controls.Control>另一個衍生類別, 而且如果您已`Label.Background`在<xref:System.Windows.Controls.Label>物件專案中指定, 則此使用方式會運作。 不過, 因為<xref:System.Windows.Controls.Label>不是的類別或基類<xref:System.Windows.Controls.Button>, 所以指定的 XAML 處理器行為會接著當做附加屬性`Label.Background`來處理。 `Label.Background`不是可用的附加屬性, 而且此使用方式失敗。  
  
### <a name="basetypenamemembername-property-elements"></a>基. 成員名稱屬性元素  
 以類似的方式來使用*typeName*。*成員名稱*形式適用于屬性語法, 也就是*基*。*成員名稱*語法適用于屬性元素語法。 例如, 下列語法可運作:  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 在這裡, `Control.Background`即使屬性專案是包含在中`Button`, 還是會提供屬性專案。  
  
 但是就像*typeName*一樣。屬性的*成員名稱*形式,*基*。*成員名稱*在標記中的樣式不佳, 您應該避免這個情況。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [XAML 命名空間 (x:)語言功能](../../xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML 延伸](wpf-xaml-extensions.md)
- [相依性屬性概觀](dependency-properties-overview.md)
- [TypeConverter 和 XAML](typeconverters-and-xaml.md)
- [WPF 的 XAML 和自訂類別](xaml-and-custom-classes-for-wpf.md)
