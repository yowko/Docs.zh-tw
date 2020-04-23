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
ms.openlocfilehash: f75d4e30dc41bbce995e466466c96c1a2830949b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071357"
---
# <a name="xtype-markup-extension"></a>x:Type 標記延伸

提供 CLR<xref:System.Type>物件,該物件是指定 XAML 類型的基礎類型。

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
|`prefix`|選擇性。 映射非預設 XAML 命名空間的前置碼。 通常不需要指定首碼。 請參閱＜備註＞。|
|`typeNameValue`|必要。 可解析為當前預設 XAML 命名空間的類型名稱;或指定的映射前置首(如果`prefix`提供)。|

## <a name="remarks"></a>備註

標記`x:Type`延伸具有與 C# 中的`typeof()`運算元或 Microsoft Visual `GetType` Basic 中的運算符類似的功能。

標記`x:Type`擴展為採用<xref:System.Type>類型的屬性提供從字串轉換行為。 輸入是 XAML 類型。 輸入<xref:System.Type>XAML 類型和輸出 CLR<xref:System.Type>之間的關係<xref:System.Xaml.XamlType.UnderlyingType%2A><xref:System.Xaml.XamlType>是輸出 是輸入的輸出,在<xref:System.Xaml.XamlType>根據 XAML 架構 上下文和<xref:System.Windows.Markup.IXamlTypeResolver>上下文提供的服務查找必要的結果後。

在 .NET XAML 服務中,此標記擴展<xref:System.Windows.Markup.TypeExtension>的處理由 類定義。

在特定框架實現中,某些作為<xref:System.Type>值的屬性可以直接接受類型的名稱(類型的`Name`字串值)。 但是,實現此行為是一個複雜的方案。 有關示例,請參閱後面的「WPF 使用說明」 部分。

屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Type` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 延伸類別的 <xref:System.Windows.Markup.TypeExtension> 值。 在基於 CLR 類型的 .NET XAML 服務的預設 XAML 架構上下文<xref:System.Reflection.MemberInfo.Name%2A>中,此屬性的值<xref:System.Reflection.MemberInfo.Name%2A>是所需類型的,或者包含非預設 XAML 命名空間映射的前置碼。

標記`x:Type`擴展可用於物件元素語法。 在這種情況下,需要指定<xref:System.Windows.Markup.TypeExtension.TypeName%2A>屬性的值才能正確初始化擴展。

標記`x:Type`擴展也可以用作詳細屬性;但是,此用途並不常見:`<object property="{x:Type TypeName=typeNameValue}" .../>`

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

### <a name="default-xaml-namespace-and-type-mapping"></a>預設 XAML 命名空間和類型映射

WPF 程式設計的預設 XAML 命名空間包含典型 XAML 方案所需的大多數 XAML 類型;因此,在引用 XAML 類型值時,通常可以避免前綴。 如果要從自訂程式集引用類型或 WPF 程式集中存在但來自未映射到預設 XAML 命名空間的 CLR 命名空間的類型,則可能需要映射前綴。 有關前置碼、XAML 命名空間與映射 CLR 命名空間的詳細資訊,請參考[WPF XAML 的 XAML 命名空間與命名空間映射](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。

### <a name="type-properties-that-support-typename-as-string"></a>類型屬性支援類型名稱作為字串

WPF 支援啟用指定某些<xref:System.Type>類型 屬性的值`x:Type`而無需 標記擴展用的技術。 相反,您可以將該值指定為命名類型的字串。 這方面的範例是<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType>與<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>。 不支援此行為不會透過類型轉換器或標記擴展提供。 相反,這是通過<xref:System.Windows.FrameworkElementFactory>實現的延遲行為。

銀光支持類似的約定。 事實上,Silverlight 目前不`{x:Type}`支援 其 XAML 語言支援`{x:Type}`,並且不接受 用於支援 WPF-Silverlight XAML 遷移的少數情況以外的用法。 因此,類型名稱即字串行為內置於所有 Silverlight 本機屬性計算中<xref:System.Type>,

## <a name="xaml-2009"></a>XAML 2009

XAML 2009 為泛型類型提供了其他支援,並`x:TypeArguments`修改`x:Type`了和的功能行為,並提供此支援。

- `x:TypeArguments`泛型物件實例化的關聯物件元素可以位於根以外的元素上。 有關詳細資訊,請參閱[x:Type 參數指令](xtypearguments-directive.md)的「XAML 2009」部分。

- XAML 2009 支援用於在標記中指定泛型類型約束的語法。 這可以`x:TypeArguments`通過、`x:Type`由或兩個要素組合使用。

- 處理 XAML 2009 負載時實現的 WPF XAML 也會將此功能<xref:System.Type>添加到使用 類型的某些框架屬性的隱式類型轉換行為中。

在 WPF 中,可以使用 XAML 2009 功能,但僅適用於鬆散的 XAML(未標記編譯的 XAML)。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Style>
- [設定樣式和範本](../fundamentals/styles-templates-overview.md)
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
- [標記延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
