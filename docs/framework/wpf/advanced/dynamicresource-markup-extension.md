---
title: DynamicResource 標記延伸
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: c09d009a8cc90e050f6cfb1a8d2abd5c61c5b19f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource 標記延伸
提供的任何值[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]可以延遲是定義資源的參考值的屬性。 該資源的查閱行為相當於執行階段查閱。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML 屬性項目用法  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`key`|要求資源的金鑰。 此機碼一開始指派[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)如果資源在標記中，建立或提供做為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果此資源原先建立在程式碼中。|  
  
## <a name="remarks"></a>備註  
 A`DynamicResource`會建立暫存的運算式，在初始的編譯期間和直到實際需要才能建構物件，而要求的資源值，因此延遲的資源查閱。 這可能很之後[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入頁面。 資源值會根據針對從目前的頁面範圍，開始的所有作用中的資源字典的索引鍵搜尋找到並取代為來自編譯預留位置的運算式。  
  
> [!IMPORTANT]
>  相依性屬性在優先順序方面，`DynamicResource`運算式就相當於套用動態資源參考所在的位置。 如果您設定如先前所擁有的屬性為區域數值`DynamicResource`運算式做為區域數值，`DynamicResource`完全移除。 如需詳細資訊，請參閱[相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)。  
  
 特定資源的存取情況會特別適用於`DynamicResource`相[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。 請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)有關的相對優點和效能影響`DynamicResource`和`StaticResource`。  
  
 指定<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>應該對應至現有的資源取決於[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)某個層級中頁面、 應用程式、 可用的控制項佈景主題和外部資源或系統資源，而資源查閱將會發生的順序。 如需靜態和動態資源的資源查閱的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)。  
  
 資源索引鍵可能是任何字串中定義[XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)。 資源索引鍵可能也是其他物件類型，例如<xref:System.Type>。 A<xref:System.Type>索引鍵是基本的佈景主題樣式的控制項可以為何。 如需詳細資訊，請參閱[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 查閱的資源值，例如<xref:System.Windows.FrameworkElement.FindResource%2A>，請依照下列所用的相同的資源查閱邏輯`DynamicResource`。  
  
 其他的宣告式方法的參考的資源是為[StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `DynamicResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.DynamicResourceExtension> 值。  
  
 `DynamicResource` 可用於物件項目語法。 在此情況下，指定的值<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>是必要屬性。  
  
 `DynamicResource` 也可以用於會指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作所定義的這個標記延伸處理<xref:System.Windows.DynamicResourceExtension>類別。  
  
 `DynamicResource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [資源和程式碼](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [x:Key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)  
 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)  
 [標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
