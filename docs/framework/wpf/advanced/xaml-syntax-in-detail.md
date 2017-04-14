---
title: "XAML 語法詳細資料 | Microsoft Docs"
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
  - "XML 命名空間"
  - "XAML 屬性剖析"
  - "屬性剖析"
  - "XAML 標記延伸"
  - "附加屬性"
  - "標記語法 [XAML]"
  - "標記延伸"
  - "XAML 物件項目語法"
  - "XAML 語法術語"
  - "附加事件"
  - "查閱語意"
  - "XAML 中，附加事件"
  - "XAML 內容的語法"
  - "XAML 中，查閱語意"
  - "內容語法"
  - "物件項目語法"
  - "語法術語 [XAML]"
  - "XAML 中，附加屬性"
  - "剖析屬性 [XAML]，"
  - "XAML 標記語法"
  - "XAML 屬性語法"
  - "屬性項目語法"
  - "用語 [XAML]"
  - "XML 命名空間"
  - "屬性語法 [XAML]"
  - "XAML 屬性項目語法"
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# XAML 語法詳細資料
本主題中定義的詞彙用於描述 XAML 語法的項目。 這些詞彙經常用於此文件適用於 WPF 文件的其餘具體來說，使用 XAML 或啟用 System.Xaml 層級的 XAML 語言支援的基本 XAML 概念的架構。 本主題會展開，主題中介紹的基本術語[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)。  
  

  
<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML 語言規格  
 此處定義的 XAML 語法術語也定義或參考在 XAML 語言規格。 XAML 是以 XML 為基礎的語言與遵循或基礎 XML 結構的規則。 某些詞彙共用，或為基礎的術語，通常用於描述 XML 語言或 XML 文件物件模型。  
  
 如需有關 XAML 語言規格的詳細資訊，請下載[ \[MS XAML\] ](http://go.microsoft.com/fwlink/?LinkId=114525)從 Microsoft 下載中心 」。  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML 和 CLR  
 XAML 是一種標記語言。 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、 為隱含的名稱可讓執行階段執行。 XAML 不單獨一種常見直接由 CLR 執行階段的語言。 相反地，您可以將 XAML 視為支援它自己的型別系統。 特定 XAML 剖析系統使用的 WPF 為基礎的 CLR 和 CLR 型別系統。 XAML 型別會對應至 CLR 型別為 WPF 的 XAML 剖析時，具現化的執行的階段表示法。 基於這個理由，討論這份文件中語法的其餘部分會包含 CLR 型別系統中，參考，即使沒有對等的語法中的討論區 XAML 語言規格。 （每個 XAML 語言規格層級中，XAML 型別無法對應至任何其他型別系統，這不一定要 CLR，但這需要建立和使用不同的 XAML 剖析器。）  
  
#### <a name="members-of-types-and-class-inheritance"></a>型別和類別繼承的成員  
 屬性和事件，您會看到顯示的 XAML 成員為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類型通常都繼承自基底型別。 例如，請考量以下範例︰ `<Button Background="Blue" .../>`。 <xref:System.Windows.Controls.Control.Background%2A>屬性不是立即宣告的屬性上<xref:System.Windows.Controls.Button>類別中，如果您要查看的類別定義、 反映結果或文件。 相反地，<xref:System.Windows.Controls.Control.Background%2A>繼承自基底<xref:System.Windows.Controls.Control>類別。  
  
 類別的繼承行為的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 項目是從 XML 標記的結構描述強制執行解譯顯著不同。 類別繼承可能會變得複雜，特別是當中繼的基底類別是抽象類別，或當牽涉到介面時。 這就是一組 XAML 項目和其所允許的屬性而難以代表精確且完全使用結構描述型別通常用於[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]程式設計、 DTD 或 XSD 格式。 另一個原因是該擴充性和 XAML 語言本身的型別對應功能不允許的類型和成員的任何固定表示法的完整性。  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>物件項目語法  
 *物件項目語法*是藉由宣告的 XML 項目產生的 CLR 類別或結構的 XAML 標記語法。 這個語法類似於其他標記語言，例如 HTML 項目語法。 物件項目語法是以左的角括號 （\<), followed immediately by the type name of the class or structure being instantiated. followed="" immediately="" by="" the="" type="" name="" of="" the="" class="" or="" structure="" being="">\</), followed immediately by the type name of the class or structure being instantiated.> 零個或多個空格可遵循的型別名稱，以及零個或多個屬性也可以宣告物件項目上有一或多個空格分隔每個屬性名稱 = 「 值 」 配對。 最後，下列其中一項必須為真︰  
  
