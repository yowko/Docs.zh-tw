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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053702"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 內建 XAML 類型
在 XAML 生產環境中啟用 XML 資料島的位置。 XAML 處理器不`x:XData`應處理內的 XML 專案，如同它們屬於作用中的預設 xaml 命名空間或任何其他 XAML 命名空間的一部分。 `x:XData`可以包含任何語式正確的 XML。  
  
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
|`elementDataRoot`|括住之資料島的單一根項目。 對於大部分的最終取用者而言，沒有單一根目錄的 XML 會被視為無效。 特別是，如果`x:XData`要做為 WPF 的 xml 資料來源，或許多其他使用 xml 來源進行資料系結的技術，則需要單一根目錄。|  
|`[elementData]`|選擇性。 代表 XML 資料的 XML。 專案資料可以包含任意數目的專案，而嵌套的元素可以包含在其他元素中;不過，XML 的一般規則也適用。|  
  
## <a name="remarks"></a>備註  
 `x:XData`物件內的 XML 元素可以重新宣告資料中包含 XMLDOM 的所有可能的命名空間和前置詞。  
  
 以程式設計方式存取 XML 資料`x:XData`和內建 XAML 類型，可以<xref:System.Windows.Markup.XData>透過類別在 .NET Framework XAML 服務中進行。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 物件主要是做為的子物件<xref:System.Windows.Data.XmlDataProvider>，或做為<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>屬性的子物件（在 XAML 中，這通常是以屬性元素語法表示）。 `x:XData`  
  
 資料通常應重新定義資料島中的基底 XML 命名空間，以成為新的預設 XML 命名空間（設為空字串）。 這對於簡單的資料島而言是最<xref:System.Windows.Data.Binding.XPath%2A>簡單的，因為用來參考和系結資料的運算式可以避免包含前置詞。 較複雜的資料島可能會為資料定義多個前置詞，並在根的 XML 命名空間中使用特定的首碼。 在此情況下， <xref:System.Windows.Data.Binding.XPath%2A>所有運算式參考都應該包含適當的命名空間對應前置詞。 如需詳細資訊，請參閱 [資料繫結概觀](../wpf/data/data-binding-overview.md)。  
  
 技術上`x:XData`而言，可以當做類型<xref:System.Xml.Serialization.IXmlSerializable>之任何屬性的內容使用。 不過， <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是唯一的主要實現。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.XmlDataProvider>
- [資料繫結概觀](../wpf/data/data-binding-overview.md)
- [Binding 標記延伸](../wpf/advanced/binding-markup-extension.md)
