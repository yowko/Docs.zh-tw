---
title: x:TypeArguments 指示詞
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: 69da9329f140121b66c71d4cf2e99e9d14a1b207
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071350"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments 指示詞

將泛型的約束類型參數傳遞給泛型類型的構造函數。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`object`|XAML 類型的物件元素聲明,由CLR泛型類型支援。 如果`object`引用的 XAML 類型不是來自預設的 XAML 命名空間`object`,則需要一個前`object`綴來指示存在存在的 XAML 命名空間。|
|`typeString`|將一個或多個 XAML 類型名稱聲明為字串的字串,該字串提供 CLR 泛型類型的類型參數。 有關其他語法註釋,請參閱備註。|

## <a name="remarks"></a>備註

在大多數情況下,用作字串中的資訊項目的 XAML 型態是預`typeString`固定的 。 CLR 泛型約束的典型類型(<xref:System.Int32>例如<xref:System.String>和 ) 來自CLR基類庫。 這些庫不映射到典型的特定於框架的預設 XAML 命名空間,因此需要 XAML 用法的前置碼映射。

可以使用逗號分隔符指定多個 XAML 類型名稱。

如果泛型約束本身使用泛型類型,則嵌套約束類型參數可以由括弧 () 包含。

請注意,此`x:TypeArguments`定義特定於 .NET XAML 服務並使用 CLR 支援。 可在[\[MS-XAML\]第 5.3.11 節中](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))找到語言級別的定義。

## <a name="usage-examples"></a>使用方式範例

對於這些範例,假定聲明了以下 XAML 命名空間定義:

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>清單\<字串>

`<scg:List x:TypeArguments="sys:String" ...>`實體化具有類型參數的新<xref:System.Collections.Generic.List%601><xref:System.String>。

### <a name="dictionarystringstring"></a>字典\<字串,字串>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`實例化具有兩<xref:System.Collections.Generic.Dictionary%602><xref:System.String>個類型參數的新參數。

### <a name="queuekeyvaluepairstringstring"></a>佇列<鍵值字串\<,字串>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`實例化具有 內部<xref:System.Collections.Generic.Queue%601>約束<xref:System.String>類型<xref:System.String><xref:System.Collections.Generic.KeyValuePair%602>參數和約束的新。

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 與 WPF 通用 XAML 用法

對於用於 WPF 應用程式的 XAML 2006 用法和`x:TypeArguments`XAML,一般 對 XAML 和泛型類型用法存在以下限制:

- 只有 XAML 檔的根元素才能支援引用泛型類型的泛型 XAML 用法。

- 根元素必須映射到具有至少一個類型參數的泛型類型。 例如 <xref:System.Windows.Navigation.PageFunction%601>。 頁面函數是 WPF 中 XAML 通用使用支援的主要方案。

- 泛型的根元素 XAML 物件元素還`x:Class`必須使用 聲明部分類。 即使定義 WPF 生成操作也是如此。

- `x:TypeArguments`不能引用嵌套的泛型約束。

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 或 XAML 2006,沒有 WPF 3.0 或 WPF 3.5 依賴項

在 .NET XAML 服務中,XAML 2006 或 XAML 2009 中,放寬了與 WPF 相關的通用 XAML 使用限制。 您可以在支援類型系統和物件模型可以支援的任何位置實例化 XAML 標記中的任何位置的泛型物件元素。

如果使用 XAML 2009 而不是映射 CLR 基類型以獲取通用語言基元中的 XAML 類型,則可以[將通用 XAML 語言基元的內置類型](types-for-primitives.md)用作 中的`typeString`資訊項。 例如,您可以聲明以下內容(未顯示前置碼映射,但 x 是 XAML 2009 的 XAML 語言 XAML 命名空間):

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

在 WPF 中,當定位 .NET 框架 4 或 .NET Core 3.0(或更高版本)時,`x:TypeArguments`您可以將 XAML 2009 功能與鬆散的 XAML(未標記編譯的 XAML)一起使用,但僅限於這些功能。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。 如果需要標記編譯 XAML,則必須在[XAML 2006 和 WPF 通用 XAML 用法](#xaml-2006-and-wpf-generic-xaml-usages)部分中所述的限制下操作。 BAML 僅在 .NET 框架中受支援。

## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](xclass-directive.md)
- [x:Type 標記延伸](xtype-markup-extension.md)
- [通用 XAML 語言基本類型的內建類型](types-for-primitives.md)
- [XAML 中的泛型](generics.md)
