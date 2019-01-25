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
ms.openlocfilehash: 25a868afded83f28f5f56a9f19e050bbd32b24c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490826"
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
|`object`|必要項。 可查詢的集合。 也就是集合，實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。|  
|(|必要項。 表示索引子屬性的開頭。|  
|`index`|必要項。 整數運算式，指定集合中項目的以零為起始的位置。|  
|)|必要項。 表示索引子屬性的結尾。|  
  
## <a name="return-value"></a>傳回值  
 從指定的位置，集合中的物件或`Nothing`如果索引超出範圍。  
  
## <a name="remarks"></a>備註  
 您可以使用擴充索引子屬性來存取集合中的個別項目。 這個索引子屬性通常是 XML 軸屬性的輸出。 XML 子代和 XML 子代 axis 屬性傳回的集合<xref:System.Xml.Linq.XElement>物件或屬性值。  
  
 Visual Basic 編譯器會將呼叫中的擴充索引子屬性`ElementAtOrDefault`方法。 不同於陣列索引子`ElementAtOrDefault`方法會傳回`Nothing`如果索引超出範圍。 當您無法輕易判斷集合中的項目數，則此行為會有所幫助。  
  
 這個索引子屬性就像延伸模組屬性實作的集合<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>： 集合並沒有索引子或預設屬性時，才使用它。  
  
 若要存取的集合中的第一個元素的值<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XAttribute>物件，您可以使用 XML`Value`屬性。 如需詳細資訊，請參閱 < [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用擴充索引子來存取集合中的第二個的子節點<xref:System.Xml.Linq.XElement>物件。 集合會使用子軸屬性，它會取得所有子項目來存取`phone`在`contact`物件。  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
