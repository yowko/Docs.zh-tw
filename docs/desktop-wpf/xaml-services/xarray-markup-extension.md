---
title: x:Array 標記延伸
ms.date: 03/30/2017
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
ms.openlocfilehash: b332c43d7f9ffe2117c9afe1ed625c3e3c869813
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072043"
---
# <a name="xarray-markup-extension"></a>x:Array 標記延伸

通過標記擴展為 XAML 中的物件數位提供常規支援。 這對應於 [MS-XAML]`x:ArrayExtension`中的 XAML 類型。

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`typeName`|將`x:Array`包含的類型的名稱。 `typeName`對於包含 XAML 類型定義的 XAML 命名空間,可能(而且通常是)預固定。|
|`arrayContents`|分配給內部`ArrayExtension.Items`屬性的項內容。 通常,這些專案被指定為`x:Array`打開和關閉標記中包含的一個或多個物件元素。 此處指定的物件應可分配給`typeName`中指定的 XAML 類型。|

## <a name="remarks"></a>備註

`Type`是所有`x:Array`物件元素的必需屬性。 參數`Type`值不需要`x:Type`使用 標記擴展,因此參數值不需要使用標記擴展。類型的短名稱是 XAML 類型,可以指定為字串。

在 .NET XAML 服務實現中,輸入 XAML<xref:System.Type>類型和創建陣列的輸出 CLR 之間的關係受標記擴展的服務上下文的影響。 輸出<xref:System.Type><xref:System.Xaml.XamlType.UnderlyingType%2A>是輸入 XAML 類型的輸出,在根據<xref:System.Xaml.XamlType>XAML<xref:System.Windows.Markup.IXamlTypeResolver>架構上下文和 上下文提供的服務查找所需的結果後。

處理時,數位內容將分配給`ArrayExtension.Items`內部屬性。 在實現中<xref:System.Windows.Markup.ArrayExtension>,這由<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>表示 。

在 .NET XAML 服務實現中,此標記擴展<xref:System.Windows.Markup.ArrayExtension>的處理由 類定義。 <xref:System.Windows.Markup.ArrayExtension>不密封,可用作自定義數位類型的標記擴展實現的基礎。

`x:Array`更適用於 XAML 中的一般語言擴充性。 但是`x:Array`,對於指定某些屬性的 XAML 值也很有用,這些屬性將 XAML 支援的集合作為其結構化屬性內容。 例如,可以指定具有<xref:System.Collections.IEnumerable>`x:Array`用法的屬性的內容。

`x:Array` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 `x:Array`部分是該規則的一個例外,因為不提供替代屬性值處理,`x:Array`而是提供對其內部文本內容的替代處理。 此行為允許將現有內容模型可能不支援的類型分組到陣列中,並在稍後通過訪問命名陣列在代碼後面引用;您可以呼叫<xref:System.Array>方法來取得單個陣列項目。

XAML 中的所有標記擴展都使用大括弧{,}`)`( 在其屬性語法中,這是 XAML 處理器識別標記擴展必須處理屬性值的約定)。 有關標記延伸的詳細資訊,請參考[XAML 的類型轉換器與標記延伸](type-converters-and-markup-extensions.md)。

在 XAML 2009`x:Array`中, 定義為語言基元而不是標記擴展。 有關詳細資訊,請參閱常見[XAML 語言基元的內建類型](types-for-primitives.md)。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

通常,填充的物件元素`x:Array`[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]不是 XAML 命名空間中存在的元素,需要前置碼映射到非預設 XAML 命名空間。

例如,下面是兩個字串的簡單陣列,`sys`前置字串(和`x`也) 在陣列的級別上定義。

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

對於用作陣列元素的自定義類型,類還必須支援在 XAML 中實例化為物件元素的要求。 有關詳細資訊,請參閱[WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)。

## <a name="see-also"></a>另請參閱

- [標記延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [從 WPF 移轉至 System.Xaml 的類型](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
