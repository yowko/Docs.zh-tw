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
ms.openlocfilehash: dbff4bed59c8d1e861555676578b52528e2aebbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186191"
---
# <a name="xaml-syntax-in-detail"></a>XAML 語法詳細資料
本主題定義用於描述 XAML 語法元素的術語。 這些術語在本文檔的其餘部分中經常使用，具體用於 WPF 文檔，以及使用 XAML 或其他框架的其他框架，這些框架或在 System.Xaml 級別啟用的 XAML 語言支援。 本主題將展開主題[XAML 概述 （WPF）](../../../desktop-wpf/fundamentals/xaml.md)仲介紹的基本術語。  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>XAML 語言規範  
 此處定義的 XAML 語法術語也在 XAML 語言規範中定義或引用。 XAML 是基於 XML 的語言，它遵循或擴展了 XML 結構規則。 某些術語來自或基於描述 XML 語言或 XML 文件物件模型時常用的術語。  
  
 有關 XAML 語言規範的詳細資訊，請從 Microsoft 下載中心下載[\[MS-XAML。\] ](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf)  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML 和 CLR  
 XAML 是一種標記語言。 通用語言運行時 （CLR） （CLR） 的名稱所暗示，支援運行時執行。 XAML 本身並不是 CLR 運行時直接使用的常見語言之一。 相反，您可以將 XAML 視為支援其自己的類型系統。 WPF 使用的特定 XAML 解析系統構建在 CLR 和 CLR 類型系統上。 XAML 類型映射到 CLR 類型，以在分析 WPF 的 XAML 時具現化運行時表示。 因此，本文檔中關於語法的討論的其餘部分將包括對 CLR 類型系統的引用，即使 XAML 語言規範中的等效語法討論沒有。 （根據 XAML 語言規範級別，XAML 類型可以映射到任何其他類型系統，其中不必是 CLR，但需要創建和使用不同的 XAML 解析器。  
  
#### <a name="members-of-types-and-class-inheritance"></a>類型和類繼承的成員  
 屬性和事件作為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類型的 XAML 成員顯示時通常從基類型繼承。 例如，請考慮此示例： `<Button Background="Blue" .../>`。 如果要<xref:System.Windows.Controls.Control.Background%2A>查看類定義、反射結果或文檔，<xref:System.Windows.Controls.Button>則該屬性不是類上的立即聲明屬性。 <xref:System.Windows.Controls.Control.Background%2A>而是從基<xref:System.Windows.Controls.Control>類繼承的。  
  
 XAML 元素[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]的類繼承行為與 XML 標記的架構強制解釋有重大背離。 類繼承可能會變得複雜，尤其是在中間基類是抽象的，或者涉及介面時。 這是 XAML 元素集及其允許屬性難以準確、完整地使用通常用於 XML 程式設計的架構類型（如 DTD 或 XSD 格式）的一個原因。 另一個原因是 XAML 語言本身的可擴充性和類型映射功能排除了允許類型和成員的任何固定表示形式的完整性。  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>物件元素語法  
 *物件元素語法*是 XAML 標記語法，它通過聲明 XML 元素具現化 CLR 類或結構。 此語法類似于其他標記語言（如 HTML）的元素語法。 物件元素語法以左角度括弧 （），\<緊接著是具現化的類或結構的類型名稱。 零個或多個空格可以遵循類型名稱，也可以在物件元素上聲明零個或多個屬性，其中一個或多個空格分隔每個屬性名稱 ="值"對。 最後，以下必須為 true：  
  
- 元素和標記必須用前斜杠 （/） 緊接，然後緊跟直角支架 （>）。  
  
