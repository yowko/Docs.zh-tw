---
title: x:Reference 標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071378"
---
# <a name="xreference-markup-extension"></a>x:Reference 標記延伸

引用在 XAML 標籤中其他位置聲明的實例。 參考參考元素的`x:Name`。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`instancexName`|引用`x:Name`實體的值(或<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-標識屬性的值)。|

## <a name="remarks"></a>備註

`x:Reference`為元素引用概念提供 XAML 語言級別支援,該概念在 WPF 等特定框架中以其他方式實現。

## <a name="xreference-and-wpf"></a>x:參考和WPF

在 WPF 和 XAML 2006 中,元素<xref:System.Windows.Data.Binding.ElementName%2A>引用由綁定的框架 級功能解決。 對於大多數 WPF 應用程式和<xref:System.Windows.Data.Binding.ElementName%2A>方案, 仍應使用綁定。 此一般指南的例外情況可能包括存在數據上下文或其他範圍範圍注意事項,使數據綁定不切實際,並且不涉及標記編譯的情況。

`x:Reference`是在 XAML 2009 中定義的構造。 在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯 WPF 標記的 XAML。 編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 語言關鍵字和功能。
