---
title: "x:Array Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "x:Array"
  - "xArray"
helpviewer_keywords: 
  - "x:Array [XAML Services]"
  - "XAML [XAML Services], x:Array markup extension"
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Array Markup Extension
透過標記延伸，提供針對 XAML 中物件陣列的一般支援。  這會對應至 \[MS\-XAML\] 中的 `x:ArrayExtension` XAML 型別。  
  
## XAML 物件項目用法  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`typeName`|您的 `x:Array` 將會包含之型別的名稱。  `typeName` 可能 \(而且通常是\) 包含 XAML 型別定義之 XAML 命名空間的前置詞。|  
|`arrayContents`|指派給內建 `ArrayExtension.Items` 屬性的項目內容。  通常，這些項目會指定為 `x:Array` 開頭和結尾標記內包含的一個或多個物件項目。  這裡指定的物件應該可以指派給在 `typeName` 中指定的 XAML 型別。|  
  
## 備註  
 `Type` 是所有 `x:Array` 物件項目的必要屬性。  `Type` 參數值不需要使用`x:Type`標記延伸；類型的短名稱為 XAML 類型，可以指定為字串。  
  
 在 .NET Framework XAML 服務實作中，所建立的陣列的輸入 XAML 型別和輸出 CLR <xref:System.Type> 之間的關聯性受標記延伸的服務內容影響。  在查詢以 XAML 結構描述內容為基礎的必要 <xref:System.Xaml.XamlType> 與內容提供的 <xref:System.Windows.Markup.IXamlTypeResolver> 服務之後，輸出 <xref:System.Type> 會是輸入 XAML 型別的 <xref:System.Xaml.XamlType.UnderlyingType%2A>。  
  
 當處理時，陣列內容會指派至 `ArrayExtension.Items` 內建屬性。  在 <xref:System.Windows.Markup.ArrayExtension> 實作中，這是由 <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=fullName> 表示。  
  
 在 .NET Framework XAML 服務實作中，這個標記延伸的處理是由 <xref:System.Windows.Markup.ArrayExtension> 類別定義的。  <xref:System.Windows.Markup.ArrayExtension>不是密封的，可以用來做為自訂陣列型別之標記延伸實作的基礎。  
  
 `x:Array` 的設計目的比較針對 XAML 中的一般語言擴充性。  但是 `x:Array` 也可用於指定採用 XAML 支援集合做為其結構化屬性內容之某些屬性的 XAML 值。  例如，您可以用 `x:Array` 使用方式來指定 <xref:System.Collections.IEnumerable> 屬性的內容。  
  
 `x:Array` 是一種標記延伸。  如果必須將屬性 \(Attribute\) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 \(而不是只對特定型別或屬性 \(Property\) 設定型別轉換子 \(Type Converter\)\)，則通常會實作標記延伸。  `x:Array` 可說是該規則的例外狀況，因為 `x:Array` 不會提供替代屬性値處理，而是提供內部文字內容的替代處理方式。  這種行為可讓現有內容模型可能不支援的型別分組到陣列中，並藉由存取具名陣列而得於稍後在程式碼後置 \(Code\-Behind\) 中參考。您可以呼叫 <xref:System.Array> 方法以取得個別陣列項目。  
  
 所有 XAML 標記延伸都會在其屬性 \(Attribute\) 語法中使用大括號 \({}`)`，這個慣例讓 XAML 處理器知道某個標記延伸必須處理這個屬性。  如需標記延伸通用概念的詳細資訊，請參閱[Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)。  
  
 在 XAML 2009 中，`x:Array` 定義為基本語言型別，而非標記延伸。  如需詳細資訊，請參閱 [Built\-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)。  
  
## WPF 使用注意事項  
 通常，填入 `x:Array` 的物件項目不是存在於 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML 命名空間中的項目，並需要前置詞對應至非預設的 XAML 命名空間。  
  
 舉例來說，下列簡單陣列具有兩個字串，並在陣列層級定義有 `sys` 前置字元 \(以及 `x`\)。  
  
 \[xaml\]  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 針對做為陣列元素的自訂型別，此類別也必須支援在 XAML 中執行個體化為物件項目的需求。  如需詳細資訊，請參閱 [WPF 的 XAML 和自訂類別](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)。  
  
## 請參閱  
 [標記延伸和 WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)