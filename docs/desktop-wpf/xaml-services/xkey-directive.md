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
ms.openlocfilehash: 7e4e9cbded01297818f9f01df01e95e94d7dc4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548269"
---
# <a name="xkey-directive"></a>x:Key 指示詞
唯一識別在 XAML 定義字典中建立及參考的元素。 將 `x:Key` 值新增至 XAML 物件專案是在資源字典中識別資源的最常見方式，例如在 WPF 中 <xref:System.Windows.ResourceDictionary> 。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 屬性使用方式 (WPF 特定的)   
  
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
|`stringKeyValue`|要做為索引鍵使用的文字字串。 文字字串必須符合 [XamlName 文法](xamlname-grammar.md)。|  
|`markupExtensionUsage`|在標記延伸分隔符號內 {} ，標記延伸使用方式會提供要作為索引鍵使用的物件。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 `x:Key` 支援 XAML 資源字典概念。 XAML 做為語言不會定義資源字典的執行，而是留給特定的 UI 架構。 若要深入瞭解如何在 WPF 中執行 XAML 資源字典，請參閱 [Xaml 資源](../fundamentals/xaml-resources-define.md)。  
  
 在 XAML 2006 和 WPF 中， `x:Key` 必須提供為屬性。 您仍然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能在屬性表單中提供非字串值。 如果您使用 XAML 2009， `x:Key` 可以指定為專案，以明確支援字串以外的物件類型，而不需要標記延伸的中間。 請參閱本主題中的「XAML 2009」一節。 [備註] 區段的其餘部分特別適用于 XAML 2006 的執行。  
  
 的屬性值 `x:Key` 可以是 [XamlName 文法](xamlname-grammar.md) 中定義的任何字串，也可以是透過標記延伸評估的物件。 如需 WPF 的範例，請參閱「WPF 使用注意事項」。  
  
 實作為實作為父項目的子專案 <xref:System.Collections.IDictionary> 通常必須包含 `x:Key` 屬性，該屬性會指定該字典內的唯一索引鍵值。 架構可能會執行別名索引鍵屬性來替代 `x:Key` 特定類型; 定義這類屬性的類型應使用屬性 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 。  
  
 指定的程式碼對等專案 `x:Key` 是用於基礎的索引鍵 <xref:System.Collections.IDictionary> 。 例如，在 `x:Key` wpf 的資源標記中套用的會相當於 `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 當您 <xref:System.Windows.ResourceDictionary> 在程式碼中將資源新增至 WPF 時的參數值。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 父物件的子物件（ <xref:System.Collections.IDictionary> 例如 WPF <xref:System.Windows.ResourceDictionary> ）通常必須包含 `x:Key` 屬性，而且索引鍵值在該字典中必須是唯一的。 有兩個值得注意的例外狀況：  
  
- 某些 WPF 類型會宣告隱含索引鍵以供字典使用。 例如， <xref:System.Windows.Style> 具有的 <xref:System.Windows.Style.TargetType%2A> 或 <xref:System.Windows.DataTemplate> 具有的 <xref:System.Windows.DataTemplate.DataType%2A> 可在中， <xref:System.Windows.ResourceDictionary> 並使用隱含索引鍵。  
  
- WPF 支援合併的資源字典概念。 您可以在合併的字典之間共用索引鍵，而且可以使用來存取共用金鑰行為 <xref:System.Windows.FrameworkContentElement.FindResource%2A> 。 如需詳細資訊，請參閱[合併的資源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。  
  
 在整體 WPF XAML 的執行和應用程式模型中，XAML 標記編譯器不會檢查金鑰唯一性。 相反地，遺漏或非唯一的 `x:Key` 值會造成載入時間 XAML 剖析器錯誤。 不過，WPF 的字典 Visual Studio 處理通常可以在設計階段中注意這類錯誤。  
  
 請注意，在顯示的語法中， <xref:System.Windows.ResourceDictionary> 物件在 WPF XAML 處理器如何產生集合以填入集合中是隱含的 <xref:System.Windows.FrameworkElement.Resources%2A> 。 <xref:System.Windows.ResourceDictionary>通常不會明確地以標記中的元素形式提供，雖然在某些情況下，如果需要清楚起見 (它會是 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性專案與在中填入字典) 內之專案之間的 collection 物件專案。 如需集合物件在標記中幾乎一律是隱含元素的詳細資訊，請參閱 [XAML 語法詳細資料](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail)。  
  
 在 WPF XAML 的執行中，資源字典索引鍵的處理是由 <xref:System.Windows.ResourceKey> 抽象類別所定義。 不過，WPF XAML 處理器會根據其使用方式，為索引鍵產生不同的基礎延伸類型。 例如， <xref:System.Windows.DataTemplate> 或任何衍生類別的索引鍵會分開處理，並產生不同的 <xref:System.Windows.DataTemplateKey> 物件。  
  
 `x:Key`在基本 XAML 定義中，索引鍵和名稱會使用不同的指示詞和語言元素 (與 `x:Name`) 。 WPF 定義和這些概念的應用程式也會在不同的情況下使用金鑰和名稱。 如需詳細資訊，請參閱 [WPF XAML 名稱範圍](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes)。  
  
 如先前所述，您可以透過標記延伸來提供索引鍵的值，而且可以是字串值以外的值。 WPF 案例的範例是，的值 `x:Key` 可能是 [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension)。 某些控制項會公開自訂樣式資源的樣式索引鍵，該類型會影響該控制項的部分外觀和行為，而不會完全取代樣式。 這類索引鍵的範例為 <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> 。  
  
 「WPF 合併的字典」功能會介紹索引鍵唯一性和索引鍵查閱行為的其他考慮。 如需詳細資訊，請參閱[合併的資源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 放寬 `x:Key` 屬性表單中一律提供的限制。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于不是標記編譯的 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 在 XAML 2009 下，您可以 `x:Key` 透過下列使用方式指定元素：  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML 元素使用 (僅限 XAML 2009)   
  
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
|`keyObject`|物件的物件專案，用來做為特製化字典中所指定的索引鍵 `object` 。|  
  
- 這裡不會顯示這類使用的容器/父系。 `object` 必須是代表特製化字典之物件元素的子系。 `keyObject` 應該是物件實例 (或實數值型別的值，) ，適合做為該特定特製化字典的索引鍵。  
  
- WPF 不會執行需要這種用法的字典。 物件索引鍵是 XAML 語言的一般功能，對於在 XAML 中建立字典的特定自訂字典案例可能很有用。 針對使用資源之非字串索引鍵的隱含樣式等 WPF 功能，有其他用來建立或指定索引鍵的技巧，因此不需要使用物件索引鍵。  
  
- `keyObject` 也可以是物件元素表單中的標記延伸使用方式，而不是直接物件實例。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用注意事項  
 `x:Key` Silverlight 會另外記載。 如需詳細資訊，請參閱 [XAML 命名空間 (x： ) 語言功能 (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。  
  
## <a name="see-also"></a>另請參閱

- [XAML 資源](../fundamentals/xaml-resources-define.md)
- [資源和程式碼](/dotnet/desktop/wpf/advanced/resources-and-code)
- [StaticResource 標記延伸](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
