---
title: "x:Array 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2304ba68956b705904c72e29a17bdac4536c79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xarray-markup-extension"></a>x:Array 標記延伸
提供一般支援用於在 XAML 中透過標記延伸的物件陣列。 這會對應至`x:ArrayExtension`[MS-XAML] 中的 XAML 型別。  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`typeName`|型別的名稱，您`x:Array`會包含。 `typeName`可能 （且通常） 包含 XAML 命名空間前置詞用於 XAML 的類型定義。|  
|`arrayContents`|指派給內建函式的項目內容`ArrayExtension.Items`屬性。 一般而言，這些項目都指定做為一或多個物件項目，內含`x:Array`開頭和結尾標記。 此處應該是指派給中指定的 XAML 型別指定物件`typeName`。|  
  
## <a name="remarks"></a>備註  
 `Type`適用於所有的必要的屬性`x:Array`物件項目。 A`Type`參數值不需要使用`x:Type`標記延伸，則為短期的型別名稱都是 XAML 類型，這可以指定為字串。  
  
 在.NET Framework XAML 服務實作中，輸入的 XAML 型別與 CLR 的輸出之間的關聯性<xref:System.Type>的建立的陣列會受到標記延伸的服務內容。 輸出<xref:System.Type>是<xref:System.Xaml.XamlType.UnderlyingType%2A>輸入 XAML 型別之後查閱所需之,<xref:System.Xaml.XamlType>根據 XAML 結構描述內容和<xref:System.Windows.Markup.IXamlTypeResolver>內容提供的服務。  
  
 陣列內容處理時，指派給`ArrayExtension.Items`內建屬性。 在<xref:System.Windows.Markup.ArrayExtension>實作中，這由<xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>。  
  
 在.NET Framework XAML 服務實作中，這個標記延伸的處理由定義<xref:System.Windows.Markup.ArrayExtension>類別。 <xref:System.Windows.Markup.ArrayExtension>並未密封，而且無法用於做為基礎標記延伸實作自訂的陣列類型。  
  
 `x:Array`為多個預期一般 xaml 語言擴充性。 但`x:Array`也可用於指定 XAML 需要支援 XAML 的集合做為其結構化的屬性內容特定屬性的值。 例如，您可以指定的內容<xref:System.Collections.IEnumerable>屬性`x:Array`使用量。  
  
 `x:Array` 是一種標記延伸。 如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。 `x:Array`所以部分該規則的例外狀況而不是提供替代的屬性值的處理，`x:Array`提供替代的內部文字內容的處理。 此行為可讓現有的內容模型以分組成陣列和存取具名的陣列; 稍後在程式碼後置中參考可能不支援的型別您可以呼叫<xref:System.Array>方法，以取得個別陣列項目。  
  
 在 XAML 中的所有標記延伸都使用大括號 ({、}`)`中其屬性的語法，也就是，XAML 處理器會辨識的標記延伸必須處理的屬性值的慣例。 如需標記延伸的一般詳細資訊，請參閱[類型轉換器和 XAML 的標記延伸](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
 在 XAML 2009 中`x:Array`定義為基本，而不是標記延伸的語言。 如需詳細資訊，請參閱[通用 XAML 語言基本類型的內建類型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 通常，填入物件項目`x:Array`不是項目存在於[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]XAML 命名空間，而且需要非預設 XAML 命名空間的前置詞對應。  
  
 例如，以下是簡單陣列的兩個字串，與`sys`前置詞 (以及`x`) 陣列的層級定義。  
  
 [xaml]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 自訂型別做為陣列項目，此類別也必須支援做為物件項目在 XAML 中所產生的需求。 如需詳細資訊，請參閱[XAML 和自訂類別 wpf](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)。  
  
## <a name="see-also"></a>請參閱  
 [標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [從 WPF 移轉至 System.Xaml 的類型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