- 開口標記必須由直角支架（>）完成。 其他物件元素、屬性元素或內部文本可以遵循打開標記。 此處可能包含的內容通常受元素的物件模型的約束。 物件元素的等效關閉標記也必須存在，以適當的嵌套並與其他打開和關閉標記對平衡。  
  
 .NET 實現的 XAML 具有一組規則，這些規則將物件元素映射到類型、屬性或事件的屬性以及 XAML 命名空間到 CLR 命名空間加上程式集。 對於 WPF 和 .NET，XAML 物件元素映射到引用程式集中定義的 .NET 類型，屬性對應到這些類型的成員。 在 XAML 中引用 CLR 類型時，您也有權訪問該類型的繼承成員。  
  
 例如，以下示例是物件元素語法，它具現化<xref:System.Windows.Controls.Button>類的新實例，並指定該<xref:System.Windows.FrameworkElement.Name%2A>屬性的屬性和值：  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 下面的示例是物件元素語法，該語法還包括 XAML 內容屬性語法。 中包含的內部文本將用於設置<xref:System.Windows.Controls.TextBox>XAML 內容屬性 。 <xref:System.Windows.Controls.TextBox.Text%2A>  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>內容模型  
 類在語法方面可能支援作為 XAML 物件元素的用法，但該元素只有在放置在總體內容模型或元素樹的預期位置時，才會在應用程式或頁面中正常運行。 例如，通常<xref:System.Windows.Controls.MenuItem>應僅作為<xref:System.Windows.Controls.Primitives.MenuBase>派生類（如<xref:System.Windows.Controls.Menu>） 的子級放置。 特定元素的內容模型作為控制項和其他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]類可用作 XAML 元素的類頁上的備註的一部分進行記錄。  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>物件元素的屬性  
 XAML 中的屬性由各種可能的語法設置。 哪些語法可用於特定屬性將因所設置的屬性的基礎類型系統特徵而異。  
  
 通過設置屬性的值，可以像運行時物件圖中存在的物件一樣，向物件添加要素或特徵。 從物件元素創建的物件的初始狀態基於無參數建構函式行為。 通常，應用程式將使用任何給定物件的完全預設實例以外的內容。  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>屬性 (Attribute) 語法 (屬性(Property))  
 屬性語法是 XAML 標記語法，通過在現有物件元素上聲明屬性來設置屬性的值。 屬性名稱必須與支援相關物件元素的類屬性的 CLR 成員名稱匹配。 屬性名稱後跟指派運算子 （*）。 屬性值必須是包含在引號中的字串。  
  
> [!NOTE]
> 可以使用交替引號在屬性中放置文本引號。 例如，可以使用單引號作為聲明包含其中雙引號字元的字串的方法。 無論使用單引號還是雙引號，都應使用匹配對來打開和關閉屬性值字串。 還有一些逸出序列或其他技術可用於解決任何特定 XAML 語法施加的字元限制。 請參閱[XML 字元實體和 XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md)。  
  
 要通過屬性語法進行設置，屬性必須是公共的，並且必須是可寫入的。 支援類型系統中的屬性值必須是數值型別，或者必須是訪問相關備份類型時 XAML 處理器可以具現化或引用的參考型別。  
  
 對於 WPF XAML 事件，引用為屬性名稱的事件必須是公共的，並且具有公共委託。  
  
 屬性或事件必須是由包含物件元素具現化的類或結構的成員。  
  
### <a name="processing-of-attribute-values"></a>屬性值的處理  
 首開和收盤引號中包含的字串值由 XAML 處理器處理。 對於屬性，預設處理行為由基礎 CLR 屬性的類型確定。  
  
 屬性值由以下之一填充，使用此處理順序：  
  
1. 如果 XAML 處理器遇到大括弧或派生自<xref:System.Windows.Markup.MarkupExtension>的物件元素，則首先計算引用的標記擴展，而不是將該值作為字串處理，標記擴展返回的物件用作值。 在許多情況下，標記擴展返回的物件將是對現有物件的引用，或將計算推遲到運行時的運算式，而不是新具現化的物件。  
  
2. 如果屬性用屬性聲明<xref:System.ComponentModel.TypeConverter>，或者該屬性的數值型別用屬性<xref:System.ComponentModel.TypeConverter>聲明，則屬性的字串值將作為轉換輸入提交到類型轉換器，轉換器將返回一個新的物件實例。  
  
