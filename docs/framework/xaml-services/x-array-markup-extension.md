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
ms.openlocfilehash: 4f4e26eb3e5ccaf66b2173c7fc9952375c5f2a58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025401"
---
# <a name="xarray-markup-extension"></a>x:Array 標記延伸
支援一般的 XAML 中透過標記延伸的物件陣列。 這會對應至`x:ArrayExtension`[MS-XAML] 中的 XAML 型別。  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`typeName`|型別的名稱，您`x:Array`會包含。 `typeName` 可能 （而且通常是） 做為前置詞的 XAML 命名空間包含的 XAML 型別定義。|  
|`arrayContents`|指派給內建函式的項目內容`ArrayExtension.Items`屬性。 一般而言，這些項目會指定為中所包含的一或多個物件元素`x:Array`開頭和結尾標記。 物件可讓您指定這裡預期要在指定的 XAML 型別指派`typeName`。|  
  
## <a name="remarks"></a>備註  
 `Type` 為所有的必要的屬性`x:Array`物件項目。 A`Type`參數值就不需要使用`x:Type`標記延伸，短期的型別名稱是 XAML 型別，可指定為字串。  
  
 在.NET Framework XAML 服務實作中，輸入的 XAML 型別與 CLR 的輸出之間的關係<xref:System.Type>的建立的陣列會影響標記延伸的服務內容。 輸出<xref:System.Type>是<xref:System.Xaml.XamlType.UnderlyingType%2A>輸入 XAML 型別之後尋找必要,<xref:System.Xaml.XamlType>根據 XAML 結構描述內容和<xref:System.Windows.Markup.IXamlTypeResolver>內容提供的服務。  
  
 陣列內容處理時，會指派給`ArrayExtension.Items`內建屬性。 在 <xref:System.Windows.Markup.ArrayExtension>實作，這由<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>。  
  
 在.NET Framework XAML 服務實作中，這個標記延伸的處理由定義<xref:System.Windows.Markup.ArrayExtension>類別。 <xref:System.Windows.Markup.ArrayExtension> 不密封格式，而且無法用於做為基礎標記延伸實作自訂的陣列類型。  
  
 `x:Array` 是多個適用於一般 XAML 中的語言擴充性。 但`x:Array`也可用於指定 XAML 的採用，XAML 支援集合做為其結構化的屬性內容的特定屬性的值。 例如，您可以在其中指定的內容<xref:System.Collections.IEnumerable>屬性與`x:Array`使用量。  
  
 `x:Array` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 `x:Array` 有一部分是該規則的例外狀況因為而不是提供替代的屬性值的處理，`x:Array`提供替代處理其內部文字內容。 此行為可讓現有的內容模型分組為陣列，並存取具名的陣列; 稍後在程式碼後置中參考可能不支援的類型您可以呼叫<xref:System.Array>方法，以取得個別的陣列項目。  
  
 在 XAML 中的所有標記延伸都使用大括號 ({,} `)`在其屬性語法中，這是用的 XAML 處理器知道某個標記延伸必須處理的屬性值的慣例。 如需一般的標記延伸的詳細資訊，請參閱[Type Converters and Markup Extensions for XAML](type-converters-and-markup-extensions-for-xaml.md)。  
  
 在 XAML 2009`x:Array`定義為基本，而不是標記延伸的語言。 如需詳細資訊，請參閱 <<c0> [ 通用 XAML 語言基本類型的內建類型](built-in-types-for-common-xaml-language-primitives.md)。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 通常，填入的物件項目`x:Array`不存在於的項目[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]XAML 命名空間，而且需要非預設 XAML 命名空間的前置詞對應。  
  
 例如，以下是簡單陣列的兩個字串，與`sys`前置詞 (以及`x`) 定義層級的陣列。  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 對於自訂類型做為陣列項目，此類別也必須支援的需求在 XAML 中具現化為物件項目。 如需詳細資訊，請參閱 < [XAML 和自訂類別，如 WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)。  
  
## <a name="see-also"></a>另請參閱

- [標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [從 WPF 移轉至 System.Xaml 的類型](types-migrated-from-wpf-to-system-xaml.md)
