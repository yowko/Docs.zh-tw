---
title: "x:Key 指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c73cf28905e1dd0f3056ab0eed953d6f05b0a7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xkey-directive"></a>x:Key 指示詞
可唯一識別所建立和定義 XAML 的字典中所參考的項目。 加入`x:Key`XAML 物件項目值是最常見的方式來識別資源字典，例如在 WPF 中的資源<xref:System.Windows.ResourceDictionary>。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 屬性使用方式 （特定 WPF）  
  
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
|`stringKeyValue`|文字字串做為索引鍵使用。 文字字串必須符合[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)。|  
|`markupExtensionUsage`|標記延伸分隔符號 {} 中的標記延伸使用方式提供要用做為索引鍵的物件。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 `x:Key`支援 XAML 資源字典的概念。 XAML 語言未定義的資源字典實作，會保留給特定的 UI 架構。 若要深入了解如何在 WPF 中實作 XAML 資源字典，請參閱[XAML 資源](../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 在 XAML 2006 和 WPF，`x:Key`必須提供做為屬性。 您仍然可以使用非索引鍵，但這需要的標記延伸使用方式，才能提供以屬性形式的非字串值。 如果您使用 XAML 2009`x:Key`都可以指定為項目，以明確地支援為索引鍵的物件類型以外的字典字串而不需要中繼標記延伸。 請參閱本主題的 < XAML 2009 > 一節。 < 備註 > 一節的其餘部分特別適用於 XAML 2006 實作。  
  
 屬性值的`x:Key`可以任何字串中定義[XamlName 文法](../../../docs/framework/xaml-services/xamlname-grammar.md)或可以是標記延伸評估的物件。 如需從 WPF 範例，請參閱 < WPF 使用量注意事項 >。  
  
 是父項目的子項目<xref:System.Collections.IDictionary>實作通常必須包含`x:Key`屬性來指定該字典內的唯一索引鍵的值。 架構可能會實作具有別名的索引鍵屬性來替代`x:Key`應該具有屬性這類屬性所定義類型，針對特定類型; <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。  
  
 程式碼相當於指定`x:Key`是用於基礎的索引鍵<xref:System.Collections.IDictionary>。 例如， `x:Key` WPF 中的資源是相等的值套用在標記中`key`參數<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>當您將資源加入至 WPF<xref:System.Windows.ResourceDictionary>程式碼中。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 也就是物件的父代的子物件<xref:System.Collections.IDictionary>實作，例如 WPF <xref:System.Windows.ResourceDictionary>，通常必須包含`x:Key`屬性及金鑰值內必須是唯一的字典。 有兩個值得注意的例外狀況：  
  
-   某些 WPF 類型宣告字典使用量隱含索引鍵。 例如，<xref:System.Windows.Style>與<xref:System.Windows.Style.TargetType%2A>，或<xref:System.Windows.DataTemplate>與<xref:System.Windows.DataTemplate.DataType%2A>，可以採用<xref:System.Windows.ResourceDictionary>並使用隱含索引鍵。  
  
-   WPF 支援合併的資源字典概念。 合併的字典，間無法共用金鑰和共用索引鍵的行為可以使用存取<xref:System.Windows.FrameworkContentElement.FindResource%2A>。 如需詳細資訊，請參閱[合併的資源字典](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。  
  
 在整體 WPF XAML 實作和應用程式模型中，XAML 標記編譯器不會檢查金鑰的唯一性。 相反地，遺漏或非唯一`x:Key`值會導致載入時間 XAML 剖析器錯誤。 不過，[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]的 WPF 通常可以在設計階段記錄這類錯誤處理的字典。  
  
 請注意，在語法中所示，<xref:System.Windows.ResourceDictionary>物件是在 WPF XAML 處理器會填入集合的產生隱含<xref:System.Windows.FrameworkElement.Resources%2A>集合。 A<xref:System.Windows.ResourceDictionary>通常並非明確做為項目在標記中，不過如果想更清楚，所以可能會在某些情況下 (將集合物件的項目之間<xref:System.Windows.FrameworkElement.Resources%2A>屬性項目和項目中，填入字典）。 如需為什麼集合物件幾乎都是在標記中的隱含項目資訊，請參閱[XAML 語法的詳細資料](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。  
  
 在 WPF XAML 實作中，所定義的資源字典索引鍵處理<xref:System.Windows.ResourceKey>抽象類別。 不過，WPF XAML 處理器會產生不同及其使用方法為基礎的金鑰為基礎的擴充功能類型。 例如，索引鍵<xref:System.Windows.DataTemplate>或任何衍生的類別會分別處理，並會產生相異<xref:System.Windows.DataTemplateKey>物件。  
  
 索引鍵和名稱使用不同的指示詞和語言項目 (`x:Key`與`x:Name`) 中的基本 XAML 定義。 索引鍵和名稱也會使用在不同情況下的 WPF 定義與這些概念的應用程式。 如需詳細資訊，請參閱[WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)。  
  
 如先前所述，索引鍵的值可以透過標記延伸來提供，而且可以以外的字串值。 WPF 即為一例，值`x:Key`可能[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md)。 某些控制項公開該類型之自訂樣式資源的影響而不會完全取代樣式的組件的外觀和行為，該控制項的樣式索引鍵。 舉例來說，這類金鑰是<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。  
  
 WPF 合併的字典功能導入了索引鍵唯一性和索引鍵查閱行為的其他考量。 如需詳細資訊，請參閱[合併的資源字典](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 會放寬這項限制，`x:Key`一定會以屬性形式提供。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未標記編譯 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 在 XAML 2009 中，您可以指定`x:Key`透過使用下列項目：  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML (XAML 2009) 的項目用法  
  
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
|`keyObject`|用做為索引鍵之物件的物件項目指定`object`特製化的字典中。|  
  
-   此處未顯示這種使用容器/父系。 `object`必須是代表特定的字典實作物件元素的子元素。 `keyObject`必須是物件執行個體 （或實值類型的值），是適當的索引鍵，該特定的特殊的字典實作。  
  
-   WPF 未實作需要這種使用方式的字典。 物件索引鍵是更一般 XAML 語言，可能是適用於特定的自訂字典的情況下在 XAML 中建立字典想要的功能。 WPF 功能，例如使用資源的非字串索引鍵的隱含樣式，其他技術在建立或指定之索引鍵存在，因此不需要使用物件的索引鍵。  
  
-   *keyObject*也可能是物件項目表單，而不是直接物件執行個體中的標記延伸使用方式。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 的使用方式附註  
 `x:Key`silverlight 被說明文件。 如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>請參閱  
 [XAML 資源](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [資源和程式碼](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [StaticResource 標記延伸](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)