3. 如果沒有<xref:System.ComponentModel.TypeConverter>，則嘗試直接轉換為屬性類型。 此最終級別是 XAML 語言基元類型之間的解析器本機值的直接轉換，或對枚舉中命名常量的名稱的檢查（解析器隨後訪問匹配值）。  
  
#### <a name="enumeration-attribute-values"></a>枚舉屬性值  
 XAML 中的枚舉由 XAML 解析器進行內在處理，枚舉成員應通過指定枚舉命名常量之一的字串名稱來指定枚舉。  
  
 對於非標記枚舉值，本機行為是處理屬性值的字串並將其解析為枚舉值之一。 您不會在格式枚*舉*中指定枚舉。*值*，就像您在代碼中所做的一樣。 相反，您只指定*值*，而*枚舉*則由要設置的屬性的類型推斷。 如果在*枚舉*中指定屬性。*值*形式，它將不會正確解析。  
  
 對於正面枚舉，行為基於 方法<xref:System.Enum.Parse%2A?displayProperty=nameWithType>。 可以通過用逗號分隔每個值來為旗面枚舉指定多個值。 但是，不能合併不按標誌標記的枚舉值。 例如，不能使用逗號語法嘗試創建<xref:System.Windows.Trigger>對非標誌枚舉的多個條件具有作用的 語法：  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 在 WPF 中，支援在 XAML 中可設置的屬性的標記枚舉很少見。 但是，此類枚舉之一是<xref:System.Windows.Media.StyleSimulations>。 例如，您可以使用逗號分隔的標記屬性語法來修改<xref:System.Windows.Documents.Glyphs>類的備註中提供的示例;`StyleSimulations = "BoldSimulation"`可能變成`StyleSimulations = "BoldSimulation,ItalicSimulation"`。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>是另一個可以指定多個枚舉值的屬性。 但是，此屬性恰好是一個特殊情況，因為<xref:System.Windows.Input.ModifierKeys>枚舉支援其自己的類型轉換器。 修改器的類型轉換器使用加號 （+） 作為分隔符號而不是逗號 （，）。 此轉換支援更傳統的語法，以表示 Microsoft Windows 程式設計中的關鍵組合，例如"Ctrl_Alt"。  
  
