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
ms.openlocfilehash: 634a480b4d7446ed09708f6c91276d1c2f61d4a9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551607"
---
# <a name="xstatic-markup-extension"></a>x:Static 標記延伸

參考 Common Language Specification 中定義的任何靜態傳值程式碼實體， (符合 CLS) 規範的方式。 所參考的靜態屬性可以用來提供 XAML 中的屬性值。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object property="{x:Static prefix:typeName.staticMemberName}" .../>
```

## <a name="xaml-values"></a>XAML 值

| | |
|-|-|
|`prefix`|選擇性。 參考對應的非預設 XAML 命名空間的前置詞。 `prefix` 因為您很少參考來自預設 XAML 命名空間的靜態屬性，所以會明確顯示在使用方式中。 請參閱＜備註＞。|
|`typeName`|必要。 定義所需靜態成員的類型名稱。|
|`staticMemberName`|必要。 所需的靜態值成員名稱 (常數、靜態屬性、欄位或列舉值) 。|

## <a name="remarks"></a>備註

參考的程式碼實體必須是下列其中一項：

- 常數
- 靜態屬性
- 欄位
- 列舉值

指定任何其他程式碼實體（例如非靜態屬性）時，如果 XAML 經過標記編譯，或 XAML 載入時間剖析例外狀況，則會導致編譯時期錯誤。

您可以 `x:Static` 參考不在目前 xaml 檔之預設 xaml 命名空間中的靜態欄位或屬性; 不過，這需要前置詞對應。 XAML 命名空間幾乎一律定義在 XAML 檔的根項目上。

當使用預設的 XAML 架構內容執行時，.NET XAML 服務及其 XAML 讀取器和 XAML 寫入器可執行靜態屬性的查閱作業。 這個 XAML 架構內容可以使用 CLR 反映來提供物件圖形結構的必要靜態值。 `typeName`您指定的實際上是 xaml 型別名稱，而不是 CLR 型別名稱，但在使用預設的 XAML 架構內容或使用所有現有的 CLR 型 XAML 實架構時，這些基本上是相同的名稱。

當您建立的 `x:Static` 參考不是屬性值的型別時，請特別小心。 在 XAML 處理順序中，提供的標記延伸值不會叫用額外的值轉換。 即使您的 `x:Static` 參考會建立文字字串，且以文字字串為基礎之屬性值的值轉換通常是針對該特定成員或傳回型別的任何成員值來轉換，也是如此。

屬性 (Attribute) 語法是最常搭配這個標記延伸來使用的語法。 `x:Static` 識別項字串後所提供的字串語彙基元，是指派做為基礎 <xref:System.Windows.Markup.StaticExtension.Member%2A> 延伸類別的 <xref:System.Windows.Markup.StaticExtension> 值。

在技術上，有兩個其他的 XAML 用法。 不過，這些使用方式較不常見，因為它們是不必要的詳細資訊：

01. 物件元素語法。

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

02. 具有初始化字串之明確成員屬性的屬性語法。

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

在 .NET XAML 服務執行中，這個標記延伸的處理是由類別所定義 <xref:System.Windows.Markup.StaticExtension> 。

`x:Static` 是一種標記延伸。 XAML 中的所有標記延伸 `{` `}` 都會在其屬性語法中使用和字元，這是 xaml 處理器辨識標記延伸必須提供值的慣例。 如需標記延伸的詳細資訊，請參閱 [Markup Extensions for XAML Overview](markup-extensions-overview.md)。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

您用於 WPF 程式設計的預設 XAML 命名空間不包含許多有用的靜態屬性，而且大部分有用的靜態屬性都有支援，例如可在不需要的情況下，協助使用的類型轉換器 `{x:Static}` 。 若為靜態屬性，如果下列其中一個條件成立，您就必須對應 XAML 命名空間的前置詞：

- 您參考的類型存在於 WPF 中，但不是 WPF () 的預設 XAML 命名空間的一部分 `http://schemas.microsoft.com/winfx/2006/xaml/presentation` 。 這是相當常見的使用案例 `x:Static` 。 例如，您可以使用 `x:Static` 具有 XAML 命名空間對應的參考，以對應到 <xref:System> CLR 命名空間和 mscorlib.dll 元件，以便參考類別的靜態屬性 <xref:System.Environment> 。

- 您正在從自訂群組件參考型別。

- 您參考的類型存在於 WPF 元件中，但該類型在 CLR 命名空間中，而該命名空間未對應為 WPF 預設 XAML 命名空間的一部分。 CLR 命名空間與 WPF 的預設 XAML 命名空間的對應是由各種 WPF 元件中的定義所執行 (如需此概念的詳細資訊，請參閱 [WPF xaml 的 Xaml 命名空間和命名空間對應](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)) 。 如果該 CLR 命名空間大部分是由通常不適合 XAML 的類別定義所組成（例如），則可能會存在非對應的 CLR 命名空間 <xref:System.Windows.Threading> 。

如需如何使用 WPF 的前置詞和 XAML 命名空間的詳細資訊，請參閱 [WPF xaml 的 Xaml 命名空間和命名空間對應](/dotnet/desktop/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml)。

## <a name="see-also"></a>另請參閱

- [x:Type 標記延伸](xtype-markup-extension.md)
- [從 WPF 移轉至 System.Xaml 的類型](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
