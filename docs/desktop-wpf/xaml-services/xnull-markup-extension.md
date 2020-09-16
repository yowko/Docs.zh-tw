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
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549440"
---
# <a name="xnull-markup-extension"></a>x:Null 標記延伸

指定 `null` 為 XAML 成員的值。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>備註

C # 和 c + + 中 null 參考的關鍵字是 null。 Null 參考的 Microsoft Visual Basic 關鍵字為 `Nothing` ，但 `{x:Null}` 不論您與 xaml 相關聯的程式碼後端語言為何，您一律會使用做為 xaml 用法。

`x:Null`標記延伸沒有可設定的屬性。

Null 使用量通常會與 CLR 值的 XAML 成員公開相關聯 <xref:System.Nullable%601> 。

`x:Null`標記延伸（如同所有 XAML 標記延伸）會使用大括弧 (`{,}`) ，將屬性值的處理方式，轉義為常值或事件處理常式參考。 屬性語法是最常搭配此標記延伸使用的語法。 物件元素語法 `<x:Null />` 在技術上是可行的，但很少使用，因為 `x:Null` 標記延伸沒有位置參數或結構引數。

如需標記延伸的詳細資訊，請參閱 [標記延伸和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)。

在 .NET XAML 服務中，此標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.NullExtension> 。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

請注意， `null` 不一定是參考型別相依性屬性的初始未設定值。 初始預設值可能會因每個相依性屬性而異，而且可以根據屬性專屬的中繼資料。 許多相依性屬性都不接受 `null` 作為值，因為它們的驗證回呼是透過標記或程式碼。 如需相依性屬性的詳細資訊，請參閱相依性 [屬性總覽](/dotnet/desktop/wpf/advanced/dependency-properties-overview)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
- [標記延伸和 WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