### <a name="properties-and-event-member-name-references"></a>屬性和事件成員名稱引用  
 指定屬性時，可以引用作為為包含物件元素具現化的 CLR 類型的成員存在的任何屬性或事件。  
  
 或者，您可以引用附加的屬性或附加事件，而獨立于包含的物件元素。 （附加屬性將在接下來的部分中討論。  
  
 還可以使用*typeName*從可通過預設命名空間訪問的任何物件命名任何事件。*事件*部分限定名稱;此語法支援為路由事件附加處理常式，其中處理常式旨在處理來自子項目的事件路由，但父元素的成員表中也沒有該事件。 此語法類似于附加的事件語法，但此處的事件不是真正的附加事件。 相反，您引用的事件具有限定名稱。 有關詳細資訊，請參閱[路由事件概述](routed-events-overview.md)。  
  
 對於某些方案，屬性名稱有時作為屬性的值提供，而不是屬性名稱。 該屬性名稱還可以包括限定詞，例如表單*擁有者類型*中指定的屬性。*屬項屬性名稱*。 在 XAML 中編寫樣式或範本時，此方案很常見。 作為屬性值提供的屬性名稱的處理規則不同，並且受要設置的屬性類型或特定 WPF 子系統的行為控制。 有關詳細資訊，請參閱[樣式和範本](../controls/styling-and-templating.md)化。  
  
 屬性名稱的另一個用法是屬性值描述屬性-屬性關係時。 此功能用於資料繫結和分鏡腳本目標，並且由<xref:System.Windows.PropertyPath>類及其類型轉換器啟用。 有關查找語義的更完整說明，請參閱[屬性路徑 XAML 語法](propertypath-xaml-syntax.md)。  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>屬性元素語法  
 *屬性元素語法*是一種語法，它在某種程度上與元素的基本 XML 語法規則不同。 在 XML 中，屬性的值是事實字串，唯一可能的變化是使用哪個字串編碼格式。 在 XAML 中，可以將其他物件元素指定為屬性的值。 此屬性元素語法啟用此功能。 該屬性使用*元素TypeName*中的打開元素標記指定該屬性，而不是將屬性指定為元素標記中的屬性。*屬性名稱*表單中，在 其中指定屬性的值，然後關閉屬性元素。  
  
 具體而言，語法以左角度括弧 （）\<開頭，緊接著是屬性元素語法中包含的類或結構的類型名稱。 緊接著是一個點 （.），然後是屬性的名稱，然後是直角括弧 （>）。 與屬性語法一樣，該屬性必須存在於指定類型的已聲明的公共成員中。 要分配給該屬性的值包含在屬性元素中。 通常，該值作為一個或多個物件元素給出，因為將物件指定為值是屬性元素語法旨在解決的方案。 最後，指定相同*元素TypeName*的等效結束標記。*屬性名稱*組合必須提供，以適當的嵌套和平衡與其他元素標記。  
  
 例如，以下是 屬性的屬性的屬性元素語法<xref:System.Windows.FrameworkElement.ContextMenu%2A><xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 屬性元素中的值也可以作為內部文本給出，在指定的屬性類型為基元數值型別的情況下，例如<xref:System.String>， 或指定名稱的枚舉。 這兩個用法有些不常見，因為每個情況都可以使用更簡單的屬性語法。 使用字串填充屬性元素的一個方案是，對於不是 XAML 內容屬性但仍用於表示 UI 文本的屬性，並且特定的空白元素（如行饋送）必須出現在該 UI 文本中。 屬性語法無法保留行饋，但屬性元素語法可以，只要顯著的空白保留處於活動狀態（有關詳細資訊，請參閱[XAML 中的空白處理](../../../desktop-wpf/xaml-services/white-space-processing.md)）。 另一種情況是[，x：Uid 指令](../../../desktop-wpf/xaml-services/xuid-directive.md)可以應用於屬性元素，從而將 中的值標記為應在 WPF 輸出 BAML 或其他技術中當地語系化的值。  
  
 屬性元素未在 WPF 邏輯樹中表示。 屬性元素只是設置屬性的特定語法，而不是具有實例或物件支援它的元素。 （有關邏輯樹概念的詳細資訊，請參閱[WPF 中的樹](trees-in-wpf.md)。  
  
 對於同時支援屬性和屬性元素語法的屬性，這兩種語法通常具有相同的結果，儘管空格處理等細微之處在語法之間可能略有不同。  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>集合語法  
 XAML 規範要求 XAML 處理器實現標識數值型別為集合的屬性。 .NET 中的常規 XAML 處理器實現基於託管代碼和 CLR，它通過以下之一標識集合類型：  
  
- 類型實現<xref:System.Collections.IList>。  
  
- 類型實現<xref:System.Collections.IDictionary>。  
  
- 類型派生自<xref:System.Array>（有關 XAML 中的陣列的詳細資訊，請參閱[x：陣列標記擴展](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)。  
  
 如果屬性的類型是集合，則推斷的集合類型不需要在標記中指定為物件元素。 相反，打算成為集合中的項的元素被指定為屬性元素的一個或多個子項目。 每個此類項在載入期間計算到物件，並通過調用隱含集合`Add`的方法添加到集合中。 例如， 的<xref:System.Windows.Style.Triggers%2A><xref:System.Windows.Style>屬性採用專用集合類型<xref:System.Windows.TriggerCollection>， 實現<xref:System.Collections.IList>。 不必具現化標記中<xref:System.Windows.TriggerCollection>的物件元素。 <xref:System.Windows.Trigger>相反，您將一個或多個項指定為`Style.Triggers`屬性元素中的元素，其中<xref:System.Windows.Trigger>（或派生類）是強烈鍵入和隱式<xref:System.Windows.TriggerCollection>中的項類型所需的類型。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 屬性可以是集合類型，也可以是該類型和派生類型的 XAML 內容屬性，本主題的下一部分將對此進行討論。  
  
 隱式集合元素在邏輯樹表示形式中創建成員，即使它不作為元素出現在標記中。 通常，父類型的建構函式對其屬性之一的集合執行具現化，並且最初空集合將成為物件樹的一部分。  
  
