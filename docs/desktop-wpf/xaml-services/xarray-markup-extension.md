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
ms.openlocfilehash: b812939cbaa74576361de534c0d39ba45536cbcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555168"
---
# <a name="xarray-markup-extension"></a>x:Array 標記延伸

透過標記延伸，在 XAML 中提供物件陣列的一般支援。 這會對應至 `x:ArrayExtension` [MS-xaml] 中的 XAML 類型。

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<x:Array Type="typeName">
  arrayContents
</x:Array>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`typeName`|您將包含的型別名稱 `x:Array` 。 `typeName` 可能 (，且通常會) 包含 XAML 型別定義之 XAML 命名空間的前置詞。|
|`arrayContents`|指派給內部屬性的專案內容 `ArrayExtension.Items` 。 一般而言，這些專案會指定為 `x:Array` 開頭和結束記號中包含的一個或多個物件元素。 在此指定的物件應可指派給中指定的 XAML 型別 `typeName` 。|

## <a name="remarks"></a>備註

`Type` 是所有物件元素的必要屬性 `x:Array` 。 `Type`參數值不需要使用 `x:Type` 標記延伸; 類型的簡短名稱是 XAML 型別，可以指定為字串。

在 .NET XAML 服務執行中， <xref:System.Type> 標記延伸的服務內容會影響輸入 XAML 類型與所建立陣列的輸出 CLR 之間的關聯性。 <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> 根據 XAML 架構內容和內容所提供的服務，查詢所需的結果之後，輸出就是輸入 XAML 型別的 <xref:System.Windows.Markup.IXamlTypeResolver> 。

處理時，會將陣列內容指派給內建 `ArrayExtension.Items` 屬性。 在 <xref:System.Windows.Markup.ArrayExtension> 執行時，這是以表示 <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType> 。

在 .NET XAML 服務執行中，這個標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.ArrayExtension> 。 <xref:System.Windows.Markup.ArrayExtension> 不是密封的，而且可以當做自訂陣列類型的標記延伸實作為基礎使用。

`x:Array` 更適合 XAML 的一般語言擴充性。 但是 `x:Array` ，也可以用來指定特定屬性的 xaml 值，這些屬性會採用支援 xaml 的集合做為其結構化屬性內容。 例如，您可以使用使用方式來指定屬性的內容 <xref:System.Collections.IEnumerable> `x:Array` 。

`x:Array` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 `x:Array` 部分是該規則的例外狀況，因為它不會提供替代的屬性值處理，而是會 `x:Array` 提供其內部文字內容的替代處理。 此行為可讓現有的內容模型不支援的型別組成陣列，並于稍後透過存取命名陣列以在程式碼後端參考該類型;您可以呼叫 <xref:System.Array> 方法來取得個別的陣列專案。

XAML 中的所有標記延伸 {,} `)` 都會在其屬性語法中使用括弧 (，這是 xaml 處理器辨識出標記延伸必須處理屬性值的慣例。 如需標記延伸的一般詳細資訊，請參閱 [XAML 的類型轉換器和標記延伸](type-converters-and-markup-extensions.md)。

在 XAML 2009 中， `x:Array` 是定義為語言基本類型，而不是標記延伸。 如需詳細資訊，請參閱 [通用 XAML 語言基本類型的內建類型](types-for-primitives.md)。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

一般而言，填入的物件專案 `x:Array` 不是存在於 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] xaml 命名空間中的元素，而且需要非預設 XAML 命名空間的前置詞對應。

例如，以下是兩個字串的簡單陣列，其中 `sys` (前置詞，也) 在 `x` 陣列層級定義。

```xaml
<x:Array Type="sys:String"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <sys:String>Hello</sys:String>
  <sys:String>World</sys:String>
</x:Array>
```

針對當做陣列元素使用的自訂類型，類別也必須支援將 XAML 中的具現化為物件元素的需求。 如需詳細資訊，請參閱 [WPF 的 XAML 和自訂類別](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)。

## <a name="see-also"></a>另請參閱

- [標記延伸和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
- [從 WPF 移轉至 System.Xaml 的類型](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
