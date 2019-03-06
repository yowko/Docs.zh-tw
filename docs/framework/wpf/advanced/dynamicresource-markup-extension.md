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
ms.openlocfilehash: a7b754ce3fb77314539e6391376b188fe9b15859
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369769"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource 標記延伸
提供值的任何[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]延後該值是定義資源的參考的屬性。 該資源查閱行為相當於執行階段查閱。  
  
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
|`key`|要求資源的金鑰。 此機碼一開始已由[X:key 指示詞](../../xaml-services/x-key-directive.md)如果資源在標記中，已建立，或已提供為`key`參數呼叫時<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>如果程式碼中所建立的資源。|  
  
## <a name="remarks"></a>備註  
 A`DynamicResource`會建立初始的編譯期間的暫時運算式，並因此延後資源的查閱，直到實際需要以建構物件，而要求的資源值。 這可能很之後[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入頁面。 資源值會根據對目前的頁面範圍，從開始的所有作用中的資源字典的索引鍵搜尋找到，且用來替代預留位置運算式編譯。  
  
> [!IMPORTANT]
>  相依性屬性在優先順序方面，`DynamicResource`運算式就相當於套用動態資源參考所在的位置。 如果您設定的屬性，先前的區域數值`DynamicResource`做為區域數值，運算式`DynamicResource`已完全移除。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。  
  
 某些資源的存取情況下會特別適合`DynamicResource`相對於[StaticResource 標記延伸](staticresource-markup-extension.md)。 請參閱[XAML 資源](xaml-resources.md)如需有關的效能含意與相對優點的討論`DynamicResource`和`StaticResource`。  
  
 指定<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>應該會對應至現有的資源取決於[X:key 指示詞](../../xaml-services/x-key-directive.md)在您的頁面、 應用程式、 可用的控制項主題和外部資源或系統資源，某些層級和資源查閱會依此順序。 如需靜態和動態資源的資源查閱的詳細資訊，請參閱[XAML 資源](xaml-resources.md)。  
  
 資源索引鍵可能是任何字串中定義[XamlName 文法](../../xaml-services/xamlname-grammar.md)。 資源索引鍵可能也是其他物件類型，例如<xref:System.Type>。 A<xref:System.Type>金鑰是由佈景主題樣式的控制項可以為何的基礎。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 查閱的資源值，例如<xref:System.Windows.FrameworkElement.FindResource%2A>，請依照下列所用的相同的資源查閱邏輯`DynamicResource`。  
  
 豐富的宣告式方法的參考資源是以[StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 
  `DynamicResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.DynamicResourceExtension> 值。  
  
 `DynamicResource` 可用於物件元素語法。 在此案例中，指定的值<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>屬性是必要項。  
  
 `DynamicResource` 也可以用於會指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實作中，這個標記延伸的處理由定義<xref:System.Windows.DynamicResourceExtension>類別。  
  
 `DynamicResource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱
- [XAML 資源](xaml-resources.md)
- [資源和程式碼](resources-and-code.md)
- [x:Key 指示詞](../../xaml-services/x-key-directive.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource 標記延伸](staticresource-markup-extension.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
