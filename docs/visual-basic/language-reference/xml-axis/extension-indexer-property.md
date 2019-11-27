---
title: 擴充索引子屬性
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 5f91dc8a6b1a0d82daa4891cf826c16e2716839f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352690"
---
# <a name="extension-indexer-property-visual-basic"></a>擴充索引子屬性 (Visual Basic)
提供集合中個別項目的存取。  
  
## <a name="syntax"></a>語法  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`object`|必要。 可查詢的集合。 也就是，會執行 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601>的集合。|  
|(|必要。 表示索引子屬性的開頭。|  
|`index`|必要。 指定集合專案之以零為基底之位置的整數運算式。|  
|)|必要。 表示索引子屬性的結尾。|  
  
## <a name="return-value"></a>傳回值  
 集合中指定位置的物件，如果索引超出範圍，則為 `Nothing`。  
  
## <a name="remarks"></a>備註  
 您可以使用擴充索引子屬性來存取集合中的個別元素。 此索引子屬性通常用於 XML 軸屬性的輸出。 XML 子系和 XML 子代軸屬性會傳回 <xref:System.Xml.Linq.XElement> 物件或屬性值的集合。  
  
 Visual Basic 編譯器會將擴充索引子屬性轉換為 `ElementAtOrDefault` 方法的呼叫。 與陣列索引子不同的是，如果索引超出範圍，`ElementAtOrDefault` 方法會傳回 `Nothing`。 當您無法輕鬆地判斷集合中的專案數目時，這個行為會很有用。  
  
 此索引子屬性就像是執行 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601>之集合的延伸模組屬性：只有在集合沒有索引子或預設屬性時，才會使用此屬性。  
  
 若要存取 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件集合中第一個元素的值，您可以使用 XML `Value` 屬性。 如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用延伸模組索引子來存取 <xref:System.Xml.Linq.XElement> 物件集合中的第二個子節點。 您可以使用 [子軸] 屬性來存取集合，這會取得 `contact` 物件中名為 `phone` 的所有子項目。  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 此程式碼顯示下列文字：  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
