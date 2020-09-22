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
ms.openlocfilehash: 23417cd982c2ddf06afce69d9b120ae0737fb87d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866114"
---
# <a name="extension-indexer-property-visual-basic"></a>擴充索引子屬性 (Visual Basic)

提供集合中個別項目的存取。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`object`|必要。 可查詢的集合。 也就是實作為或的 <xref:System.Collections.Generic.IEnumerable%601> 集合 <xref:System.Linq.IQueryable%601> 。|  
|(|必要。 表示索引子屬性的開頭。|  
|`index`|必要。 整數運算式，指定集合元素之以零為基底的位置。|  
|)|必要。 表示索引子屬性的結尾。|  
  
## <a name="return-value"></a>傳回值  

 集合中指定位置的物件， `Nothing` 如果索引超出範圍，則為。  
  
## <a name="remarks"></a>備註  

 您可以使用擴充索引子屬性來存取集合中的個別元素。 此索引子屬性通常用於 XML 軸屬性的輸出。 XML 子系和 XML 子代軸屬性會傳回物件的集合 <xref:System.Xml.Linq.XElement> 或屬性值。  
  
 Visual Basic 編譯器會將擴充索引子屬性轉換成方法的呼叫 `ElementAtOrDefault` 。 不同于陣列索引子， `ElementAtOrDefault` 如果索引超出範圍，則此方法會傳回 `Nothing` 。 當您無法輕鬆地判斷集合中的專案數目時，這個行為會很有用。  
  
 此索引子屬性就像是執行或的集合的延伸模組屬性 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> 。只有在集合沒有索引子或預設屬性時，才會使用此屬性。  
  
 若要存取或物件集合中第一個元素的值 <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> ，您可以使用 XML `Value` 屬性。 如需詳細資訊，請參閱 [XML 值屬性](xml-value-property.md)。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用擴充索引子來存取物件集合中的第二個子節點 <xref:System.Xml.Linq.XElement> 。 您可以使用子軸屬性來存取集合，該屬性會取得物件中所命名的所有子項目 `phone` `contact` 。  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 此程式碼顯示下列文字：  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](index.md)
- [XML 常值](../xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
- [XML 值屬性](xml-value-property.md)
