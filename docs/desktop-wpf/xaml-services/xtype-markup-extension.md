---
title: x:Type 標記延伸
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: 00e6684f6ad1eb8d96f72f49bd5e0d211c8166c3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559066"
---
# <a name="xtype-markup-extension"></a>x:Type 標記延伸

提供 CLR <xref:System.Type> 物件，該物件為指定之 XAML 型別的基礎型別。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object property="{x:Type prefix:typeNameValue}" .../>
```

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<x:Type TypeName="prefix:typeNameValue"/>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`prefix`|選擇性。 對應非預設 XAML 命名空間的前置詞。 通常不需要指定前置詞。 請參閱＜備註＞。|
|`typeNameValue`|必要。 可解析為目前預設 XAML 命名空間的類型名稱;如果提供，則為指定的對應前置詞 `prefix` 。|

## <a name="remarks"></a>備註

`x:Type`標記延伸與 `typeof()` c # 中的運算子或 Microsoft Visual Basic 中的運算子具有類似的函數 `GetType` 。

`x:Type`標記延伸針對採用型別的屬性，提供字串轉換行為 <xref:System.Type> 。 輸入是 XAML 類型。 輸入 XAML 型別和輸出 CLR 之間的關聯性 <xref:System.Type> <xref:System.Type> <xref:System.Xaml.XamlType.UnderlyingType%2A> <xref:System.Xaml.XamlType> ，是 <xref:System.Xaml.XamlType> 根據 XAML 架構內容和內容所提供的服務，在查閱必要時，輸出是輸入的 <xref:System.Windows.Markup.IXamlTypeResolver> 。

在 .NET XAML 服務中，此標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.TypeExtension> 。

在特定的架構執行中，某些做 <xref:System.Type> 為值的屬性可以直接 (類型) 的字串值來接受型別的名稱 `Name` 。 不過，執行此行為是很複雜的案例。 如需範例，請參閱後面的「WPF 使用注意事項」一節。

屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。 在 .NET XAML 服務的預設 XAML 架構內容（以 CLR 型別為基礎）下，此屬性的值為所 <xref:System.Reflection.MemberInfo.Name%2A> 需類型的，或包含在 <xref:System.Reflection.MemberInfo.Name%2A> 非預設 XAML 命名空間對應的前置詞前面。

`x:Type`標記延伸可用於物件元素語法中。 在此情況下，必須指定屬性的值， <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 才能正確地初始化延伸模組。

`x:Type`標記延伸也可以用來做為詳細資訊屬性; 不過，這種使用方式並不常見：`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

### <a name="default-xaml-namespace-and-type-mapping"></a>預設 XAML 命名空間和類型對應

WPF 程式設計的預設 XAML 命名空間包含您一般 XAML 案例所需的大部分 XAML 類型;因此，在參考 XAML 類型值時，您通常可以避免前置詞。 如果您是從自訂群組件或存在於 WPF 元件中的類型，而不是來自未對應至預設 XAML 命名空間的 CLR 命名空間，則您可能需要對應前置詞。 如需首碼、XAML 命名空間和對應 CLR 命名空間的詳細資訊，請參閱 [WPF xaml 的 Xaml 命名空間和命名空間對應](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)。

### <a name="type-properties-that-support-typename-as-string"></a>支援 Typename as 字串的型別屬性

WPF 支援的技巧可讓您指定類型的某些屬性值， <xref:System.Type> 而不需要 `x:Type` 標記延伸使用方式。 相反地，您可以將此值指定為為該類型命名的字串。 這是和的 <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> 範例 <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType> 。 無法透過類型轉換器或標記延伸來提供此行為的支援。 相反地，這是透過執行的延遲行為 <xref:System.Windows.FrameworkElementFactory> 。

Silverlight 支援類似的慣例。 事實上，Silverlight 目前並不支援 `{x:Type}` 它的 XAML 語言支援，而且在 `{x:Type}` 某些情況下不接受使用 WPF Silverlight XAML 遷移的使用方式。 因此，typename 即字串行為內建于所有 Silverlight 原生屬性評估中，其中 <xref:System.Type> 是值。

## <a name="xaml-2009"></a>XAML 2009

XAML 2009 提供對泛型型別的其他支援，並修改和的功能行為， `x:TypeArguments` `x:Type` 以提供這項支援。

- `x:TypeArguments` 而且，泛型物件具現化的相關物件專案可以在根以外的元素上。 如需詳細資訊，請參閱 [x:TypeArguments](xtypearguments-directive.md)指示詞的 "XAML 2009" 一節。

- XAML 2009 支援在標記中指定泛型型別條件約束的語法。 這可由下列 `x:TypeArguments` `x:Type` 兩個功能的組合使用。

- 處理適用于載入的 XAML 2009 時，WPF XAML 會將這項功能新增至使用類型之特定架構屬性的隱含類型轉換行為 <xref:System.Type> 。

在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于不是標記編譯) 的鬆散 XAML (XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Style>
- [樣式設定和範本化](../fundamentals/styles-templates-overview.md)
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
- [標記延伸和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
