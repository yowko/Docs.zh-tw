---
title: '{} 逸出序列-標記延伸'
ms.date: 03/30/2017
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
ms.openlocfilehash: 9f6743dd8a82891ac2233978550e5679130de0be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182063"
---
# <a name="-escape-sequence--markup-extension"></a>{} 逸出序列/標記延伸
提供屬性值的 XAML 逸出序列。 逸出序列可解譯為常值屬性中讓後續的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML 屬性項目用法  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*literalValue*|常值字串後面的逸出序列。 這個字串通常包含開啟或關閉括號 （{或}）。|  
  
## <a name="remarks"></a>備註  
 逸出序列 ({}) 使用，因此左大括號 （{}） 可用來當做在 XAML 中的常值字元。  
  
 XAML 讀取器通常會使用左大括號 （{}） 來代表標記延伸模組的進入點; 不過，他們第一次檢查以判斷它是否右大括號 （}） 的下一個字元。 只有當兩個括號中 ({}) 相鄰的是，您可以將它們視為逸出序列。  
  
 如果遇到逸出序列時，XAML 讀取器應該處理字串的其餘部分，做為字串。 不過，如果逸出序列套用至具有型別轉換子的成員，此字串可能進行類型轉換時由 XAML 寫入器，它會解譯。  
  
 逸出序列不是標記延伸，並不支援的類別。 不過，它是 （包括自訂的 XAML 讀取器） 的 XAML 讀取器應該採用的慣例。  
  
 引號 （"） 不能以這種方式逸出序列。 如果您需要設定為非屬性的屬性值的引號，使用屬性元素語法和屬性項目內的字串放在引號或使用 XML 字元實體。 內容屬性中，引號可以是完整的內容。  
  
 逸出序列 ({}) 時，經常必須指定 XML 型別，其中必須包含命名空間限定詞位置中的 XAML 標記延伸模組可能會出現。 這可以包括開頭的 XAML 屬性值，然後在 標記延伸，等號 （=） 的後面。 下列範例會出現在 XAML 屬性值的開頭的 XML 命名空間的逸出序列。  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>另請參閱

- [XAML 的類型轉換子和標記延伸](type-converters-and-markup-extensions-for-xaml.md)
- [XML 字元實體和 XAML](xml-character-entities-and-xaml.md)
