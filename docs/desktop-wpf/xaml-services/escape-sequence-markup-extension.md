---
title: '{}逸出序列 - 標記延伸'
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
ms.openlocfilehash: f84243994557d76fa52d72b060a1ba35460e98b0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071742"
---
# <a name="-escape-sequence--markup-extension"></a>{}逸出序列/標記延伸

為屬性值提供 XAML 轉義序列。 轉義序列允許將屬性中的後續值解釋為文本。

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
|*字面值*|逸出序列的文字字串。 通常,此字串包含打開或關閉大括弧 (* 或 |)。|

## <a name="remarks"></a>備註

逸出序列{}( ) 用於讓開啟大括號 (*) 可用作 XAML 中的字面字元。

XAML 讀取器通常使用開放大括弧 (*) 來表示標記擴展的入口點;但是,他們首先檢查下一個字元以確定它是否是右大括弧 (*)。 只有當兩個大括號{}( ) 相鄰時, 它們才被視為轉義序列.

如果遇到轉義序列,XAML 讀取器應作為字串處理字串的其餘部分。 但是,如果轉義序列應用於具有類型轉換器的成員,則當 XAML 編寫器解釋該字串時,該字串可能會進行類型轉換。

轉義序列不是標記擴展,並且不由類支援。 但是,XAML 讀取器(包括自定義 XAML 讀取器)應遵守的約定。

引號 (") 不能以這種方式用作轉義序列。 如果需要將引號設置為非內容屬性的屬性值,請使用屬性元素語法並將引號作為字串放在屬性元素中,或使用 XML 字元實體。 對於內容屬性,引號可以是整個內容。

指定必須包含命名{}空間限定符的位置的 XML 類型時,經常需要轉義序列 ( ) 。 此位置包括 XAML 屬性值的開頭,以及等於符號 (*) 之後的標記擴展中。 下面的範例顯示出現在 XAML 屬性值開頭的 XML 命名空間的轉義序列。

[!code-xaml[XLINQExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]

## <a name="see-also"></a>另請參閱

- [XAML 的類型轉換子和標記延伸](type-converters-and-markup-extensions.md)
- [XML 字元實體和 XAML](xml-character-entities.md)
