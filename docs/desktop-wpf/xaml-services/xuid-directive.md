---
title: x:Uid 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 3de02702e6fd2be63bc2d099dad11f896b281ad1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543494"
---
# <a name="xuid-directive"></a>x:Uid 指示詞

提供標記元素的唯一識別碼。 在許多情況下，XAML 當地語系化程式和工具會使用這個唯一的識別碼。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`identifier`|當取用者解讀檔案時，手動建立或自動產生的字串應該是唯一的 `x:Uid` 。|

## <a name="remarks"></a>備註

在 [MS-XAML] 中， `x:Uid` 定義為指示詞。 如需詳細資訊，請參閱[ \[ MS-XAML \] 區段 5.3.6](/previous-versions/msp-n-p/ff650760(v=pandp.10))。

`x:Uid``x:Name`因為有所述的 XAML 當地語系化案例，所以用於當地語系化的識別碼與的程式設計模型含意沒有相依性 `x:Name` 。 此外， `x:Name` 是由 xaml 名稱範圍所控管，但 `x:Uid` 不受任何 xaml 語言所定義之唯一性強制概念的規範。 XAML 處理器如果不屬於當地語系化程式) 的 (處理器，則不需要強制唯一性 `x:Uid` 值。 這項責任在概念上是值的建立者。 在 `x:Uid` 單一 XAML 來源中，值的唯一性對於值的取用者而言是合理的，例如專用的全球化進程或工具。 一般的唯一性模型是 `x:Uid` 值在代表 XAML 的 XML 編碼檔案內是唯一的。

對於特定 XAML 架構有顯著瞭解的工具，可以選擇只套用至真正的可 `x:Uid` 當地語系化字串，而不是在標記中遇到文字字串值的所有案例中。

架構可以將 `x:Uid` 屬性套用至定義型別，以將其物件模型中的特定屬性指定為的別名 <xref:System.Windows.Markup.UidPropertyAttribute> 。 如果架構指定了特定的屬性，則在 `x:Uid` 相同物件上同時指定和別名成員是不正確。 如果同時 `x:Uid` 指定了和別名成員，則 .NET XAML 服務 API 通常會在 <xref:System.Xaml.XamlDuplicateMemberException> 此情況下擲回。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

如需 `x:Uid` wpf 當地語系化程式和 BAML 形式的 XAML 之角色的詳細資訊，請參閱 [Wpf 的全球化](/dotnet/desktop/wpf/advanced/globalization-for-wpf) 或 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF 的全球化](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
