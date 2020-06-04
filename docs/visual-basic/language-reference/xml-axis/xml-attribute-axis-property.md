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
ms.openlocfilehash: 3f60190a949856cb2bbc2eba09d097c09089bea7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408428"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 屬性軸屬性 (Visual Basic)
提供物件之屬性值的存取權， <xref:System.Xml.Linq.XElement> 或物件集合中第一個元素的存取權限 <xref:System.Xml.Linq.XElement> 。  
  
## <a name="syntax"></a>語法  
  
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
 選擇性。 當不是 Visual Basic 中的有效識別碼時，表示屬性名稱的開頭 `attribute` 。  
  
 `attribute`  
 必要。 要存取的屬性名稱，格式為 [ `prefix` ：] `name` 。  
  
|部分|描述|  
|----------|-----------------|  
|`prefix`|選擇性。 屬性的 XML 命名空間前置詞。 必須是以 `Imports` 陳述式定義的全域 XML 命名空間。|  
|`name`|必要。 區域屬性名稱。 請參閱宣告[的 XML 元素和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 選擇性。 當不是 Visual Basic 中的有效識別碼時，代表屬性名稱的結尾 `attribute` 。  
  
## <a name="return-value"></a>傳回值  
 包含值的字串 `attribute` 。 如果屬性名稱不存在， `Nothing` 則會傳回。  
  
## <a name="remarks"></a>備註  
 您可以使用 XML 屬性軸屬性，從物件的名稱， <xref:System.Xml.Linq.XElement> 或從物件集合中的第一個專案，存取屬性的值 <xref:System.Xml.Linq.XElement> 。 您可以依名稱抓取屬性值，或指定新的名稱，並在前面加上 @ identifier，將新的屬性加入至元素。  
  
 當您使用 @ identifier 來參考 XML 屬性時，屬性值會當做字串傳回，而且您不需要明確指定 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。  
  
 XML 屬性的命名規則不同于 Visual Basic 識別碼的命名規則。 若要存取名稱不是有效 Visual Basic 識別碼的 XML 屬性，請以角括弧（）括住名稱 \< and > 。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 屬性軸屬性中的名稱只能使用在全域宣告的 XML 命名空間前置詞（使用 `Imports` 語句）。 它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。 如需詳細資訊，請參閱[Imports 語句（XML 命名空間）](../statements/imports-statement-xml-namespace.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何從名為的 XML 專案集合中，取得名為之 XML 屬性的值 `type` `phone` 。  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 此程式碼顯示下列文字：  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>範例  
 下列範例示範如何以宣告的方式，將 XML 專案的屬性建立為 XML 的一部分，並藉由將屬性新增至物件的實例來動態地執行 <xref:System.Xml.Linq.XElement> 。 `type`屬性會以宣告方式建立，並且 `owner` 會動態建立屬性。  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>範例  
 下列範例會使用角括弧語法來取得名為之 XML 屬性的值 `number-type` ，這在 Visual Basic 中不是有效的識別碼。  
  
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
