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
ms.openlocfilehash: 8474fd5ee6f9f6e6dccda5fb57fbed9ddd787c26
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58046201"
---
# <a name="xkey-directive"></a>x:Key 指示詞
可唯一識別建立和參考 XAML 定義的字典中的項目。 新增`x:Key`XAML 物件元素的值是最常見的方式，來識別資源字典中，例如在 WPF 中的資源<xref:System.Windows.ResourceDictionary>。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 屬性使用方式 （特定於 WPF）  
  
```  
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
|`stringKeyValue`|文字字串做為索引鍵使用。 文字字串必須符合[XamlName 文法](xamlname-grammar.md)。|  
|`markupExtensionUsage`|標記延伸分隔符號內{}，標記延伸使用方式，提供做為索引鍵的物件。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 `x:Key` 支援 XAML 資源字典概念。 XAML 作為語言未定義的資源字典實作，保留給特定的 UI 架構。 若要深入了解如何在 WPF 中實作 XAML 資源字典，請參閱[XAML 資源](../wpf/advanced/xaml-resources.md)。  
  
 在 XAML 2006 和 WPF，`x:Key`必須提供做為屬性。 您仍然可以使用非字串索引鍵，但這需要標記延伸使用方式，才能提供以屬性形式的非字串值。 如果您使用 XAML 2009`x:Key`都可以指定為項目，以明確支援以外的其他索引的物件類型的字典字串而不需要標記延伸中繼。 請參閱本主題的 < XAML 2009 > 一節。 < 備註 > 一節的其餘部分專門適用於 XAML 2006 實作。  
  
 屬性值`x:Key`可以任何字串中定義[XamlName 文法](xamlname-grammar.md)也可以是透過標記延伸評估的物件。 如需 WPF 的範例，請參閱 < WPF 使用方式附註 >。  
  
 是父項目的子項目<xref:System.Collections.IDictionary>通常必須包含實作`x:Key`指定該字典內的唯一索引鍵值的屬性。 架構可能會實作別名索引鍵屬性，來替代`x:Key`特定類型上定義這類屬性的類型應該屬性具有<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。  
  
 指定的相同程式碼`x:Key`是用於基礎的索引鍵<xref:System.Collections.IDictionary>。 例如， `x:Key` WPF 中的資源是相當於值套用在標記中`key`參數<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>當您將資源加入 WPF<xref:System.Windows.ResourceDictionary>在程式碼中。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 也就是物件的父系的子物件<xref:System.Collections.IDictionary>實作，例如 WPF <xref:System.Windows.ResourceDictionary>，通常必須包含`x:Key`屬性，而且索引鍵值內必須是唯一的字典。 有兩個值得注意的例外狀況：  
  
-   一些 WPF 類型宣告字典使用方式的隱含索引鍵。 比方說，<xref:System.Windows.Style>具有<xref:System.Windows.Style.TargetType%2A>，或<xref:System.Windows.DataTemplate>具有<xref:System.Windows.DataTemplate.DataType%2A>，可以是<xref:System.Windows.ResourceDictionary>，並使用隱含的索引鍵。  
  
-   WPF 支援合併的資源字典概念。 金鑰可以共用之間合併的字典和可存取的共用金鑰的行為，使用<xref:System.Windows.FrameworkContentElement.FindResource%2A>。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
 在整體 WPF XAML 實作和應用程式模型中，XAML 標記編譯器不會檢查索引鍵唯一性。 相反地，缺少或非唯一`x:Key`值會導致載入時間 XAML 剖析器錯誤。 不過，Visual Studio 的字典中的處理 wpf 可以通常在設計階段注意這類錯誤。  
  
 請注意，在顯示的語法<xref:System.Windows.ResourceDictionary>物件是隱含在 WPF XAML 處理器如何產生集合以填入<xref:System.Windows.FrameworkElement.Resources%2A>集合。 A<xref:System.Windows.ResourceDictionary>通常並非明確為項目在標記中，但如果想為了清楚起見，也可以是在某些情況下 (它會是集合物件項目之間<xref:System.Windows.FrameworkElement.Resources%2A>屬性項目並在其中的項目填入字典）。 如需為什麼集合物件幾乎都是隱含的項目在標記中的資訊，請參閱[XAML 語法詳細資料](../wpf/advanced/xaml-syntax-in-detail.md)。  
  
 在 WPF XAML 實作中，資源字典索引鍵的處理由定義<xref:System.Windows.ResourceKey>抽象類別。 不過，WPF XAML 處理器會產生不同的基礎擴充類型，根據其使用方式索引鍵。 例如，索引鍵<xref:System.Windows.DataTemplate>或任何衍生的類別處理分開，而且會產生不同<xref:System.Windows.DataTemplateKey>物件。  
  
 索引鍵和名稱使用不同的指示詞和語言項目 (`x:Key`與`x:Name`) 基本 XAML 定義中。 索引鍵和名稱也會在不同的情況下由 WPF 定義和這些概念的應用程式。 如需詳細資訊，請參閱 < [WPF XAML Namescopes](../wpf/advanced/wpf-xaml-namescopes.md)。  
  
 如先前所述，機碼的值可以透過標記延伸提供，並可以是字串值以外的值。 WPF 即為一例，值`x:Key`可能[ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)。 特定控制項會公開該類型的樣式索引鍵，而不取代樣式影響組件的外觀和行為，該控制項的自訂樣式資源。 舉例來說，這類金鑰<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。  
  
 WPF 合併的字典功能導入了索引鍵唯一性和索引鍵查閱行為的其他考量。 如需詳細資訊，請參閱[合併的資源字典](../wpf/advanced/merged-resource-dictionaries.md)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 放寬了這項限制，`x:Key`一律會以屬性形式提供。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未標記編譯的 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 在 XAML 2009 中，您可以指定`x:Key`透過下列的使用方式的項目：  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML 項目使用方式 (XAML 2009)  
  
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
|`keyObject`|用做為索引鍵之物件的物件項目指定`object`特殊字典中。|  
  
-   此處未顯示這種使用容器/父代。 `object` 應該是代表特殊的字典實作之物件項目的子系。 `keyObject` 必須是物件執行個體 （或實值類型的值），而且適當做該特定特殊的字典實作的索引鍵。  
  
-   WPF 不會實作需要這種使用方式的字典。 物件索引鍵是更一般 XAML 語言，可能會需要在 XAML 中建立字典某些自訂字典案例很實用的功能。 WPF 功能，例如使用資源非字串索引鍵的隱含樣式，其他技術，建立或指定之索引鍵存在，因此不需要使用物件索引鍵。  
  
-   *keyObject*也可能是物件項目表單，而不是直接物件執行個體中的標記延伸使用方式。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用方式附註  
 `x:Key` silverlight 會另外記載。 如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>另請參閱
- [XAML 資源](../wpf/advanced/xaml-resources.md)
- [資源和程式碼](../wpf/advanced/resources-and-code.md)
- [StaticResource 標記延伸](../wpf/advanced/staticresource-markup-extension.md)
