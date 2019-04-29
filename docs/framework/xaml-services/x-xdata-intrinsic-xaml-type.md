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
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938823"
---
# <a name="xxdata-intrinsic-xaml-type"></a>x:XData 內建 XAML 類型
可讓 XAML 生產環境內的 XML 資料島的放置。 中的 XML 項目`x:XData`應該不視為 XAML 處理器所處理預設 XAML 命名空間的一部分或任何其他的 XAML 命名空間。 `x:XData` 可以包含任意格式正確的 XML。  
  
## <a name="xaml-object-element-usage"></a>XAML 物件項目用法  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`elementDataRoot`|被封入的資料島單一根項目。 大部分的最終取用者，並沒有單一根節點的 XML 視為無效。 特別是，單一根節點如果，則需要`x:XData`適用於 WPF 或許多其他資料繫結使用 XML 來源的技術做為 XML 資料來源。|  
|`[elementData]`|選擇性。 代表 XML 資料的 XML。 項目資料可包含任意數目的項目和其他項目; 中可包含巢狀項目不過，套用 XML 的一般規則。|  
  
## <a name="remarks"></a>備註  
 中的 XML 項目`x:XData`所有可能的命名空間和前置詞的資料內包含的 XMLDOM 物件可以重新宣告。  
  
 以程式設計方式存取 XML 資料和`x:XData`透過.NET Framework XAML 服務中的內建 XAML 類型可<xref:System.Windows.Markup.XData>類別。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 `x:XData`物件主要是做為子物件<xref:System.Windows.Data.XmlDataProvider>，或者改的子物件<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>屬性 （在 XAML，這通常表示屬性項目語法中）。  
  
 資料通常應該重新定義基底資料島是新 （設為空字串） 的預設 XML 命名空間內的 XML 命名空間。 這是最簡單的簡單資料群島，因為<xref:System.Windows.Data.Binding.XPath%2A>用來參考和繫結至資料的運算式可以避免包含的前置詞。 更複雜的資料島可能會定義資料的多個前置詞，並使用 XML 命名空間根目錄的特定前置詞。 在此情況下，所有<xref:System.Windows.Data.Binding.XPath%2A>運算式參考應該包含適當的命名空間對應前置詞。 如需詳細資訊，請參閱 [資料繫結概觀](../wpf/data/data-binding-overview.md)。  
  
 技術上來說，`x:XData`可用之類型的任何屬性的內容當做<xref:System.Xml.Serialization.IXmlSerializable>。 不過，<xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType>是只提供顯著的實作。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.XmlDataProvider>
- [資料繫結概觀](../wpf/data/data-binding-overview.md)
- [Binding 標記延伸](../wpf/advanced/binding-markup-extension.md)
