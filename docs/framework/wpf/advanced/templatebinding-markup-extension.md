---
title: TemplateBinding 標記延伸
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 1e4adc4c0b5579ca6c75324f358e70edd48273cc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372226"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding 標記延伸
將控制項樣板中的屬性值連結成為樣板化控制項上另一個屬性的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>XAML 屬性使用方式 (針對樣板或樣式中的 Setter 屬性)  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`propertyName`|在 setter 語法中設定之屬性的 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>。|  
|`sourceProperty`|存在於樣板化類型上的另一個相依性屬性，由其 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> 所指定。<br /><br /> -或-<br /><br /> 「穿插句點」的屬性名稱，由樣板化目標類型以外的不同類型所定義。 這實際上是一個 <xref:System.Windows.PropertyPath>。 請參閱[PropertyPath XAML 語法](propertypath-xaml-syntax.md)。|  
  
## <a name="remarks"></a>備註  
 A`TemplateBinding`是的最佳化的形式[繫結](binding-markup-extension.md)範本的情況下，類似於`Binding`建構`{Binding RelativeSource={RelativeSource TemplatedParent}}`。 
  `TemplateBinding` 永遠是單向繫結，即使相關的屬性是預設為雙向繫結也一樣。 相關的兩個屬性必須是相依性屬性。 為了達到樣板化父代的雙向繫結下列繫結陳述式改為使用`{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`。 
  
 [RelativeSource](relativesource-markupextension.md)是另一個標記延伸，有時候搭配使用或取而代之`TemplateBinding`才能執行相對屬性繫結，在範本內。  
  
 概念說明控制項樣板未涵蓋;如需詳細資訊，請參閱 <<c0> [ 控制項的樣式和範本](../controls/control-styles-and-templates.md)。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 
  `TemplateBinding` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.TemplateBindingExtension.Property%2A> 延伸類別的 <xref:System.Windows.TemplateBindingExtension> 值。  
  
 物件項目語法雖然可行，但由於沒有實際的應用程式，所以這裡不加說明。 `TemplateBinding` 是用來以評估後的運算式填滿 setter 內的值，而使用 `TemplateBinding` 的物件項目語法來填滿 `<Setter.Property>` 屬性項目語法則太過繁瑣。  
  
 `TemplateBinding` 也可以用於會指定 <xref:System.Windows.TemplateBindingExtension.Property%2A> 屬性 (Property) 做為 property=value 配對組的詳細屬性 (Attribute) 使用方式中。  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 詳細使用方式通常是適用於具有一個以上可設定屬性或有些屬性為選擇性屬性的標記延伸。 因為 `TemplateBinding` 只有一個必要的可設定屬性，所以這種詳細使用方式並不常見。  
  
 在  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 處理器實作中，這個標記延伸的處理由定義<xref:System.Windows.TemplateBindingExtension>類別。  
  
 `TemplateBinding` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 在 XAML 使用的所有標記延伸`{`和`}`字元在其屬性語法中，這是用 XAML 處理器會辨識為標記延伸必須處理這個屬性的慣例。 如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [樣式設定和範本化](../controls/styling-and-templating.md)
- [XAML 概觀 (WPF)](xaml-overview-wpf.md)
- [標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource 標記延伸](relativesource-markupextension.md)
- [Binding 標記延伸](binding-markup-extension.md)
