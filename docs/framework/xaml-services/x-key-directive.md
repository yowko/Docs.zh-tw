---
title: x:Key 指示詞
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: 4ffd7a2922c7f3ba35ccb9ac7ce29a6a00cd99af
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837203"
---
# <a name="xkey-directive"></a>x:Key 指示詞
在 XAML 定義的字典中建立和參考的唯一識別項目。 將 `x:Key` 值加入至 XAML 物件項目是在資源字典中識別資源的常見方式，例如在 WPF <xref:System.Windows.ResourceDictionary>。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 屬性使用方式 (特定於 WPF)  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`stringKeyValue`|文字字串，使用做為索引鍵。 文字字串必須符合[XamlName 文法](xamlname-grammar.md)。|  
|`markupExtensionUsage`|在標記延伸分隔符號 {}中，這是一種標記延伸使用方式，可提供要當做索引鍵使用的物件。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 `x:Key` 支援 XAML 資源字典概念。 XAML 語言不定義資源字典實作，而是保留給特定 UI 架構。 若要深入瞭解如何在 WPF 中執行 XAML 資源字典，請參閱[Xaml 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
 在 XAML 2006 和 WPF 中，必須以屬性的形式提供 `x:Key`。 您依然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能在屬性表單中提供非字串值。 如果您使用 XAML 2009，則可以將 `x:Key` 指定為元素，以明確支援字串以外的物件類型所建立的字典，而不需要標記延伸的中繼。 請參閱本主題中的「XAML 2009」一節。 [備註] 區段的其餘部分會特別適用于 XAML 2006 的執行。  
  
 `x:Key` 的屬性值可以是在[XamlName 文法](xamlname-grammar.md)中定義的任何字串，或者可以是透過標記延伸評估的物件。 如需 WPF 的範例，請參閱＜WPF 使用方式附註＞。  
  
 本身為 <xref:System.Collections.IDictionary> 實作的父項目，其子項目通常必須包含 `x:Key` 屬性，以指定該字典內的唯一索引鍵值。 架構可能會實作別名索引鍵屬性以取代特定類型上的 `x:Key`。定義這類屬性的類型都應該以 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 屬性化。  
  
 指定 `x:Key` 的相同程式碼，也就是用於基礎 <xref:System.Collections.IDictionary> 的索引鍵。 例如，套用在 WPF 內資源之標記中的 `x:Key`，就等同於在程式碼中將資源加入至 WPF <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 時，<xref:System.Windows.ResourceDictionary> 的 `key` 參數值。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 做為父物件的子物件，如果是 <xref:System.Collections.IDictionary> 實作，像是 WPF <xref:System.Windows.ResourceDictionary>，通常必須包含 `x:Key` 屬性，而且索引鍵值在字典內必須是唯一的。 有兩個值得注意的例外狀況：  
  
- 一些 WPF 類型宣告字典使用方式的隱含索引鍵。 例如，具有 <xref:System.Windows.Style> 的 <xref:System.Windows.Style.TargetType%2A>，或是具有 <xref:System.Windows.DataTemplate> 的 <xref:System.Windows.DataTemplate.DataType%2A>，都可位在 <xref:System.Windows.ResourceDictionary> 中，並使用隱含機碼。  
  
- WPF 支援合併的資源字典概念。 索引鍵可以在合併的字典之間共用，而且可以使用 <xref:System.Windows.FrameworkContentElement.FindResource%2A> 來存取共用的索引鍵行為。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
 在整體 WPF XAML 實作和應用程式模型中，XAML 標記編譯器不會檢查索引鍵唯一性。 反之，缺少或非唯一`x:Key`值會導致載入時間 XAML 剖析器錯誤。 不過，Visual Studio WPF 的字典處理，通常可以在設計階段中注意這類錯誤。  
  
 請注意，在以下語法中，在 WPF XAML 處理器產生集合以填入 <xref:System.Windows.ResourceDictionary> 集合的過程中，<xref:System.Windows.FrameworkElement.Resources%2A> 物件是隱含的。 <xref:System.Windows.ResourceDictionary> 通常不會在標記中明確提供為項目，雖然在某些情況下，可以於必要時提供以避免困擾 (它會是 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性項目與其內部填入字典的項目之間的集合物件項目)。 如需集合物件幾乎一律是標記中隱含元素的原因資訊，請參閱[XAML 語法詳細資料](../wpf/advanced/xaml-syntax-in-detail.md)。  
  
 在 WPF XAML 的實作中，資源字典索引鍵的處理是由 <xref:System.Windows.ResourceKey> 抽象類別所定義。 不過，WPF XAML 處理器會根據索引鍵的使用方式，產生不同的基礎擴充類型。 例如，<xref:System.Windows.DataTemplate> 或任何衍生類別的索引鍵都是分開處理的，並會產生不同的 <xref:System.Windows.DataTemplateKey> 物件。  
  
 索引鍵和名稱使用基本 XAML 定義中的不同指示詞和語言項目 ( `x:Key` 與 `x:Name` 的比較)。 索引鍵和名稱也會在不同的情況下，由 WPF 定義和這些概念的應用程式所使用。 如需詳細資訊，請參閱[WPF XAML 名稱範圍](../wpf/advanced/wpf-xaml-namescopes.md)。  
  
 如先前所述，機碼的值可以透過標記延伸提供，並成為字串值以外的值。 WPF 案例的範例是 `x:Key` 的值可能是[ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)。 某些控制項會針對影響控制項之外觀及行為部分，而不取代樣式的自訂樣式資源，公開該類型的樣式索引鍵。 這類索引鍵的範例有 <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。  
  
 WPF 合併字典功能對於索引鍵唯一性和索引鍵查閱行為，引入了額外的考量。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 放寬一定會在屬性格式中提供 `x:Key` 的限制。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于未編譯標記的 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 在 XAML 2009 底下，您可以透過下列用法指定 `x:Key` 元素：  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML 項目使用方式 (僅適用於 XAML 2009)  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`keyObject`|在特殊字典中做為指定 `object` 的索引鍵之物件的物件項目。|  
  
- 這裡不會顯示這種用途的容器/父代。 `object` 必須是某個表示特製化字典實作之物件項目的子代。 `keyObject` 應該是物件執行個體 (或實值類型的值)，而且適當做為該特定特殊字典實作的索引鍵。  
  
- WPF 不會實作需要這種使用方式的字典。 物件索引鍵是更廣泛的 XAML 語言功能，可能適用於需要在 XAML 中建立字典的某些自訂字典案例。 若為 WPF 功能 (例如使用資源非字串索引鍵的隱含樣式)，會有其他建立或指定索引鍵的技術存在，因此不需使用物件索引鍵。  
  
- *keyObject*也可以是物件元素表單中的標記延伸使用方式，而不是直接物件實例。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用方式備註  
 Silverlight 的 `x:Key` 會在其他篇幅中做說明。 如需詳細資訊，請參閱[XAML 命名空間（x：）語言功能（Silverlight）](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。  
  
## <a name="see-also"></a>請參閱

- [XAML 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [資源和程式碼](../wpf/advanced/resources-and-code.md)
- [StaticResource 標記延伸](../wpf/advanced/staticresource-markup-extension.md)
