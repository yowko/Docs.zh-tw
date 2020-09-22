---
title: XML Attribute Axis Property
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
ms.openlocfilehash: 9eddd132b2d4dd6ffbd935a0c8c57a03a3d65435
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869446"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 屬性軸屬性 (Visual Basic)

提供物件的屬性值 <xref:System.Xml.Linq.XElement> 或物件集合中第一個元素的存取權 <xref:System.Xml.Linq.XElement> 。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>組件  

 `object`  
 必要。 <xref:System.Xml.Linq.XElement>物件或物件的集合 <xref:System.Xml.Linq.XElement> 。  
  
 .@  
 必要。 表示屬性軸屬性的開頭。  
  
 <  
 選擇性。 當不是 `attribute` Visual Basic 中的有效識別碼時，表示屬性名稱的開頭。  
  
 `attribute`  
 必要。 要存取的屬性名稱，格式為 [ `prefix` ：] `name` 。  
  
|組件|描述|  
|----------|-----------------|  
|`prefix`|選擇性。 屬性的 XML 命名空間前置詞。 必須是以 `Imports` 陳述式定義的全域 XML 命名空間。|  
|`name`|必要。 區域屬性名稱。 請參閱宣告 [的 XML 專案和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 選擇性。 當不是 Visual Basic 中的有效識別碼時，表示屬性名稱的結尾 `attribute` 。  
  
## <a name="return-value"></a>傳回值  

 包含值的字串 `attribute` 。 如果屬性名稱不存在， `Nothing` 則會傳回。  
  
## <a name="remarks"></a>備註  

 您可以使用 XML 屬性軸屬性，從物件的名稱 <xref:System.Xml.Linq.XElement> 或物件集合中的第一個元素，存取屬性的值 <xref:System.Xml.Linq.XElement> 。 您可以依名稱抓取屬性值，或指定新的名稱，並在前面加上 @ 識別碼，以將新的屬性加入至元素。  
  
 當您使用 @ 識別碼來參考 XML 屬性時，屬性值會以字串的形式傳回，而且您不需要明確指定 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。  
  
 XML 屬性的命名規則不同于 Visual Basic 識別碼的命名規則。 若要存取名稱不是有效 Visual Basic 識別碼的 XML 屬性，請以角括弧括住名稱 (\< and >) 。  
  
## <a name="xml-namespaces"></a>XML 命名空間  

 屬性軸屬性中的名稱只能使用使用語句來全域宣告的 XML 命名空間前置詞 `Imports` 。 它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。 如需詳細資訊，請參閱 [ (XML 命名空間) 的 Imports 語句 ](../statements/imports-statement-xml-namespace.md)。  
  
## <a name="example"></a>範例  

 下列範例示範如何 `type` 從名為的 xml 專案集合中取得名為之 xml 屬性的值 `phone` 。  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 此程式碼顯示下列文字：  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>範例  

 下列範例示範如何以宣告方式將 XML 專案的屬性建立為 XML 的一部分，並以動態方式將屬性（attribute）加入至物件的實例 <xref:System.Xml.Linq.XElement> 。 `type`屬性是以宣告方式建立的，而且 `owner` 會動態建立屬性。  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>範例  

 下列範例會使用角括弧語法取得名為之 XML 屬性的值 `number-type` ，這在 Visual Basic 中不是有效的識別碼。  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 此程式碼顯示下列文字：  
  
 `Phone type: work`  
  
## <a name="example"></a>範例  

 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後，它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱 "" 的第一個子節點 `ns:name` 。  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 此程式碼顯示下列文字：  
  
 `Phone type: home`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](index.md)
- [XML 常值](../xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
- [宣告的 XML 項目和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
