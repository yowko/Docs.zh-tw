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
ms.openlocfilehash: f8b05f314be84e6104f1a9c7fe2edfdf826e51da
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559444"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource 標記延伸
藉由延後該值為所定義資源的參考，為任何 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 屬性屬性提供值。 該資源的查閱行為類似于執行時間查閱。  
  
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
|`key`|要求資源的金鑰。 如果資源是在標記中建立，則此索引鍵一開始是由[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞所指派，或在呼叫 <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> （如果資源是在程式碼中建立）時，以 `key` 參數的形式提供。|  
  
## <a name="remarks"></a>備註  
 `DynamicResource` 會在初始編譯期間建立暫存運算式，因此會延遲資源查閱，直到實際需要要求的資源值才能建立物件為止。 這可能會在載入 [[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]] 頁面之後。 系統會根據從目前頁面範圍開始的所有作用中資源字典的索引鍵搜尋，找到資源值，並將其取代為來自編譯的預留位置運算式。  
  
> [!IMPORTANT]
> 就相依性屬性的優先順序而言，`DynamicResource` 運算式就相當於套用動態資源參考的位置。 如果您為先前具有 `DynamicResource` 運算式做為區域值的屬性設定本機值，`DynamicResource` 就會完全移除。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。  
  
 某些資源存取案例特別適用于 `DynamicResource`，而不是[StaticResource 標記延伸](staticresource-markup-extension.md)。 如需 `DynamicResource` 和 `StaticResource`的相對優勢和效能含意的討論，請參閱[XAML 資源](xaml-resources.md)。  
  
 指定的 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 應該對應至您頁面、應用程式、可用的控制項主題和外部資源或系統資源中某個層級的[x：Key](../../../desktop-wpf/xaml-services/xkey-directive.md)指示詞所決定的現有資源，而資源查閱會依照該順序發生。 如需靜態和動態資源之資源查閱的詳細資訊，請參閱[XAML 資源](xaml-resources.md)。  
  
 資源索引鍵可以是[XamlName 文法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中定義的任何字串。 資源索引鍵也可能是其他物件類型，例如 <xref:System.Type>。 <xref:System.Type> 鍵是控制項如何透過主題來設計樣式的基礎。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 用於查閱資源值（例如 <xref:System.Windows.FrameworkElement.FindResource%2A>）的 Api 會遵循 `DynamicResource`所使用的相同資源查閱邏輯。  
  
 參考資源的替代宣告式方法是[StaticResource 標記延伸](staticresource-markup-extension.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `DynamicResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.DynamicResourceExtension> 值。  
  
 `DynamicResource` 可以在物件專案語法中使用。 在此情況下，必須指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性的值。  
  
 `DynamicResource` 也可以用於會指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器執行中，此標記延伸模組的處理是由 <xref:System.Windows.DynamicResourceExtension> 類別所定義。  
  
 `DynamicResource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>請參閱

- [XAML 資源](xaml-resources.md)
- [資源和程式碼](resources-and-code.md)
- [x:Key 指示詞](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource 標記延伸](staticresource-markup-extension.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
