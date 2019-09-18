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
ms.openlocfilehash: eb9f9cc1dfdb802e340123d0d39e9c9ebaa457f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053753"
---
# <a name="xkey-directive"></a>x:Key 指示詞
唯一識別在 XAML 定義的字典中所建立和參考的元素。 將值加入至 XAML 物件專案是在資源字典中識別資源的最常見方式，例如在 WPF <xref:System.Windows.ResourceDictionary>中。 `x:Key`  
  
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
|`markupExtensionUsage`|在標記延伸的分隔符號{}內，標記延伸使用方式會提供物件當做索引鍵使用。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 `x:Key`支援 XAML 資源字典概念。 XAML 做為語言並不會定義資源字典的執行，而是留給特定的 UI 架構。 若要深入瞭解如何在 WPF 中執行 XAML 資源字典，請參閱[Xaml 資源](../wpf/advanced/xaml-resources.md)。  
  
 在 XAML 2006 和 WPF 中`x:Key` ，必須以屬性的形式提供。 您仍然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能在屬性格式中提供非字串值。 如果您使用 XAML 2009， `x:Key`可以指定為元素，以明確支援字串以外的物件類型所建立的字典，而不需要標記延伸的中繼。 請參閱本主題中的「XAML 2009」一節。 [備註] 區段的其餘部分會特別適用于 XAML 2006 的執行。  
  
 的屬性值`x:Key`可以是[XamlName 文法](xamlname-grammar.md)中定義的任何字串，或者可以是透過標記延伸評估的物件。 如需 WPF 的範例，請參閱「WPF 使用方式附注」。  
  
 做為<xref:System.Collections.IDictionary>實作為執行之父元素的子項目，通常必須`x:Key`包含屬性，以指定該字典中的唯一索引鍵值。 架構可能會實作為`x:Key`別名索引鍵屬性，以替代特定型別，定義這類屬性的型別應該以<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>屬性化。  
  
 與指定`x:Key`相等的程式碼是用於基礎<xref:System.Collections.IDictionary>的索引鍵。 例如， <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>當您`x:Key`在程式碼中將資源新增至 wpf <xref:System.Windows.ResourceDictionary>時，在 wpf 中針對資源的`key`標記所套用的會相當於的參數值。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 做<xref:System.Collections.IDictionary>為執行之父物件的子物件（例如 WPF <xref:System.Windows.ResourceDictionary> `x:Key` ），通常必須包含屬性，而且索引鍵值在該字典內必須是唯一的。 有兩個值得注意的例外狀況：  
  
- 某些 WPF 類型會宣告字典使用的隱含索引鍵。 <xref:System.Windows.Style>例如，具有的<xref:System.Windows.Style.TargetType%2A>或<xref:System.Windows.DataTemplate>具有<xref:System.Windows.DataTemplate.DataType%2A>的可以在中<xref:System.Windows.ResourceDictionary> ，並使用隱含索引鍵。  
  
- WPF 支援合併的資源字典概念。 金鑰可以在合併的字典之間共用，而且共用金鑰行為可以使用<xref:System.Windows.FrameworkContentElement.FindResource%2A>來存取。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
 在整體 WPF XAML 執行和應用程式模型中，XAML 標記編譯器不會檢查索引鍵的唯一性。 相反地，遺漏或`x:Key`非唯一的值會導致載入時間 XAML 剖析器錯誤。 不過，Visual Studio WPF 的字典處理，通常可以在設計階段中注意這類錯誤。  
  
 請注意，在顯示的語法中<xref:System.Windows.ResourceDictionary> ，物件在 WPF XAML 處理器如何產生集合以<xref:System.Windows.FrameworkElement.Resources%2A>填入集合中是隱含的。 通常不<xref:System.Windows.FrameworkElement.Resources%2A>會明確地提供為標記中的專案，不過，如果想要清楚起見，它可能在某些情況下（在屬性專案與內填入<xref:System.Windows.ResourceDictionary>字典）。 如需集合物件幾乎一律是標記中隱含元素的原因資訊，請參閱[XAML 語法詳細資料](../wpf/advanced/xaml-syntax-in-detail.md)。  
  
 在 WPF XAML 執行中，資源字典索引鍵的處理是由<xref:System.Windows.ResourceKey>抽象類別所定義。 不過，WPF XAML 處理器會根據其使用方式，為金鑰產生不同的基礎延伸模組類型。 例如， <xref:System.Windows.DataTemplate>或任何衍生類別的索引鍵會分別處理，並產生不同<xref:System.Windows.DataTemplateKey>的物件。  
  
 索引鍵和名稱會在基本 XAML 定義中`x:Key`使用`x:Name`不同的指示詞和語言專案（與）。 在不同的情況下，索引鍵和名稱也會用於 WPF 定義和應用程式的這些概念。 如需詳細資訊，請參閱[WPF XAML 名稱範圍](../wpf/advanced/wpf-xaml-namescopes.md)。  
  
 如先前所述，索引鍵的值可以透過標記延伸提供，而且可以不是字串值。 WPF 案例的範例是，的值`x:Key`可能是[ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)。 某些控制項會公開該類型的樣式索引鍵，以影響該控制項的部分外觀和行為，而不會完全取代該樣式。 這類索引鍵的範例是<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。  
  
 WPF 合併字典功能導入了索引鍵唯一性和索引鍵查閱行為的其他考慮。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 放寬`x:Key`一律在屬性表單中提供的限制。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于未編譯標記的 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 在 XAML 2009 底下，您可以`x:Key`透過下列用法指定元素：  
  
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
|`keyObject`|物件的物件專案，這個專案會當做特定字典中指定`object`的索引鍵使用。|  
  
- 這種用法的容器/父系不會顯示在這裡。 `object`應該是物件專案的子系，代表特製化的字典執行。 `keyObject`應該是物件實例（或實數值型別的值），適合做為該特定特製化字典執行的索引鍵。  
  
- WPF 不會執行需要此用法的字典。 物件索引鍵是 XAML 語言的一般功能，可能適用于在 XAML 中建立字典的特定自訂字典案例。 針對 WPF 功能（例如使用非字串索引鍵的資源），有其他用來建立或指定索引鍵的方法存在，因此不需要使用物件索引鍵。  
  
- *keyObject*也可以是物件元素表單中的標記延伸使用方式，而不是直接物件實例。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用注意事項  
 `x:Key`針對 Silverlight, 會分別記載。 如需詳細資訊, [請參閱 XAML 命名空間 (x:)語言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>另請參閱

- [XAML 資源](../wpf/advanced/xaml-resources.md)
- [資源和程式碼](../wpf/advanced/resources-and-code.md)
- [StaticResource 標記延伸](../wpf/advanced/staticresource-markup-extension.md)
