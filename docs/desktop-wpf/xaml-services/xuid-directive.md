---
title: x:Uid 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: b5b480016d2183268422dea861510c6a169ac27b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071336"
---
# <a name="xuid-directive"></a>x:Uid 指示詞

提供標記元素的唯一識別碼。 在許多情況下,XAML 當地語系化過程和工具都使用此唯一標識符。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Uid="identifier"... />
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`identifier`|手動建立或自動產生的字串,當使用者解釋該檔時,該字串在檔案中應是唯一的`x:Uid`。|

## <a name="remarks"></a>備註

在 [MS-XAML]`x:Uid`中,定義為指令。 有關詳細資訊,請參閱[\[MS-XAML\]部分 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。

`x:Uid`由於所述的`x:Name`XAML 當地語系化方案,並且用於本地化的標識符對的程式設計模型含義沒有依賴關係,因此與 這`x:Name`兩種情況是離散 的。 此外,`x:Name`受 XAML 名稱範圍控制;但是,`x:Uid`不受任何 XAML 語言定義的唯一性實施概念的約束。 廣義的 XAML 處理器(不屬於本地化過程的處理器)不應`x:Uid`強制實施 值的唯一性。 這種責任在概念上取決於價值觀的發起者。 對於值(如專用的`x:Uid`全球化過程或工具)的消費者來說,對單個 XAML 源中值的唯一性的期望是合理的。 典型的唯一性模型是值`x:Uid`在表示 XAML 的 XML 編碼檔中是唯一的。

對特定 XAML 架構有重大瞭解的工具可以選擇僅`x:Uid`應用於 真正的可本地化字串,而不是應用於標記中遇到文本字串值的所有情況。

框架可以通過將`x:Uid`<xref:System.Windows.Markup.UidPropertyAttribute>屬性 應用於定義類型來指定其物件模型中的特定屬性為別名。 如果框架指定特定屬性,則在同一物件上指定和`x:Uid`別名成員無效。 如果同時`x:Uid`指定了兩個成員和別名成員,則 .NET<xref:System.Xaml.XamlDuplicateMemberException>XAML 服務 API 通常會為此情況引發。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

有關 WPF 當地`x:Uid`語系化過程 和 XAML BAML 形式中的角色的詳細資訊,請參閱[WPF 的全球化](../../framework/wpf/advanced/globalization-for-wpf.md)或<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF 的全球化](../../framework/wpf/advanced/globalization-for-wpf.md)
