---
title: x:XData 內建 XAML 類型
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: d78c2fd63192dc499b119e5b038b92555511a695
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544800"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 內建 XAML 類型
在 XAML 生產環境中啟用 XML 資料島的放置。 `x:XData`XAML 處理器不應將內的 XML 專案視為作用中預設 xaml 命名空間或任何其他 XAML 命名空間的一部分。 `x:XData` 可以包含任何格式正確的 XML。

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`elementDataRoot`|封閉資料島的單一根項目。 對於大部分的最終取用者而言，沒有單一根的 XML 會視為無效。 特別是，如果 `x:XData` 是要做為 WPF 的 xml 資料來源，或許多其他使用 xml 來源進行資料系結的技術，則需要單一根。|
|`[elementData]`|選擇性。 表示 XML 資料的 XML。 任何數目的專案都可以包含為專案資料，而可包含在其他專案中的多個元素：但是，XML 的一般規則也適用。|

## <a name="remarks"></a>備註

物件內的 XML 元素 `x:XData` 可以重新宣告資料中包含 XMLDOM 的所有可能命名空間和前置詞。

`x:XData`.NET XAML 服務可以透過類別，以程式設計方式存取 XML 資料和內建 XAML 類型 <xref:System.Windows.Markup.XData> 。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

`x:XData`物件主要是做為的子物件 <xref:System.Windows.Data.XmlDataProvider> ，或者當做 XAML 中屬性 (的子物件， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 通常是以屬性專案語法) 表示。

資料通常應該會將資料島內的基底 XML 命名空間重新定義為新的預設 XML 命名空間， (設定為空的字串) 。 這是簡單資料島最簡單的方式，因為 <xref:System.Windows.Data.Binding.XPath%2A> 用來參考和系結至資料的運算式可以避免包含前置詞。 更複雜的資料島可能會定義資料的多個前置詞，並在根目錄上使用 XML 命名空間的特定前置詞。 在此情況下，所有 <xref:System.Windows.Data.Binding.XPath%2A> 運算式參考都應該包含適當的命名空間對應前置詞。 如需詳細資訊，請參閱資料系結 [總覽](../data/data-binding-overview.md)。

技術上來說， `x:XData` 可以當做型別的任何屬性內容使用 <xref:System.Xml.Serialization.IXmlSerializable> 。 不過， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> 這是唯一的主要執行。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.XmlDataProvider>
- [資料系結總覽](../data/data-binding-overview.md)
- [Binding 標記延伸](/dotnet/desktop/wpf/advanced/binding-markup-extension)
