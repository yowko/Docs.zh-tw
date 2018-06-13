---
title: 擴充索引子屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: a7718a4aa85a000d0c83e8c9556a448ceaf13c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603466"
---
# <a name="extension-indexer-property-visual-basic"></a>擴充索引子屬性 (Visual Basic)
提供集合中個別項目的存取。  
  
## <a name="syntax"></a>語法  
  
```  
object(index)  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`object`|必要。 可查詢的集合。 也就是集合中實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。|  
|(|必要。 代表索引子屬性開始。|  
|`index`|必要。 整數運算式，指定集合中項目的以零為起始的位置。|  
|)|必要。 代表索引子屬性的結尾。|  
  
## <a name="return-value"></a>傳回值  
 從集合中指定位置的物件或`Nothing`如果索引超出範圍。  
  
## <a name="remarks"></a>備註  
 擴充索引子屬性可用來存取集合中的個別項目。 XML 軸屬性的輸出通常會用於這個索引子屬性。 XML 子代和 XML 子代軸屬性傳回的集合<xref:System.Xml.Linq.XElement>物件或屬性值。  
  
 Visual Basic 編譯器會將擴充功能索引子屬性轉換成呼叫`ElementAtOrDefault`方法。 不同於陣列索引子，`ElementAtOrDefault`方法會傳回`Nothing`如果索引超出範圍。 這種行為時，您無法輕鬆地判斷集合中的項目數。  
  
 這個索引子屬性就延伸模組屬性的集合，實作像是<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>： 集合沒有索引子或預設屬性時，才使用它。  
  
 若要存取之集合中的第一個元素的值<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>物件，您可以使用 XML`Value`屬性。 如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用來存取集合中的第二個的子節點的擴充索引子<xref:System.Xml.Linq.XElement>物件。 使用子軸屬性，就會取得所有子項目，名為存取集合`phone`中`contact`物件。  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>  
 [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