> [!NOTE]
> 泛型清單和字典介面<xref:System.Collections.Generic.IList%601>（<xref:System.Collections.Generic.IDictionary%602>和 ） 不支援用於集合檢測。 但是，您可以將<xref:System.Collections.Generic.List%601>類用作基類，因為它直接實現<xref:System.Collections.IList>，或者<xref:System.Collections.Generic.Dictionary%602>作為基類實現，因為它直接實現。 <xref:System.Collections.IDictionary>  
  
 在集合類型的 .NET 參考頁中，在 XAML 語法部分中偶爾會將此語法與集合物件元素的故意省略記錄稱為隱式集合語法。  
  
 除根項目外，作為另一個元素的子項目嵌套的 XAML 檔中的每個物件元素實際上是一個元素，它是以下一種情況之一或兩種情況：其父元素的隱式集合屬性的成員或指定父元素的 XAML 內容屬性的值的元素（XAML 內容屬性將在下一節中討論）。 換句話說，標記頁中的父元素和子項目的關係實際上是根上的單個物件，根下方的每個物件元素要麼是提供父元素屬性值的單個實例，要麼是也是父級的集合類型屬性值的集合。 這種單根概念在 XML 中很常見，並且在載入 XAML（如<xref:System.Windows.Markup.XamlReader.Load%2A>） 的 API 行為中經常被強化。  
  
 下面的示例是顯式指定的集合的物件元素 （<xref:System.Windows.Media.GradientStopCollection>的語法。  
  
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
  
 請注意，並不總是可以顯式聲明集合。 例如，嘗試在前面顯示<xref:System.Windows.TriggerCollection><xref:System.Windows.Style.Triggers%2A>的示例中顯式聲明將失敗。 顯式聲明集合要求集合類必須支援無參數建構函式，並且<xref:System.Windows.TriggerCollection>沒有無參數建構函式。  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>XAML 內容屬性  
 XAML 內容語法是僅在指定<xref:System.Windows.Markup.ContentPropertyAttribute>作為類聲明的一部分的類上啟用的語法。 引用<xref:System.Windows.Markup.ContentPropertyAttribute>作為該類型元素（包括派生類）的內容屬性的屬性名稱。 當 XAML 處理器處理時，物件元素的打開和關閉標記之間找到的任何子項目或內部文本都將分配為該物件的 XAML 內容屬性的值。 允許為內容屬性指定顯式屬性元素，但此用法通常不顯示在 .NET 引用中的 XAML 語法部分中。 顯式/詳細技術偶爾對標記清晰度或標記樣式具有價值，但內容屬性通常旨在簡化標記，以便可以直接嵌套與父子關係且直觀相關的元素。 根據嚴格的 XAML 語言定義，元素上其他屬性的屬性元素標記不會指定為"內容";因此，根據嚴格的 XAML 語言定義，元素的屬性元素標記不會指定為"內容";它們以前在 XAML 解析器的處理順序中處理，不被視為"內容"。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML 內容屬性值必須是連續的  
 XAML 內容屬性的值必須完全放在該物件元素上的任何其他屬性元素之前或完全之後。 無論 XAML 內容屬性的值指定為字串，還是指定為一個或多個物件，都是如此。 例如，以下標記不解析：  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 這是非法的，主要是因為如果使用屬性元素語法對內容屬性顯式進行此語法，則內容屬性將設置兩次：  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 同樣非法的示例是，如果內容屬性是集合，並且子項目與屬性元素交織在一起：  
  
