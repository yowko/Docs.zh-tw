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
ms.openlocfilehash: b00218623add052e135bc5815d615fe7cdf002ee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459952"
---
# <a name="xkey-directive"></a>x:Key 指示詞
唯一識別在 XAML 定義的字典中所建立和參考的元素。 將 `x:Key` 值新增至 XAML 物件專案，是在資源字典中識別資源的最常見方式，例如在 WPF <xref:System.Windows.ResourceDictionary>中。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 屬性使用方式（WPF 特定）  
  
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
|`stringKeyValue`|要當做索引鍵使用的文字字串。 文字字串必須符合[XamlName 文法](xamlname-grammar.md)。|  
|`markupExtensionUsage`|在標記延伸分隔符號 {}中，這是一種標記延伸使用方式，可提供要當做索引鍵使用的物件。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 `x:Key` 支援 XAML 資源字典概念。 XAML 做為語言並不會定義資源字典的執行，而是留給特定的 UI 架構。 若要深入瞭解如何在 WPF 中執行 XAML 資源字典，請參閱[Xaml 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
 在 XAML 2006 和 WPF 中，必須以屬性的形式提供 `x:Key`。 您仍然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能在屬性格式中提供非字串值。 如果您使用 XAML 2009，則可以將 `x:Key` 指定為元素，以明確支援字串以外的物件類型所建立的字典，而不需要標記延伸的中繼。 請參閱本主題中的「XAML 2009」一節。 [備註] 區段的其餘部分會特別適用于 XAML 2006 的執行。  
  
 `x:Key` 的屬性值可以是在[XamlName 文法](xamlname-grammar.md)中定義的任何字串，或者可以是透過標記延伸評估的物件。 如需 WPF 的範例，請參閱「WPF 使用方式附注」。  
  
 屬於 <xref:System.Collections.IDictionary> 實作為父元素的子專案，通常必須包含在該字典中指定唯一索引鍵值的 `x:Key` 屬性。 架構可能會執行別名索引鍵屬性，以替代特定類型上的 `x:Key`;定義這類屬性的類型應該使用 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>來進行屬性化。  
  
 指定 `x:Key` 的程式碼就是用於基礎 <xref:System.Collections.IDictionary>的索引鍵。 例如，當您在程式碼中將資源新增至 WPF <xref:System.Windows.ResourceDictionary> 時，在 WPF 中針對資源的標記所套用的 `x:Key` 相當於 <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 的 `key` 參數值。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 做為 <xref:System.Collections.IDictionary> 實值之父物件的子物件（例如 WPF <xref:System.Windows.ResourceDictionary>），通常必須包含 `x:Key` 屬性，而且索引鍵值在該字典內必須是唯一的。 有兩個值得注意的例外狀況：  
  
- 某些 WPF 類型會宣告字典使用的隱含索引鍵。 例如，具有 <xref:System.Windows.Style.TargetType%2A>的 <xref:System.Windows.Style> 或具有 <xref:System.Windows.DataTemplate.DataType%2A>的 <xref:System.Windows.DataTemplate>，可以在 <xref:System.Windows.ResourceDictionary> 中，並使用隱含索引鍵。  
  
- WPF 支援合併的資源字典概念。 金鑰可以在合併的字典之間共用，而且共用金鑰行為可以使用 <xref:System.Windows.FrameworkContentElement.FindResource%2A>來存取。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
 在整體 WPF XAML 執行和應用程式模型中，XAML 標記編譯器不會檢查索引鍵的唯一性。 相反地，遺漏或非唯一的 `x:Key` 值會導致載入時間 XAML 剖析器錯誤。 不過，Visual Studio WPF 的字典處理，通常可以在設計階段中注意這類錯誤。  
  
 請注意，在顯示的語法中，<xref:System.Windows.ResourceDictionary> 物件在 WPF XAML 處理器如何產生集合以填入 <xref:System.Windows.FrameworkElement.Resources%2A> 集合中是隱含的。 <xref:System.Windows.ResourceDictionary> 通常不會明確地提供為標記中的專案，但在某些情況下，如果想要清楚明瞭（它會是在 <xref:System.Windows.FrameworkElement.Resources%2A> 屬性專案和擴展字典中的專案之間的集合物件元素）。 如需集合物件幾乎一律是標記中隱含元素的原因資訊，請參閱[XAML 語法詳細資料](../wpf/advanced/xaml-syntax-in-detail.md)。  
  
 在 WPF XAML 執行中，資源字典索引鍵的處理是由 <xref:System.Windows.ResourceKey> 抽象類別所定義。 不過，WPF XAML 處理器會根據其使用方式，為金鑰產生不同的基礎延伸模組類型。 例如，<xref:System.Windows.DataTemplate> 或任何衍生類別的索引鍵會分別處理，並產生不同的 <xref:System.Windows.DataTemplateKey> 物件。  
  
 索引鍵和名稱會在基本 XAML 定義中使用不同的指示詞和語言元素（`x:Key` 與 `x:Name`）。 在不同的情況下，索引鍵和名稱也會用於 WPF 定義和應用程式的這些概念。 如需詳細資訊，請參閱[WPF XAML 名稱範圍](../wpf/advanced/wpf-xaml-namescopes.md)。  
  
 如先前所述，索引鍵的值可以透過標記延伸提供，而且可以不是字串值。 WPF 案例的範例是 `x:Key` 的值可能是[ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)。 某些控制項會公開該類型的樣式索引鍵，以影響該控制項的部分外觀和行為，而不會完全取代該樣式。 <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>這類金鑰的範例。  
  
 WPF 合併字典功能導入了索引鍵唯一性和索引鍵查閱行為的其他考慮。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 放寬一定會在屬性格式中提供 `x:Key` 的限制。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于未編譯標記的 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 在 XAML 2009 底下，您可以透過下列用法指定 `x:Key` 元素：  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML 元素使用方式（僅限 XAML 2009）  
  
```  
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
|`keyObject`|物件的物件專案，這個專案會當做特定字典中給定 `object` 的索引鍵使用。|  
  
- 這種用法的容器/父系不會顯示在這裡。 `object` 應該是物件專案的子系，代表特定的字典執行。 `keyObject` 應該是物件實例（或實數值型別的值），適合做為該特定特製化字典執行的索引鍵。  
  
- WPF 不會執行需要此用法的字典。 物件索引鍵是 XAML 語言的一般功能，可能適用于在 XAML 中建立字典的特定自訂字典案例。 針對 WPF 功能（例如使用非字串索引鍵的資源），有其他用來建立或指定索引鍵的方法存在，因此不需要使用物件索引鍵。  
  
- *keyObject*也可以是物件元素表單中的標記延伸使用方式，而不是直接物件實例。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用注意事項  
 Silverlight 的 `x:Key` 會分別記載。 如需詳細資訊，請參閱[XAML 命名空間（x：）語言功能（Silverlight）](https://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>請參閱

- [XAML 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [資源和程式碼](../wpf/advanced/resources-and-code.md)
- [StaticResource 標記延伸](../wpf/advanced/staticresource-markup-extension.md)
