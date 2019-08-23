---
title: XML Value 屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942984"
---
# <a name="xml-value-property-visual-basic"></a>XML Value 屬性 (Visual Basic)
提供<xref:System.Xml.Linq.XElement>物件集合中第一個元素的值存取。  
  
## <a name="syntax"></a>語法  
  
```  
object.Value  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`object`|必要項。 <xref:System.Xml.Linq.XElement> 物件的集合。|  
  
## <a name="return-value"></a>傳回值  
 , `String`其中包含集合中第一個元素的值, 或者`Nothing` , 如果集合是空的, 則為。  
  
## <a name="remarks"></a>備註  
 屬性可讓您輕鬆地存取<xref:System.Xml.Linq.XElement>物件集合中第一個元素的值。 <xref:System.Xml.Linq.XElement.Value%2A> 這個屬性會先檢查集合是否至少包含一個物件。 如果集合是空的, 則這個屬性`Nothing`會傳回。 否則, 這個屬性會傳回集合中第<xref:System.Xml.Linq.XElement.Value%2A>一個元素的屬性值。  
  
> [!NOTE]
> 當您使用 '\@' 識別碼來存取 XML 屬性的值時, 屬性值會當做傳回`String` , 而且您不<xref:System.Xml.Linq.XAttribute.Value%2A>需要明確指定屬性。  
  
 若要存取集合中的其他元素, 您可以使用 XML 延伸模組索引子屬性。 如需詳細資訊, 請參閱[擴充索引子屬性](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)。  
  
## <a name="inheritance"></a>繼承  
 大部分的使用者都不需要執行<xref:System.Collections.Generic.IEnumerable%601>, 因此可以忽略這個區段。  
  
 屬性是實作為類型`IEnumerable(Of XElement)`的擴充屬性。 <xref:System.Xml.Linq.XElement.Value%2A> 此延伸模組屬性的系結就像是擴充方法的系結: 如果型別會實作為其中一個介面, 並定義一個名稱為 "Value" 的屬性, 則該屬性的優先順序高於擴充屬性。 換句話說, 您可以在<xref:System.Xml.Linq.XElement.Value%2A>執行的類別`IEnumerable(Of XElement)`中定義新的屬性來覆寫這個屬性。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用<xref:System.Xml.Linq.XElement.Value%2A>屬性來存取<xref:System.Xml.Linq.XElement>物件集合中的第一個節點。 此範例會使用 [子軸] 屬性, 取得`phone` `contact`物件中名為之所有子節點的集合。  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 此程式碼顯示下列文字：  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>範例  
 下列範例顯示如何從<xref:System.Xml.Linq.XAttribute>物件集合取得 XML 屬性的值。 此範例會使用 [屬性軸] 屬性來顯示所有`type` `phone`元素的屬性值。  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 此程式碼顯示下列文字：  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [擴充索引子屬性](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [XML 子代軸屬性](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML 屬性 (Attribute) 軸屬性 (Property)](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