```xaml  
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
 為了接受多個物件元素作為內容，內容屬性的類型必須特別為集合類型。 與集合類型的屬性元素語法類似，XAML 處理器必須標識集合類型的類型。 如果元素具有 XAML 內容屬性，並且 XAML 內容屬性的類型是集合，則隱含的集合類型不需要在標記中指定為物件元素，並且不需要將 XAML 內容屬性指定為屬性元素。 因此，標記中的明顯內容模型現在可以將多個子項目指定為內容。 以下是<xref:System.Windows.Controls.Panel>派生類的內容語法。 所有<xref:System.Windows.Controls.Panel>派生類都建立 XAML 內容屬性<xref:System.Windows.Controls.Panel.Children%2A>，這需要 類型的<xref:System.Windows.Controls.UIElementCollection>值 。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 請注意，標記中既不需要<xref:System.Windows.Controls.Panel.Children%2A>屬性元素，也<xref:System.Windows.Controls.UIElementCollection>不需要 元素的元素。 這是 XAML 的設計功能，因此，在不影響屬性元素標記或集合物件的情況下，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可以更直觀地將定義 定義的 元素表示為具有直接父子項目關係的嵌套元素樹。 事實上，<xref:System.Windows.Controls.UIElementCollection>無法在標記中顯式指定為物件元素。設計。 因為它的唯一用途是作為隱式集合，<xref:System.Windows.Controls.UIElementCollection>因此不會公開公共無參數建構函式，因此不能具現化為物件元素。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>將物件中的屬性元素和物件元素與內容屬性混合  
 XAML 規範聲明 XAML 處理器可以強制用於填充物件元素中的 XAML 內容屬性的物件元素必須是連續的，並且不能混合。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器強制執行了對混合屬性元素和內容的限制。  
  
 可以將子物件元素作為物件元素中的第一個直接標記。 然後，您可以引入屬性元素。 或者，您可以指定一個或多個屬性元素，然後指定內容，然後指定更多屬性元素。 但是，一旦屬性元素遵循內容，您就不能引入任何進一步的內容，您只能添加屬性元素。  
  
 此內容/屬性元素順序要求不適用於用作內容的內部文本。 但是，保持內部文本連續仍然是一種良好的標記樣式，因為如果屬性元素與內部文本交織在一起，則很難在標記中直觀地檢測到顯著的空白。  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>XAML 命名空間  
 前面的語法示例均未指定 XAML 命名空間，而不是預設的 XAML 命名空間。 在典型的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中，預設 XAML 命名空間指定為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]命名空間。 您可以指定預設 XAML 命名空間以外的 XAML 命名空間，並且仍然使用類似的語法。 但是，在命名在預設 XAML 命名空間中無法訪問的類的任何地方，該類名稱必須前面加上映射到相應 CLR 命名空間的 XAML 命名空間的首碼。 例如，`<custom:Example/>`物件元素語法用於具現化`Example`類的實例，其中包含該類的 CLR 命名空間（可能還有包含支援類型的外部程式集資訊）以前映射到`custom`首碼。  
  
 有關 XAML 命名空間的詳細資訊，請參閱[WPF XAML 的 XAML 命名空間和命名空間映射](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>標記延伸  
 XAML 定義了標記擴展程式設計實體，該實體允許從字串屬性值或物件元素的正常 XAML 處理器處理中轉義，並將處理延遲到備份類。 使用屬性語法時標識 XAML 處理器的標記擴展的字元是首角大括弧 （*），後跟關閉大括弧 （*） 以外的任何字元。 開頭大括弧後的第一個字串必須引用提供特定擴展行為的類，如果該子字串是真實類名稱的一部分，則引用可能會省略子字串"擴展"。 此後，可能會出現單個空格，然後每個後續字元都用作擴展實現的輸入，直到遇到關閉的大括弧。  
  
 .NET XAML 實現使用<xref:System.Windows.Markup.MarkupExtension>抽象類別作為其他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]框架或技術支援的所有標記擴展的基礎。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]專門實現的標記擴展通常旨在提供引用其他現有物件的方法，或對將在運行時計算的物件進行延遲引用。 例如，通過指定`{Binding}`標記擴展代替特定屬性通常採用的值來完成簡單的 WPF 資料繫結。 許多 WPF 標記擴展為無法進行屬性語法的屬性啟用屬性語法。 例如，<xref:System.Windows.Style>物件是一種相對複雜的類型，包含嵌套的物件和屬性系列。 WPF 中的樣式通常定義為<xref:System.Windows.ResourceDictionary>中的資源，然後通過請求資源的兩個 WPF 標記擴展之一引用。 標記擴展將屬性值的計算延遲到資源查找，並啟用在屬性語法中提供<xref:System.Windows.FrameworkElement.Style%2A>屬性的值，採用類型<xref:System.Windows.Style>，如以下示例所示：  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 此處，`StaticResource`標識提供標記<xref:System.Windows.StaticResourceExtension>擴展實現的類。 下一個`MyStyle`字串用作非預設<xref:System.Windows.StaticResourceExtension>建構函式的輸入，其中從擴充字元串獲取的參數聲明請求<xref:System.Windows.ResourceKey>的 。 `MyStyle`應為<xref:System.Windows.Style>定義為資源的[x：鍵](../../../desktop-wpf/xaml-services/xkey-directive.md)值。 [靜態資源標記擴展](staticresource-markup-extension.md)使用請求使用資源在載入時通過靜態資源查找邏輯<xref:System.Windows.Style>提供屬性值。  
  
 如需標記延伸的詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。 有關在常規 .NET XAML 實現中啟用的標記擴展和其他 XAML 程式設計功能的引用，請參閱[XAML 命名空間 （x：）語言功能](../../../desktop-wpf/xaml-services/namespace-language-features.md). 有關特定于 WPF 的標記擴展，請參閱[WPF XAML 擴展](wpf-xaml-extensions.md)。  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>附加屬性  
 附加屬性是在 XAML 中引入的程式設計概念，根據該概念，屬性可以由特定類型擁有和定義，但設置為任何元素的屬性或屬性元素。 附加屬性的主要方案是使標記結構中的子項目能夠將資訊報告給父元素，而無需跨所有元素進行廣泛共用的物件模型。 相反，父元素可以使用附加屬性向子項目報告資訊。 有關附加屬性的用途以及如何創建自己的附加屬性的詳細資訊，請參閱[附加屬性概述](attached-properties-overview.md)。  
  
 附加屬性使用表面上類似于屬性元素語法的語法，因為您還指定了*typeName*。*屬性名稱*組合。 有兩個重大差異：  
  
- 您可以使用*類型名稱*。*屬性名稱*組合，即使通過屬性語法設置附加屬性也是如此。 附加屬性是唯一限定屬性名稱是屬性語法中的要求。  
  
- 還可以對附加屬性使用屬性元素語法。 但是，對於典型的屬性元素語法，指定的*類型Name*是包含屬性元素的物件元素。 如果引用附加屬性，則*typeName*是定義附加屬性的類，而不是包含的物件元素。  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>附加事件  
 附加事件是在 XAML 中引入的另一個程式設計概念，其中事件可以由特定類型定義，但處理常式可以附加到任何物件元素上。 在 WOF 實現中，定義附加事件的類型通常是定義服務的靜態類型，有時這些附加事件由公開服務類型的路由事件別名公開。 附加事件的處理常式通過屬性語法指定。 與附加事件一樣，附加事件的屬性語法將展開，以允許*typeName*。*事件名稱*用法，其中*類型名稱*是為附加的事件`Add`基礎結構`Remove`提供和事件處理常式訪問器的類，*事件名稱*是事件名稱。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>XAML 根項目的剖析  
 下表顯示了分解的典型 XAML 根項目，顯示了根項目的特定屬性：  
  
|||  
|-|-|  
|`<Page`|打開根項目的物件元素|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|預設 （[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]） XAML 命名空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 語言 XAML 命名空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|將標記連接到為部分類定義的任何代碼後面的任何部分類聲明|  
|`>`|根物件元素的結束。 物件尚未關閉，因為元素包含子項目|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>可選和非推薦的 XAML 用法  
 以下各節介紹 XAML 處理器在技術上支援的 XAML 用法，但會產生詳細性或其他美學問題，干擾在開發包含 XAML 源的應用程式時保持人類可讀的 XAML 檔。  
  
### <a name="optional-property-element-usages"></a>可選屬性元素用法  
 可選屬性元素用法包括顯式寫入 XAML 處理器認為隱式的元素內容屬性。 例如，當您聲明 的內容時<xref:System.Windows.Controls.Menu>，可以選擇顯式聲明 集合<xref:System.Windows.Controls.ItemsControl.Items%2A><xref:System.Windows.Controls.Menu>為`<Menu.Items>`屬性元素標記，並將每個<xref:System.Windows.Controls.MenuItem>集合放在`<Menu.Items>`中，而不是使用隱式 XAML 處理器行為，所有<xref:System.Windows.Controls.Menu>子項目的所有子項目都必須是<xref:System.Windows.Controls.MenuItem>和 放置在<xref:System.Windows.Controls.ItemsControl.Items%2A>集合中。 有時，可選用法有助於直觀地闡明標記中表示的物件結構。 或者有時顯式屬性元素使用可以避免在技術上起作用但視覺上令人困惑的標記，例如屬性值中的嵌套標記擴展。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>全類型名稱.成員名稱限定屬性  
 *類型名稱*。屬性*的 iName*表單實際上比路由事件案例更通用。 但在其他情況下，形式是多餘的，你應該避免它，如果僅僅是標記風格和可讀性的原因。 在下面的示例中，對<xref:System.Windows.Controls.Control.Background%2A>該屬性的三個引用中的每一個都完全等效：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`工作，因為 該<xref:System.Windows.Controls.Button>屬性的限定查找成功（<xref:System.Windows.Controls.Control.Background%2A>從 Control 繼承），並且<xref:System.Windows.Controls.Button>是物件元素或基類的類。 `Control.Background`工作，<xref:System.Windows.Controls.Control>因為類實際上定義<xref:System.Windows.Controls.Control.Background%2A>，是<xref:System.Windows.Controls.Control>一個<xref:System.Windows.Controls.Button>基類。  
  
 但是，以下*類型名稱*。*成員名稱*表單示例不起作用，因此顯示注釋：  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>是另一派生類，<xref:System.Windows.Controls.Control>如果您在`Label.Background`<xref:System.Windows.Controls.Label>物件元素中指定，則此用法將起作用。 但是，由於<xref:System.Windows.Controls.Label>不是 的類或基類<xref:System.Windows.Controls.Button>，因此指定的 XAML 處理器行為是作為附加`Label.Background`屬性進行處理。 `Label.Background`不是可用的附加屬性，並且此用法將失敗。  
  
### <a name="basetypenamemembername-property-elements"></a>基類型名稱.成員名稱屬性元素  
 以類似的方式與*類型名稱*。*成員名稱*表單適用于屬性語法，*基類型名稱*。*成員名稱*語法適用于屬性元素語法。 例如，以下語法有效：  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 此處，即使屬性元素包含在 中`Control.Background``Button`，屬性元素也給出為  
  
 但就像*類型名稱*。*屬性的成員名稱*表單，*基本類型名稱*。*成員名稱*在標記中是不好的樣式，您應該避免它。  
  
## <a name="see-also"></a>另請參閱

- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [XAML 命名空間 (x:) 語言功能](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [WPF XAML 擴充功能](wpf-xaml-extensions.md)
- [相依性屬性概觀](dependency-properties-overview.md)
- [TypeConverter 和 XAML](typeconverters-and-xaml.md)
- [WPF 的 XAML 和自訂類別](xaml-and-custom-classes-for-wpf.md)
