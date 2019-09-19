---
title: '{}Escape 序列-標記延伸'
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
ms.openlocfilehash: b0646c62a1342eb160d1967e86ac286429013f3c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053867"
---
# <a name="-escape-sequence--markup-extension"></a>{} 逸出序列/標記延伸
提供屬性值的 XAML 逸出序列。 Escape 序列允許將屬性中的後續值視為常值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML 屬性項目用法  
  
```xaml  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*literalValue*|在 escape 序列之後的常值字串。 這個字串通常包含左或右大括弧（{或}）。|  
  
## <a name="remarks"></a>備註  
 使用 escape 序列（{}），以便在 XAML 中使用左大括弧（{）做為常值字元。  
  
 XAML 讀取器通常會使用左括弧（{）來表示標記延伸的進入點; 不過，它們會先檢查下一個字元，以判斷它是否為右大括弧（}）。 只有當兩個大括弧{}（）相鄰時，它們是否視為逸出序列。  
  
 如果遇到 escape 序列，XAML 讀取器應該將字串的其餘部分當做字串處理。 不過，如果將 escape 序列套用至具有類型轉換器的成員，則當 XAML 寫入器解讀該字串時，可能會經歷類型轉換。  
  
 Escape 序列不是標記延伸，而且不受類別支援。 不過，這是 XAML 讀取器（包括自訂 XAML 讀取器）應遵守的慣例。  
  
 不能以這種方式將引號（"）當做 escape 序列使用。 如果您需要將引號設定為 noncontent 屬性的屬性值，請使用屬性專案語法，並將引號放在 property 專案中做為字串，或使用 XML 字元實體。 若為 content 屬性，引號可以是整個內容。  
  
 指定必須在 XAML{}標記延伸可能出現之位置中包含命名空間限定詞的 XML 類型時，通常需要使用 escape 序列（）。 這包括 XAML 屬性值的開頭，以及在標記延伸中，緊接在等號（=）之後。 下列範例顯示在 XAML 屬性值開頭出現之 XML 命名空間的逸出序列。  
  
 [!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>另請參閱

- [XAML 的類型轉換子和標記延伸](type-converters-and-markup-extensions-for-xaml.md)
- [XML 字元實體和 XAML](xml-character-entities-and-xaml.md)