-   此項目和標記必須先關閉以正斜線 （/） 後面緊接跟著右角括弧 (>)。  
  
-   必須完成的開頭標記的右角括號 (>)。 其他物件項目、 屬性項目或內部的文字，可以遵循的開頭標記。 完全內容可能會包含在這裡通常受限於物件模型的項目。 對等的物件項目結尾標記也必須位於正確的巢狀，並使用其他的開頭和結尾標記組平衡。  
  
 XAML 由.NET 實作有一組物件項目對應至型別，屬性至屬性或事件和 CLR 命名空間加上組件的 XAML 命名空間的規則。 WPF 和.NET Framework 中，XAML 物件項目對應至[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]參考的組件中所定義的型別和屬性會對應至這些型別的成員。 當您參考的 CLR 型別，在 XAML 中時，您可以存取該型別繼承的成員。  
  
 例如，下列範例是具現化的新執行個體的物件項目語法<xref:System.Windows.Controls.Button>類別，並也會指定<xref:System.Windows.FrameworkElement.Name%2A>屬性和該屬性的值︰  
  
 [!code-xml[XAMLOvwSupport#SyntaxOE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 下列範例是物件也包含 XAML 內容屬性語法的項目語法。 內含的內部文字將會用來設定<xref:System.Windows.Controls.TextBox>XAML 內容屬性，<xref:System.Windows.Controls.TextBox.Text%2A>。  
  
 [!code-xml[XAMLOvwSupport#ThisIsATextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>內容模型  
 類別可能會以 XAML 物件項目語法，以支援使用，但是該項目將只正常運作的應用程式或網頁中放置在整體內容模型或項目樹狀結構的預期的位置時。 例如， <xref:System.Windows.Controls.MenuItem>通常只應放為子系<xref:System.Windows.Controls.Primitives.MenuBase>衍生類別，例如<xref:System.Windows.Controls.Menu>。 內容模型的特定項目會記載為控制項和其他的類別頁面上的 「 註解的一部分[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類別可用來做為 XAML 項目。  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>物件項目屬性  
 在 XAML 中的屬性會設定各種不同的可能語法。 何種語法可用於特定屬性而異，根據您要設定的屬性的基礎類型系統特性。  
  
 藉由設定屬性的值，您加入功能或特性的物件存在於執行的階段物件圖形中。 從物件項目所建立的物件的初始狀態為基礎的預設建構函式的行為。 通常，您的應用程式會使用不完全的預設執行個體指定的物件。  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>屬性語法 （屬性）  
 屬性語法是屬性的值設定現有的物件項目上宣告屬性的 XAML 標記語法。 屬性名稱必須符合 CLR 成員名稱，會將備份的相關物件項目類別的屬性。 屬性名稱後面接著指派運算子 （=）。 屬性值必須以引號括住的字串。  
  
> [!NOTE]
>  您可以使用替代引號將放在屬性中的常值引號。 例如您可以使用單引號做為宣告字串，包含雙引號字元內。 不論您使用單引號或雙引號時，您應該使用相符的配對來開啟和關閉屬性值字串。 另外還有逸出序列或其他技術可用來解決任何特定的 XAML 語法所加諸的字元限制。 請參閱[XML 字元實體和 XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)。  
  
 若要設定透過屬性語法，屬性必須是公用的因此必須是可寫入。 在支援類型系統屬性的值必須是實值型別，或必須參考型別可以具現化或存取相關時，XAML 處理器所參考的支援類型。  
  
 WPF XAML 事件之事件的參考做為屬性名稱必須具有公用和具有公用委派。  
  
 屬性或事件必須是類別或結構所包含的物件項目所具現化的成員。  
  
### <a name="processing-of-attribute-values"></a>屬性值的處理  
 XAML 處理器會處理包含在開頭和結尾引號的字串值。 屬性，預設的處理行為是由基礎 CLR 屬性的型別決定。  
  
 屬性值會填入下列其中一種使用此處理順序︰  
  
1.  如果 XAML 處理器遇到大括號或物件項目衍生自<xref:System.Windows.Markup.MarkupExtension>，然後參考的標記延伸會先評估而不是處理值為字串，並使用標記延伸模組所傳回的物件做為值。 在許多情況下傳回標記延伸的物件會參考現有的物件或會評估延後到執行階段，並不是新具現化的物件的運算式。  
  
2.  如果屬性宣告與屬性化<xref:System.ComponentModel.TypeConverter>，該屬性的值型別已宣告或使用屬性化<xref:System.ComponentModel.TypeConverter>屬性的字串值送出至轉換輸入型別轉換子，轉換器會傳回新的物件執行個體。  
  
3.  如果沒有任何<xref:System.ComponentModel.TypeConverter>，會嘗試直接轉換成屬性型別。 這個最後一個層級是直接在 XAML 語言基本類型或列舉型別 （剖析器會存取相符的值） 的具名常數的名稱檢查之間的剖析器原生值轉換。  
  
#### <a name="enumeration-attribute-values"></a>列舉屬性值  
 在 XAML 中的列舉型別處理在本質上 XAML 剖析器，以及藉由指定其中一個列舉的具名常數的名稱應該指定列舉的成員。  
  
 （attribute） 的列舉值，對於原生的行為就是處理屬性值的字串，並解析為其中一個列舉值。 您沒有指定列舉型別格式*列舉*。*值*，與您在程式碼。 相反地，您指定只有*值*，和*列舉*由您設定屬性的型別推斷。 如果您指定屬性在*列舉*。*值*表單，它將會無法正確解析。  
  
 若是旗列舉型別，此行為根據<xref:System.Enum.Parse%2A?displayProperty=fullName>方法。 您可以指定多個旗列舉值以逗號區隔每個值。 不過，您無法合併不旗標式的列舉值。 比方說，您無法使用逗號語法來嘗試建立<xref:System.Windows.Trigger>，充當 （attribute） 列舉型別的多個條件︰  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 支援可在 XAML 中設定的屬性旗列舉型別是在 WPF 中極少數。 不過，一個這類列舉型別是<xref:System.Windows.Media.StyleSimulations>。 比方說，可用以逗點分隔旗屬性語法來修改的 「 備註 」 中所提供的範例<xref:System.Windows.Documents.Glyphs>類別;`StyleSimulations = "BoldSimulation"`可能會變得`StyleSimulations = "BoldSimulation,ItalicSimulation"`。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=fullName>是另一個屬性可在其中指定多個列舉值。 不過，這個屬性是特殊的情況下，因為<xref:System.Windows.Input.ModifierKeys>列舉型別支援它自己的型別轉換子。 修飾詞的型別轉換子會使用加號 （+），做為分隔符號，而不是逗號 （，）。 此轉換支援更傳統的語法來表示按鍵的組合，在 Microsoft Windows 程式設計中，例如 「 Ctrl + Alt。  
  
### <a name="properties-and-event-member-name-references"></a>屬性和事件成員名稱參考  
 當指定屬性時，您可以參考任何屬性或事件，您針對包含的物件項目具現化的 CLR 型別的成員形式存在。  
  
 或者，您可以參考附加的屬性，或是附加事件，獨立於包含的物件項目。 （附加的屬性會在後續章節中討論）。  
  
 您也可以將名稱是透過預設命名空間使用的所有物件的任何事件*typeName*。*事件*部分限定的名稱; 這個附加路由事件的處理常式的支援此處理常式要處理事件路由子項目，但父項目也沒有該事件在其成員資料表中的語法。 這個語法類似於附加的事件語法，但這裡的事件就不會真的附加的事件。 相反地，您所參考的限定名稱的事件。 如需詳細資訊，請參閱[路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。  
  
 某些情況下，有時會提供屬性名稱做為屬性，而不是屬性名稱的值。 該屬性名稱也可以包含辨識符號，例如表單中指定的屬性*ownerType*。*dependencyPropertyName*。 在 XAML 中撰寫樣式或範本時，常會使用此案例中。 提供做為屬性值的屬性名稱的處理規則不同，而且受到所設定的屬性類型，或藉由特定 WPF 子系統的行為。 如需詳細資訊，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
 另一個屬性名稱的使用方式時，屬性值描述屬性屬性關聯性。 這項功能會使用資料繫結和分鏡腳本的目標，而且會啟用<xref:System.Windows.PropertyPath>類別，而且其型別轉換子。 如需查閱語意的更完整說明，請參閱[PropertyPath XAML 語法](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)。  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>屬性項目語法  
 *屬性項目語法*是背道而馳稍微從基本的 XML 語法規則的項目語法。 在 XML 中，屬性的值是現行的字串，唯一可能的變化是正在使用哪一種字串編碼格式。 在 XAML 中，您可以指派其他物件項目是屬性的值。 屬性項目語法會啟用這項功能。 而不是指定為元素標記內之屬性的屬性，指定的屬性是使用 開啟項目中，標記*elementTypeName*。*propertyName*表單內，指定屬性的值和屬性項目然後關閉。  
  
 具體來說，語法是以左的角括號 （\<), followed immediately by the type name of the class or structure that the property element syntax is contained within. followed="" immediately="" by="" the="" type="" name="" of="" the="" class="" or="" structure="" that="" the="" property="" element="" syntax="" is="" contained="">\</), followed immediately by the type name of the class or structure that the property element syntax is contained within.> 這後面緊接跟著一個點 （.），然後由屬性的名稱，然後的右角括號 (>)。 如同屬性語法，該屬性必須存在於指定的型別宣告公用成員。 要指派給屬性的值會包含在屬性項目。 一般而言，指定為一或多個 object 元素的值，指定做為值的物件是案例，因為該屬性的項目語法為了解決。 最後，指定相同對等的結尾標記*elementTypeName*。*propertyName*組合必須，以提供適當的巢狀結構和平衡與其他項目的標記。  
  
 例如，以下是屬性的項目語法<xref:System.Windows.FrameworkElement.ContextMenu%2A>屬性<xref:System.Windows.Controls.Button>。  
  
 [!code-xml[XAMLOvwSupport#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 屬性項目內的值也指定為內部的文字，在案例中所指定的屬性類型的基本值類型，例如<xref:System.String>，或列舉型別在指定的名稱。 兩種使用方法是有點不常見，因為每個案例中也可以使用屬性語法更簡單。 屬性項目填入字串的其中一個案例的屬性不是 XAML 內容屬性，但是仍然用於 UI 文字表示法，才會出現在 UI 文字所需的特定空白項目，例如換。 屬性語法無法保留換行符號，但屬性項目語法可以只要保留的空白字元是作用中 (如需詳細資訊，請參閱[在 XAML 中的空白字元處理](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md))。 另一個案例是讓[X:uid 指示詞](../../../../docs/framework/xaml-services/x-uid-directive.md)可以套用至屬性項目並因此標記內的值應該當地語系化 WPF 中的值輸出 BAML 或以其他技術。  
  
 屬性項目不會呈現 WPF 的邏輯樹狀結構中。 屬性項目是只是特定語法來設定屬性，而非執行個體或物件支援的項目。 (如邏輯樹狀結構的詳細資訊，請參閱[WPF 中的樹狀結構](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)。)  
  
 屬性受到屬性和屬性的項目語法，兩個語法通常都有相同的結果，不過微妙，例如空白字元處理可以之間的語法稍有差異。  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>集合語法  
 XAML 規格要求 XAML 處理器實作識別其中實值型別是集合的屬性。 在.NET 中的一般 XAML 處理器實作根據 managed 程式碼和 CLR，用來識別集合型別，透過下列其中一項︰  
  
-   型別會實作<xref:System.Collections.IList>。  
  
-   型別會實作<xref:System.Collections.IDictionary>。  
  
-   型別衍生自<xref:System.Array>(如需 XAML 中的陣列的詳細資訊，請參閱[X:array 標記延伸](../Topic/x:Array%20Markup%20Extension.md)。)  
  
 如果屬性的型別是集合，然後推斷的集合型別不必指定為物件項目在標記中。 相反地，即將成為的項目集合中的項目會指定為一或多個屬性項目的子項目。 每個這類項目載入期間評估的物件，以及加入至集合，藉由呼叫`Add`隱含的集合的方法。 例如，<xref:System.Windows.Style.Triggers%2A>屬性<xref:System.Windows.Style>採用特製化的集合型別<xref:System.Windows.TriggerCollection>，它會實作<xref:System.Collections.IList>。 不需要具現化<xref:System.Windows.TriggerCollection>物件標記中的項目。 相反地，您指定一個或多個<xref:System.Windows.Trigger>做為項目內的項目`Style.Triggers`屬性項目，其中<xref:System.Windows.Trigger>（或衍生的類別） 是預期的項目類型的強型別和隱含的類型<xref:System.Windows.TriggerCollection>。  
  
 [!code-xml[XAMLOvwSupport#SyntaxPECollection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 屬性可能是集合型別和 XAML 內容屬性，該型別和衍生型別，其中會討論這個主題的下一節。  
  
 隱含的集合項目會建立成員邏輯樹狀結構表示法中，即使它不會顯示為項目在標記中。 父類型的建構函式通常會具現化執行集合的其中一個屬性，並一開始是空的集合會成為物件樹狀結構的一部分。  
  
> [!NOTE]
>  泛型 list 與 dictionary 介面 (<xref:System.Collections.Generic.IList%601>和<xref:System.Collections.Generic.IDictionary%602>) 不支援集合偵測。\</TKey, TValue> 不過，您可以使用<xref:System.Collections.Generic.List%601>類別做為基底類別，因為它會實作<xref:System.Collections.IList>直接或<xref:System.Collections.Generic.Dictionary%602>做為基底類別，因為它會實作<xref:System.Collections.IDictionary>直接。\</TKey, TValue>  
  
 在集合型別的.NET 參考資料頁中，這個語法與刻意略過其中集合的物件項目會偶爾會註明 XAML 語法 > 章節中做為隱含的集合語法。  
  
 除了根項目，做為另一個項目的子項目巢狀的 XAML 檔案中的每個物件項目其實是一個或多個下列情況下的項目︰ 其父項目，或指定的父項目 (XAML 內容屬性將在後續章節中討論) XAML 內容屬性值的項目隱含的集合屬性的成員。 換句話說，父項目和子項目標記頁面中的關聯是根目錄的單一物件，而且根目錄下的每個物件項目為提供的父代，屬性值的單一執行個體或其中一個項目也是父系的集合型別屬性值在集合內。 此單一根概念是一般的 xml，並經常加強的 Api，例如 XAML 的載入行為<xref:System.Windows.Markup.XamlReader.Load%2A>。  
  
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
  
 請注意，它不一定明確宣告集合。 例如，嘗試宣告<xref:System.Windows.TriggerCollection>明確中先前所示<xref:System.Windows.Style.Triggers%2A>範例將會失敗。 明確宣告集合需要集合類別必須支援的預設建構函式，和<xref:System.Windows.TriggerCollection>並沒有預設建構函式。  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML 內容屬性  
 XAML 內容的語法是才會啟用指定的類別一個語法<xref:System.Windows.Markup.ContentPropertyAttribute>做為其類別宣告的一部分。 <xref:System.Windows.Markup.ContentPropertyAttribute>參考該類型的項目 （包括衍生的類別） 的內容屬性的屬性名稱。 時由 XAML 處理器所處理，該物件的 XAML 內容屬性的值會指派任何子項目或找到的開頭和結尾標記的物件項目之間的內部文字。 您可以指定明確的屬性項目之內容的屬性，但 XAML 語法 」 一節中的.NET 參考中通常不顯示這種使用方式。 明確/詳細的技術有一些價值標記的清晰度或的標記樣式，但通常內容屬性的目的是要簡化標記，以便為父子式直覺的方式相關的項目可以直接巢狀。 項目上的其他屬性的屬性項目標記不被指派為 「 內容 」，每個嚴格的 XAML 語言定義。在 XAML 剖析器的處理順序來處理先前並不會被視為是 「 內容 」。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>必須是連續的 XAML 內容屬性值  
 XAML 內容屬性的值必須完全之前或之後任何其他的屬性項目完全授予該物件的項目上。 XAML 內容屬性的值會指定為字串，或一或多個物件是否也是如此。 例如，下列標記不會剖析︰  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 基本上，這是不合法因為如果這種語法明確使用之內容屬性的屬性項目語法，然後內容屬性會設定兩次︰  
  
```  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 類似的不合法的範例為內容屬性是集合，並子項目會穿插屬性項目︰  
  
```  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>   
## <a name="content-properties-and-collection-syntax-combined"></a>內容屬性以及集合語法結合  
 多個單一物件項目做為內容，才能接收內容屬性的型別必須特別會是集合型別。 類似於集合型別的屬性項目語法，XAML 處理器必須識別屬於集合型別的型別。 如果項目有 XAML 內容屬性的 XAML 內容屬性的型別是集合，然後隱含的集合型別不需要指定成物件項目在標記中，XAML 內容屬性不需要指定為屬性項目。 因此顯而易見的內容模型，在標記中現在有一個以上的子項目指派做為內容。 下列是內容語法<xref:System.Windows.Controls.Panel>衍生的類別。 所有<xref:System.Windows.Controls.Panel>衍生的類別建立 XAML 內容屬性設為<xref:System.Windows.Controls.Panel.Children%2A>，皆需要型別的值<xref:System.Windows.Controls.UIElementCollection>。  
  
 [!code-xml[XAMLOvwSupport#SyntaxContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 請注意，都沒有的屬性項目<xref:System.Windows.Controls.Panel.Children%2A>的項目也不<xref:System.Windows.Controls.UIElementCollection>需要在標記中。 這是 XAML 設計功能，以便以遞迴方式包含項目會定義[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]會更直覺的方式表示的直屬父系-子系項目關聯性，而不需要中介屬性項目標記或集合物件的巢狀項目樹狀結構。 事實上， <xref:System.Windows.Controls.UIElementCollection>中不能指定明確標記為物件項目所設計。 其唯一用途是做為隱含的集合，因為<xref:System.Windows.Controls.UIElementCollection>不會公開公用預設建構函式，因此無法具現化為物件項目。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>混合屬性項目和內容屬性的物件中的物件項目  
 XAML 規格會宣告用來填滿 XAML 物件項目內內容屬性的物件項目必須是連續的並不混合 XAML 處理器可以強制執行。 針對混合屬性項目和內容的這項限制由強制執行[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 處理器。  
  
 物件項目內的第一個立即標記為可能的子物件項目。 然後您可以採用屬性元素。 或者，您可以指定一或多個屬性項目，然後內容，然後再多個屬性項目。 但是，一旦屬性項目後面的內容，您不能引入任何進一步的內容，您只能新增屬性項目。  
  
 此內容 / 屬性項目的順序要求不適用於做為內容的內部文字。 不過，它仍維持內部文字連續的因為重要的空白字元很難在標記中以視覺化方式偵測，如果屬性項目會穿插內部文字好的標記樣式。  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML 命名空間  
 預設的 XAML 命名空間以外的 XAML 命名空間指定任何上述語法範例。 在一般[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式，預設 XAML 命名空間指定為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]命名空間。 您可以指定非預設的 XAML 命名空間的 XAML 命名空間，但仍然使用類似的語法。 但是，任何一處類別會命名為無法存取預設 XAML 命名空間中的類別名稱前面必須有的 XAML 命名空間前置詞對應至對應的 CLR 命名空間。 例如，`<custom:Example/>`物件具現化的執行個體的項目語法`Example`類別，其中包含該類別 （和可能的外部組件資訊，其中包含支援型別） 的 CLR 命名空間先前已對應至`custom`前置詞。  
  
 如需 XAML 命名空間的詳細資訊，請參閱[XAML 命名空間和命名空間對應 WPF XAML](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>標記延伸  
 XAML 定義的程式設計實體，可讓從字串屬性值或物件項目，一般 XAML 處理器處理逸出字元，而且會延後到支援類別處理的標記延伸。 識別 XAML 處理器的標記延伸模組時使用屬性語法的左大括號 （{}），加上右大括號 （}） 以外的任何字元的字元。 第一個字串後面的左大括號必須參考類別，提供特定延伸行為，其中的參考可以省略子字串"Extension"，如果子字串是真正的類別名稱的一部分。 因此，可能會出現一個空格，，然後每個後續字元做為輸入的延伸模組實作中，直到遇到右大括號。  
  
 .NET XAML 實作會使用<xref:System.Windows.Markup.MarkupExtension>抽象類別，做為所有支援的標記延伸的基礎[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以及其他架構或技術。 標記延伸的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]特別實作通常為了提供方法，以參考其他現有的物件，或是延後將會在執行階段評估的物件參考。 例如，簡單的 WPF 資料繫結透過指定`{Binding}`標記延伸來取代通常需要特定屬性的值。 許多 WPF 標記延伸可讓其中一個屬性的語法所不可能的內容屬性語法。 例如，<xref:System.Windows.Style>物件是相當複雜的型別，其中包含一系列巢狀的物件和屬性。 在 WPF 中的樣式通常會定義中的資源為<xref:System.Windows.ResourceDictionary>，然後透過其中一種要求資源的兩個 WPF 標記延伸之參考。 標記延伸會延遲評估的資源查閱的屬性值，並可讓您提供的值<xref:System.Windows.FrameworkElement.Style%2A>屬性，取得類型<xref:System.Windows.Style>，請在屬性語法，如下列範例所示︰  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 在這裡，`StaticResource`識別<xref:System.Windows.StaticResourceExtension>提供標記延伸實作的類別。 下一個字串`MyStyle`做為非預設的輸入<xref:System.Windows.StaticResourceExtension>建構函式，從擴充字串的參數會要求宣告<xref:System.Windows.ResourceKey>。 `MyStyle`預計要[X:key](../../../../docs/framework/xaml-services/x-key-directive.md)值<xref:System.Windows.Style>定義為資源。 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)使用量要求資源用來提供<xref:System.Windows.Style>透過靜態資源查閱邏輯在載入時間的屬性值。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。 如需標記延伸和程式設計功能，在一般的.NET XAML 實作中啟用其他 XAML 的參考，請參閱[XAML 命名空間 （x:）語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)。 WPF 特定標記延伸，請參閱[WPF XAML 延伸](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)。  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>附加屬性  
 附加的屬性是一種程式設計概念，導入 XAML 屬性可以讓擁有和定義的特定型別，但是將做為屬性或屬性的項目上的任何項目。 主要案例附加的屬性是針對是要回報資訊給父元素的標記結構中的子項目，而不需要廣泛地共用的物件模型之間的所有項目。 相反地，附加的屬性可供報表資訊項目子系的父項目。 附加的屬性，以及如何建立您自己的詳細資訊的用途附加屬性，請參閱[附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)。  
  
 附加的屬性使用的語法，表面上類似於屬性項目語法，，，您也指定*typeName*。*propertyName*組合。 有兩個重大差異：  
  
-   您可以使用*typeName*。*propertyName*即使設定透過屬性語法附加的屬性的組合。 附加的屬性是唯一的情況，其中限定屬性名稱是屬性語法的需求。  
  
-   您也可以使用附加屬性的屬性項目語法。 不過，對於一般的屬性項目語法， *typeName*您指定的物件項目，其中包含屬性的項目。 如果您參照到附加的屬性，然後在*typeName*是附加的屬性，而不包含的物件項目會定義的類別。  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>附加事件  
 附加的事件都是導入 XAML，事件可以定義特定的型別，但處理常式可能會附加在物件中的任何項目上的另一個程式設計概念。 在 WOF 實作中，定義附加的事件的型別通常是靜態型別定義的服務，而且有時候那些附加的事件會公開公開服務的型別中的路由的事件別名。 附加事件處理常式所指定屬性語法。 使用附加的事件屬性語法是展開的附加事件，以允許*typeName*。*eventName*使用方式，其中*typeName*為類別，提供`Add`和`Remove`附加的事件基礎結構的事件處理常式存取子和*eventName*事件名稱。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML 根項目結構  
 下表顯示典型 XAML 根項目細分，顯示的特定屬性的根項目︰  
  
|||  
|-|-|  
|`<Page`|開啟根項目的物件項目|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|預設值 ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML 命名空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|在 XAML 語言 XAML 命名空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|將標記連接到任何程式碼後置的部分類別宣告為部分類別定義|  
|`>`|物件項目結尾的根目錄。 因為項目包含子項目沒有尚未關閉物件|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>選擇性的找 XAML 使用方式  
 下列章節說明 XAML 用法，XAML 處理器技術支援的但可以產生詳細等級或其他美觀的問題與 XAML 檔案剩餘人們可讀取時可能會影響您開發包含 XAML 來源應用程式。  
  
### <a name="optional-property-element-usages"></a>選擇性的屬性項目用法  
 選擇性的屬性項目使用方式包括明確地寫出項目內容的屬性，XAML 處理器會將視為隱含。 比方說，當您宣告的內容<xref:System.Windows.Controls.Menu>，您可以選擇明確宣告<xref:System.Windows.Controls.ItemsControl.Items%2A>集合<xref:System.Windows.Controls.Menu>做為`<Menu.Items>`屬性項目標記，並將每個<xref:System.Windows.Controls.MenuItem>內`<Menu.Items>`，而不是使用隱含 XAML 處理器的行為，目的所有子項目<xref:System.Windows.Controls.Menu>必須<xref:System.Windows.Controls.MenuItem>並放置於<xref:System.Windows.Controls.ItemsControl.Items%2A>集合。 有時候選擇性的使用方式有助於以視覺化方式在標記中所示，釐清物件結構。 或明確的屬性項目用法有時可以避免技術上正常運作，但在視覺上令人困惑，例如屬性值內的巢狀的標記延伸的標記。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完整限定的 typeName.memberName 屬性  
 The *typeName*.*memberName*形成屬性實際上運作比只是路由的事件案例普遍的。 但在其他情況下，該表單是多餘，而且應該避免，如果僅基於標記樣式和可讀性。 在下列範例中，每三個參考<xref:System.Windows.Controls.Control.Background%2A>屬性是完全相同︰  
  
 [!code-xml[XAMLOvwSupport#TypeNameProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`可以運作，因為該屬性的限定的查閱<xref:System.Windows.Controls.Button>成功 (<xref:System.Windows.Controls.Control.Background%2A>繼承自控制項) 和<xref:System.Windows.Controls.Button>的物件項目類別或基底類別。 `Control.Background`因為<xref:System.Windows.Controls.Control>類別會實際定義<xref:System.Windows.Controls.Control.Background%2A>和<xref:System.Windows.Controls.Control>是<xref:System.Windows.Controls.Button>基底類別。  
  
 不過，下列*typeName*。*memberName*表單範例無法運作，因此顯示加上註解︰  
  
 [!code-xml[XAMLOvwSupport#TypeNameBadProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>是另一個衍生的類別<xref:System.Windows.Controls.Control>，而且如果已指定`Label.Background`內<xref:System.Windows.Controls.Label>物件項目，會處理這種使用方式。 不過，因為<xref:System.Windows.Controls.Label>不是類別或基底類別的<xref:System.Windows.Controls.Button>，XAML 處理器的行為就是再處理`Label.Background`為附加屬性。 `Label.Background`不是可用的附加的屬性，而且這種用法會失敗。  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName 屬性項目  
 如何以類似方式*typeName*。*memberName*形式的運作方式的屬性語法*baseTypeName*。*memberName*語法適用於屬性項目語法。 例如，下列語法適用於︰  
  
 [!code-xml[XAMLOvwSupport#GoofyPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 屬性項目，指定為`Control.Background`即使屬性項目所包含之`Button`。  
  
 但就像*typeName*。*memberName*的屬性，格式*baseTypeName*。*memberName*是不佳的樣式，在標記中，而且您應該避免這樣。  
  
## <a name="see-also"></a>另請參閱  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [XAML 命名空間 （x:）語言功能](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [WPF XAML 擴充功能](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Typeconverter 和 XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)   
 [XAML 和 WPF 的自訂類別](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)