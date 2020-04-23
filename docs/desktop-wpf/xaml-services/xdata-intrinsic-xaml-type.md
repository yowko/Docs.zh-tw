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
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071539"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 內建 XAML 類型
支援在 XAML 生產中放置 XML 資料孤島。 XAML`x:XData`處理器不應將其中的 XML 元素視為代理預設 XAML 命名空間或任何其他 XAML 命名空間的一部分。 `x:XData`可以包含任意格式良好的 XML。

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
|`elementDataRoot`|封閉數據島的單根元素。 對於大多數最終消費者,沒有單個根的 XML 被視為無效。 特別是,如果`x:XData`用作 WPF 的 XML 數據源或使用 XML 源進行數據綁定的許多其他技術,則需要單個根。|
|`[elementData]`|選擇性。 表示 XML 資料的 XML。 任意數量的元素可以包含在元素數據中,嵌套元素可以包含在其他元素中;但是,XML 的一般規則適用。|

## <a name="remarks"></a>備註

`x:XData`物件中的 XML 元素可以重新聲明數據中包含 XMLDOM 的所有可能的命名空間和前綴。

在 .NET XAML`x:XData`<xref:System.Windows.Markup.XData>服務中可以通過 類對 XML 數據和內在 XAML 類型進行程式設計存取。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

該`x:XData`物件主要用<xref:System.Windows.Data.XmlDataProvider>作 的子物件,或者用作<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>屬性的 子物件(在 XAML 中,這通常用屬性元素語法表示)。

數據通常應重新定義資料孤島中的基本 XML 命名空間,作為新的預設 XML 命名空間(設置為空字串)。 對於簡單的數據孤島來說,這很容易,<xref:System.Windows.Data.Binding.XPath%2A>因為用於引用和綁定到數據的表達式可以避免包含首碼。 更複雜的數據孤島可能為數據定義多個首碼,並使用根目錄的 XML 命名空間的特定首碼。 在這種情況下,所有<xref:System.Windows.Data.Binding.XPath%2A>表達式引用都應包含適當的命名空間映射前綴。 有關詳細資訊,請參閱[資料繫結此概述](../data/data-binding-overview.md)。

從技術上講,`x:XData`可用作任何<xref:System.Xml.Serialization.IXmlSerializable>類型 屬性的內容。 然而,<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是唯一突出的實現。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.XmlDataProvider>
- [資料繫結概述](../data/data-binding-overview.md)
- [繫結標記延伸](../../framework/wpf/advanced/binding-markup-extension.md)
