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
ms.openlocfilehash: 5ccda8ba8f41a30e0ce1c832a6d3176b7fb8e8c2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646266"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource 標記延伸
通過將該值作為對[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]已定義資源的引用來為任何屬性屬性提供值。 該資源的查找行為類似於運行時查找。  
  
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
|`key`|要求資源的金鑰。 如果在標記中創建了資源,則[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)最初分配此密鑰,或者`key`<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>在調用 資源時作為參數提供, 則調用資源是在代碼中創建的。|  
  
## <a name="remarks"></a>備註  
 將在`DynamicResource`初始編譯期間創建臨時表達式,從而推遲查找資源,直到實際需要請求的資源值才能構造物件。 這可能是在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]載入頁面之後。 資源值將基於對從當前頁面作用域開始的所有活動資源字典的鍵搜索找到,並替換為編譯中的占位符運算式。  
  
> [!IMPORTANT]
> 在依賴項屬性優先順序方面,`DynamicResource`運算式等效於應用動態資源引用的位置。 如果為以前具有`DynamicResource`表示式為本地值的屬性設定局部值,則將完全刪除`DynamicResource`。 如需詳細資訊，請參閱[相依性屬性值優先順序](dependency-property-value-precedence.md)。  
  
 某些資源存取機制特別`DynamicResource`適用於 靜態[資源標記延伸](staticresource-markup-extension.md)。 有關`DynamicResource``StaticResource`和的相對優點和性能影響,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
 指定的<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>應對應於[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)在頁面、應用程式、可用控制主題和外部資源或系統資源的某些級別確定的現有資源,並且資源查找將按該順序進行。 有關有關靜態和動態資源的資源尋找的詳細資訊,請參閱[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
 資源鍵可以是[XamlName 語法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中定義的任何字串。 資源金鑰也可以是其他物件類型,如<xref:System.Type>。 鍵<xref:System.Type>是如何按主題設置控件樣式的基礎。 如需詳細資訊，請參閱[控制項撰寫概觀](../controls/control-authoring-overview.md)。  
  
 尋找資源值的 API,例如<xref:System.Windows.FrameworkElement.FindResource%2A>,遵循與使用的資源尋找邏輯相同的資源尋找邏輯`DynamicResource`。  
  
 參考資源的替代方法宣告性方法是為[靜態資源標記延伸](staticresource-markup-extension.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `DynamicResource` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 延伸類別的 <xref:System.Windows.DynamicResourceExtension> 值。  
  
 `DynamicResource`可用於物件元素語法。 在這種情況下,需要指定<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>屬性的值。  
  
 `DynamicResource` 也可以用於會指定 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `DynamicResource` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器實現中,此標記擴展的處理由<xref:System.Windows.DynamicResourceExtension>類定義。  
  
 `DynamicResource` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱

- [XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [資源和程式碼](resources-and-code.md)
- [x:Key 指示詞](../../../desktop-wpf/xaml-services/xkey-directive.md)
- [XAML 概觀 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource 標記延伸](staticresource-markup-extension.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
