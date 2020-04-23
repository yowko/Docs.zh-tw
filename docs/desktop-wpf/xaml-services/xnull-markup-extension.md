---
title: x:Null 標記延伸
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071427"
---
# <a name="xnull-markup-extension"></a>x:Null 標記延伸

指定`null`為 XAML 成員的值。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>備註

C# 和 C++ 中空引用的關鍵字為 null。 對於 null 引用的 Microsoft `Nothing`Visual Basic 關鍵字是`{x:Null}`,但無論與 XAML 關聯的代碼後面語言如何,您始終用作 XAML 用法。

標記`x:Null`擴展沒有可設置屬性。

空用法通常與 CLR<xref:System.Nullable%601>值的 XAML 成員暴露相關聯。

標記`x:Null`延伸與所有 XAML 標籤延伸一樣,使用大括`{,}`弧 ( ) 來轉義屬性值的處理,以非文本或事件處理程式引用。 屬性語法是最常用於此標記擴展的語法。 物件元素語法`<x:Null />`在技術上是可能的,但很少使用`x:Null`, 因為標記擴展沒有位置參數或構造參數。

有關標記延伸的資訊,請參閱[標籤延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。

在 .NET XAML 服務中,此標記擴展<xref:System.Windows.Markup.NullExtension>的處理由 類定義。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

請注意,`null`不一定是引用類型依賴項屬性的初始未設置值。 初始預設值可能因依賴項屬性而異,並且可以基於特定於屬性的元數據。 許多依賴項屬性不接受`null`作為值,無論是通過標記還是代碼,因為它們的驗證回調實現。 有關相依項屬性的詳細資訊,請參閱[相依項屬性概述](../../framework/wpf/advanced/dependency-properties-overview.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
- [標記延伸和 WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
