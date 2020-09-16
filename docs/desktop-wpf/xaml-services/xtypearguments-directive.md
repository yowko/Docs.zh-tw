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
ms.openlocfilehash: 430ab65af52282ccb1d429cd2523efe213f13609
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543547"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments 指示詞

將泛型的條件約束類型引數傳遞至泛型型別的函式。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:TypeArguments="typeString" .../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`object`|XAML 型別的物件元素宣告，由 CLR 泛型型別支援。 如果 `object` 參考不是來自預設 xaml 命名空間的 xaml 型別，則 `object` 需要前置詞來表示 xaml 命名空間（如果 `object` 有的話）。|
|`typeString`|將一或多個 XAML 型別名稱宣告為字串的字串，它會提供 CLR 泛型型別的型別引數。 如需其他語法注意事項，請參閱備註。|

## <a name="remarks"></a>備註

在大部分的情況下，當做字串中的資訊專案使用的 XAML 型別會加上前置詞 `typeString` 。 例如，CLR 泛型條件約束的一般類型 (， <xref:System.Int32> 而 <xref:System.String>) 來自 CLR 基類庫。 這些程式庫不會對應至一般架構特定的預設 XAML 命名空間，因此需要 XAML 使用的前置詞對應。

您可以使用逗號分隔符號指定一個以上的 XAML 類型名稱。

如果泛型條件約束本身使用泛型型別，則可以使用括弧 ( # A1 來包含嵌套的條件約束型別引數。

請注意，這個定義 `x:TypeArguments` 是 .NET XAML 服務和使用 CLR 支援的特定。 您可以在[ \[ 5.3.11 的 MS XAML \] 區段](/previous-versions/msp-n-p/ff650760(v=pandp.10))中找到語言層級定義。

## <a name="usage-examples"></a>使用方式範例

在這些範例中，假設已宣告下列 XAML 命名空間定義：

```xaml
xmlns:sys="clr-namespace:System;assembly=mscorlib"
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"
```

### <a name="liststring"></a>清單\<String>

`<scg:List x:TypeArguments="sys:String" ...>`<xref:System.Collections.Generic.List%601>使用型別引數具現化新的 <xref:System.String> 。

### <a name="dictionarystringstring"></a>字典\<String,String>

`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`<xref:System.Collections.Generic.Dictionary%602>以兩個型別引數具現化新的 <xref:System.String> 。

### <a name="queuekeyvaluepairstringstring"></a>佇列<KeyValuePair\<String,String>>

`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`<xref:System.Collections.Generic.Queue%601>具現化具有 <xref:System.Collections.Generic.KeyValuePair%602> 具有內部條件約束類型引數和之條件約束的新 <xref:System.String> <xref:System.String> 。

## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 和 WPF 泛型 XAML 用法

針對 WPF 應用程式使用的 XAML 2006 使用方式和 XAML，通常會對 `x:TypeArguments` xaml 和泛型型別用法有下列限制：

- 只有 XAML 檔案的根項目可以支援參考泛型型別的一般 XAML 用法。

- 根項目必須對應至具有至少一個型別引數的泛型型別。 例如 <xref:System.Windows.Navigation.PageFunction%601>。 頁面函式是 WPF 中 XAML 一般使用方式支援的主要案例。

- 泛型的根項目 XAML 物件元素也必須使用宣告部分類別 `x:Class` 。 即使定義 WPF 組建動作也是如此。

- `x:TypeArguments` 無法參考嵌套泛型條件約束。

## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 或 XAML 2006，沒有 WPF 3.0 或 WPF 3.5 的相依性

在 XAML 2006 或 XAML 2009 的 .NET XAML 服務中，會放寬對泛型 XAML 用法的 WPF 相關限制。 您可以在支援型別系統和物件模型可支援的 XAML 標記中，于任何位置具現化泛型物件元素。

如果您使用 XAML 2009，而不是對應 CLR 基底型別來取得通用語言基本類型的 XAML 型別，您可以使用 [通用 XAML 語言基本類型的內建類型](types-for-primitives.md) 作為中的資訊專案 `typeString` 。 例如，您可以宣告下列未顯示的 (前置詞對應，但 x 是 xaml 2009) 的 XAML 語言 XAML 命名空間：

```xaml
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>
```

在 WPF 中，以 .NET Framework 4 或 .NET Core 3.0 (或更新版本的) 為目標時，您可以搭配使用 XAML 2009 功能與， `x:TypeArguments` 但僅適用于不是標記編譯) 的鬆散 xaml (xaml。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。 如果您需要標記編譯 XAML，您必須依照 [xaml 2006 和 WPF 泛型 XAML 使用](#xaml-2006-and-wpf-generic-xaml-usages) 方式一節中所述的限制來操作。 只有 .NET Framework 才支援 BAML。

## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](xclass-directive.md)
- [x:Type 標記延伸](xtype-markup-extension.md)
- [通用 XAML 語言基本類型的內建類型](types-for-primitives.md)
- [XAML 中的泛型](generics.md)
