---
title: XML 屬性軸屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: cfc18df4487488bd90d7b0250a9053f55305d8a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631489"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 屬性軸屬性 (Visual Basic)
提供的屬性值存取權<xref:System.Xml.Linq.XElement>物件或集合中的第一個項目<xref:System.Xml.Linq.XElement>物件。  
  
## <a name="syntax"></a>語法  
  
```  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>組件  
 `object`  
 必要項。 <xref:System.Xml.Linq.XElement>物件或集合<xref:System.Xml.Linq.XElement>物件。  
  
 .@  
 必要項。 表示屬性軸屬性的開頭。  
  
 <  
 選擇性。 表示屬性名稱的開頭時`attribute`不在 Visual Basic 中是有效的識別項。  
  
 `attribute`  
 必要項。 若要存取，在表單的屬性名稱的 [`prefix`:]`name`。  
  
|組件|描述|  
|----------|-----------------|  
|`prefix`|選擇性。 XML 屬性的命名空間前置詞。 必須是以 `Imports` 陳述式定義的全域 XML 命名空間。|  
|`name`|必要項。 本機屬性名稱。 請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 選擇性。 代表屬性名稱的結尾時`attribute`不在 Visual Basic 中是有效的識別項。  
  
## <a name="return-value"></a>傳回值  
 字串，包含的值`attribute`。 如果屬性名稱不存在，`Nothing`會傳回。  
  
## <a name="remarks"></a>備註  
 您可以使用 XML 屬性軸屬性來存取屬性的值，依名稱從<xref:System.Xml.Linq.XElement>物件或從集合中的第一個項目<xref:System.Xml.Linq.XElement>物件。 您可以依名稱擷取屬性值，或加入新屬性的項目，藉由指定新名稱，前面加上 @ 識別項。  
  
 當您參考 XML 屬性使用 @ 識別項，則屬性會傳回值為字串，並不需要明確指定<xref:System.Xml.Linq.XAttribute.Value%2A>屬性。  
  
 與 Visual Basic 識別項的命名規則，不同的 XML 屬性的命名規則。 若要存取 XML 屬性具有不是有效的 Visual Basic 識別項的名稱，將名稱括在括弧 (\<和 >)。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 屬性軸屬性 中的名稱可以使用只有 XML 命名空間前置詞使用全域宣告`Imports`陳述式。 它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。 如需詳細資訊，請參閱 < [Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何取得名為 XML 屬性的值`type`集合中的 XML 項目會在名為`phone`。  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 此程式碼顯示下列文字：  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>範例  
 下列範例示範如何以宣告方式，XML 中，而且以動態方式加入的執行個體的屬性建立屬性的 XML 項目這兩個<xref:System.Xml.Linq.XElement>物件。 `type`屬性會以宣告方式建立和`owner`屬性會動態建立。  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>範例  
 下列範例使用角括號語法來取得名為 XML 屬性的值`number-type`，這不是在 Visual Basic 中是有效的識別碼。  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Phone type: work`  
  
## <a name="example"></a>範例  
 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點 」`ns:name`"。  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Phone type: home`  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
