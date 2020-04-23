---
title: x:ClassModifier 指示詞
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072029"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier 指示詞
在提供時`x:Class`修改 XAML 編譯行為。 具體而言,提供的不是創建具有`class``Public`訪問級別的部分(預設值),而是`x:Class``NotPublic`使用訪問級別創建所提供的部分。 此行為會影響生成的程式集中類的訪問級別。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|*不公開*|要指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的確切字串與不同<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>,具體取決於您使用的代碼背後的程式設計語言。 請參閱＜備註＞。|

## <a name="dependencies"></a>相依性

[x:類](xclass-directive.md)也必須在同一元素上提供,並且該元素必須是頁面中的根元素。 有關詳細資訊,請參閱[\[MS-XAML\]部分 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。

## <a name="remarks"></a>備註

.NET `x:ClassModifier` XAML 服務使用中的值因程式設計語言而異。 要使用的字串取決於每種語言如何實現其<xref:System.CodeDom.Compiler.CodeDomProvider>和返回的類型轉換器來定義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的含義,以及該語言是否區分大小寫。

- 對 C#,要傳遞到指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>的字串為`internal`。

- 對於 Microsoft Visual Basic .NET,要傳遞<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>要`Friend`指定的字串為 。

- 對於C++/CLI,不存在支援編譯 XAML 的目標;因此,未指定要傳遞的值。

您還可以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>`public`( 在`Public`C# 中 ,在視覺基礎中);但是,指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>不常執行,因為<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>已是默認行為。

具有等效用戶代碼訪問級別限制的其他值(如`private`C#中)與 XAML`x:ClassModifier`中不支援嵌套類引用<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>無關,因此,修改器具有相同的效果。

## <a name="security-notes"></a>安全性注意事項

中`x:ClassModifier`宣佈的訪問級別仍受特定框架及其能力的解釋。 WPF 包括載入和實例化類型的功能,`x:ClassModifier``internal`如果 透過包URI引用WPF資源引用該類。 由於這種情況,以及可能由其他框架實現的可能其他框架,不完全依賴`x:ClassModifier`來阻止所有可能的實例化嘗試。

## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](xclass-directive.md)
- [WPF 中的程式碼後置和 XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier 指示詞](xfieldmodifier-directive.md)
- [安全性 (WPF)](../../framework/wpf/security-wpf.md)
- [從 WPF 移轉至 System.Xaml 的類型](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
