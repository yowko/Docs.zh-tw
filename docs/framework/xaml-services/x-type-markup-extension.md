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
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459909"
---
# <a name="xtype-markup-extension"></a>x:Type 標記延伸
提供 CLR <xref:System.Type> 物件，這是指定之 XAML 類型的基礎類型。  
  
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
|`prefix`|選擇項。 對應非預設 XAML 命名空間的前置詞。 通常不需要指定前置詞。 請參閱＜備註＞。|  
|`typeNameValue`|必要項。 可解析為目前預設 XAML 命名空間的類型名稱;或者，如果提供 `prefix`，則為指定的對應前置詞。|  
  
## <a name="remarks"></a>備註  
 `x:Type` 標記延伸模組與中C#的 `typeof()` 運算子或 Microsoft Visual Basic 中的 `GetType` 運算子具有類似的功能。  
  
 `x:Type` 標記延伸模組會針對接受類型 <xref:System.Type>的屬性，提供 from 字串轉換行為。 輸入是 XAML 型別。 輸入 XAML 型別和輸出 CLR <xref:System.Type> 之間的關聯性是，在根據 XAML 架構內容和內容所提供的 <xref:System.Xaml.XamlType> 服務查閱必要的 <xref:System.Windows.Markup.IXamlTypeResolver> 之後，輸出 <xref:System.Type> 是輸入 <xref:System.Xaml.XamlType>的 <xref:System.Xaml.XamlType.UnderlyingType%2A>。  
  
 在 .NET Framework XAML 服務中，此標記延伸模組的處理是由 <xref:System.Windows.Markup.TypeExtension> 類別所定義。  
  
 在特定架構的執行中，以 <xref:System.Type> 做為值的某些屬性可以直接接受類型的名稱（類型的字串值 `Name`）。 不過，執行此行為是一種複雜的案例。 如需範例，請參閱下面的「WPF 使用注意事項」一節。  
  
 屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。 在 .NET Framework XAML 服務（根據 CLR 類型）的預設 XAML 架構內容底下，此屬性的值會是所需類型的 <xref:System.Reflection.MemberInfo.Name%2A>，或是包含該 <xref:System.Reflection.MemberInfo.Name%2A>，前面加上非預設 XAML 命名空間對應的前置詞。  
  
 `x:Type` 標記延伸模組可用於物件元素語法中。 在此情況下，必須指定 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 屬性的值，才能正確地初始化延伸模組。  
  
 `x:Type` 標記延伸也可以當做 verbose 屬性使用;不過，這種用法並不一般： `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>預設的 XAML 命名空間和類型對應  
 WPF 程式設計的預設 XAML 命名空間包含一般 XAML 案例所需的大部分 XAML 類型;因此，您通常可以在參考 XAML 類型值時避免前置詞。 如果您要從自訂群組件或存在於 WPF 元件中的類型參考，但來自未對應至預設 XAML 命名空間的 CLR 命名空間，則您可能需要對應前置詞。 如需前置詞、XAML 命名空間和對應 CLR 命名空間的詳細資訊，請參閱[WPF xaml 的 Xaml 命名空間和命名空間對應](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。  
  
### <a name="type-properties-that-support-typename-as-string"></a>類型支援 Typename as String 的屬性  
 WPF 支援的技術可讓您指定 <xref:System.Type> 類型的某些屬性值，而不需要 `x:Type` 標記延伸使用方式。 相反地，您可以將值指定為名稱為類型的字串。 <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>的範例如下。 不是透過型別轉換器或標記延伸來提供此行為的支援。 相反地，這是透過 <xref:System.Windows.FrameworkElementFactory>實作為延遲的行為。  
  
 Silverlight 支援類似的慣例。 事實上，Silverlight 目前不支援其 XAML 語言支援中的 `{x:Type}`，而且在支援 WPF-Silverlight XAML 遷移的少數情況下，並不接受 `{x:Type}` 的使用方式。 因此，typename 字串行為會內建至所有的 Silverlight 原生屬性評估，其中 <xref:System.Type> 為值。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 提供泛型型別的額外支援，並修改 `x:TypeArguments` 和 `x:Type` 的功能行為，以提供這項支援。  
  
- `x:TypeArguments` 和泛型物件具現化的相關聯物件專案，可以位於根以外的元素上。 如需詳細資訊，請參閱[x:TypeArguments](x-typearguments-directive.md)指示詞的 "XAML 2009" 區段。  
  
- XAML 2009 支援在標記中指定泛型型別條件約束的語法。 這可由 `x:TypeArguments`、`x:Type`或結合這兩個功能使用。  
  
- WPF XAML 在處理 XAML 2009 以進行載入時，也會將這項功能新增至使用類型 <xref:System.Type>之特定架構屬性的隱含類型轉換行為。  
  
 在 WPF 中，您可以使用 XAML 2009 功能，但僅適用于鬆散的 XAML （不是以標記編譯的 XAML）。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Style>
- [設定樣式和範本](../wpf/controls/styling-and-templating.md)
- [XAML 概觀 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [標記延伸和 WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
