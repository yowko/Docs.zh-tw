---
title: x:Static 標記延伸
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: fb9ee6807135f17fd9e0c799533bba28b369ebe2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072022"
---
# <a name="xstatic-markup-extension"></a>x:Static 標記延伸

引用以通用語言規範 (CLS) 相容方式定義的任何靜態按值代碼實體。 引用的靜態屬性可用於在 XAML 中提供屬性的值。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>XAML 值

| | |
|-|-|
|`prefix`|選擇性。 指映射的非預設 XAML 命名空間的前置碼。 `prefix`在用法中顯式顯示,因為很少引用來自預設 XAML 命名空間的靜態屬性。 請參閱＜備註＞。|
|`typeName`|必要。 定義所需靜態成員的類型的名稱。|
|`staticMemberName`|必要。 所需靜態值成員(常量、靜態屬性、欄位或枚舉值)的名稱。|

## <a name="remarks"></a>備註

參考的代碼實體必須是以下類型之一:

- 常量
- 靜態屬性
- 欄位
- Enlt

如果編譯了 XAML,或者 XAML 載入時間分析異常,則指定任何其他代碼實體(如非靜態屬性)會導致編譯時錯誤。

您可以`x:Static`參考目前 XAML 文件的預設 XAML 命名空間中未包含的靜態欄位或屬性;但是,這需要首碼映射。 XAML 命名空間幾乎總是在 XAML 文件的根元素上定義。

靜態屬性的尋找操作可以由 .NET XAML 服務及其 XAML 讀取器和 XAML 編寫器執行,當它們使用預設的 XAML 架構上下文運行時。 此 XAML 架構上下文可以使用 CLR 反射為物件圖形建構提供必要的靜態值。 `typeName`您指定的實際上是一個 XAML 類型名稱,而不是 CLR 類型名稱,儘管在使用預設 XAML 架構上下文或使用所有基於 CLR 的 XAML 實現框架時,這些名稱本質上是相同的名稱。

當您進行`x:Static`不是屬性值類型的引用時,應小心謹慎。 在 XAML 處理序列中,從標記擴展提供的值不會調用附加值轉換。 即使引用`x:Static`創建了文本字串,也是如此,並且通常針對該特定成員或返回類型的任何成員值對基於文本字串的屬性值進行值轉換。

屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。

技術上可能還有其他兩個 XAML 用法。 但是,這些用法不太常見,因為它們是不必要的冗長:

01. 物件元素語法。

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. 具有顯式成員屬性的屬性語法,用於初始化字串。

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

在 .NET XAML 服務實現中,此標記擴展<xref:System.Windows.Markup.StaticExtension>的處理由 類定義。

`x:Static` 是一種標記延伸。 XAML 中的所有標記擴展在其屬性語法中`{``}`使用和字元,這是 XAML 處理器識別標記擴展必須提供值的約定。 如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

用於 WPF 程式設計的預設 XAML 命名空間不包含許多有用的靜態屬性,並且大多數有用的靜態屬性都支援,例如類型轉換`{x:Static}`器,無需即可 方便使用。 對於靜態屬性,如果以下原因之一為 true,則必須映射 XAML 命名空間的前置字串:

- 您引用的類型存在於 WPF 中,但不是 WPF ( 的`http://schemas.microsoft.com/winfx/2006/xaml/presentation`預設 XAML 命名空間的一部分)。 這是使用`x:Static`的相當常見的方案。 例如,可以使用具有`x:Static`XAML 命名空間映<xref:System>射到 CLR 命名空間和 mscorlib 程式集的<xref:System.Environment>引用,以便引用類的靜態屬性。

- 您正在引用自訂程式集中的類型。

- 您引用的類型存在於 WPF 程式集中,但該類型位於未映射到 WPF 預設 XAML 命名空間的 CLR 命名空間中。 CLR 命名空間映射到 WPF 的預設 XAML 命名空間由各種 WPF 程式集中的定義執行(有關此概念的詳細資訊,請參閱[WPF XAML 的 XAML 命名空間和命名空間映射](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md))。 如果 CLR 命名空間主要由通常不用於 XAML 的類別定義組成,則存在非映射 CLR 命名空間,例如<xref:System.Windows.Threading>。

有關如何為 WPF 使用前置碼與 XAML 命名空間的詳細資訊,請參考[WPF XAML 的 XAML 命名空間與命名空間映射](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。

## <a name="see-also"></a>另請參閱

- [x:Type 標記延伸](xtype-markup-extension.md)
- [從 WPF 移轉至 System.Xaml 的類型](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
