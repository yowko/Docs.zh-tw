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
ms.openlocfilehash: 109c4b45a5e3ed4e3e4db49687df5cb127a5e0c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352664"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>XML 屬性軸屬性 (Visual Basic)
Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.  
  
## <a name="syntax"></a>語法  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>組件  
 `object`  
 必要項。 An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.  
  
 .@  
 必要項。 Denotes the start of an attribute axis property.  
  
 <  
 選擇項。 Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.  
  
 `attribute`  
 必要項。 Name of the attribute to access, of the form [`prefix`:]`name`.  
  
|組件|描述|  
|----------|-----------------|  
|`prefix`|選擇項。 XML namespace prefix for the attribute. 必須是以 `Imports` 陳述式定義的全域 XML 命名空間。|  
|`name`|必要項。 Local attribute name. See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 選擇項。 Denotes the end of the name of the attribute when `attribute` is not a valid identifier in Visual Basic.  
  
## <a name="return-value"></a>傳回值  
 A string that contains the value of `attribute`. If the attribute name does not exist, `Nothing` is returned.  
  
## <a name="remarks"></a>備註  
 You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects. You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.  
  
 When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.  
  
 The naming rules for XML attributes differ from the naming rules for Visual Basic identifiers. To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement. 它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。 For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>範例  
 The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 此程式碼顯示下列文字：  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>範例  
 The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object. The `type` attribute is created declaratively and the `owner` attribute is created dynamically.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 此程式碼顯示下列文字：  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>範例  
 The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 此程式碼顯示下列文字：  
  
 `Phone type: work`  
  
## <a name="example"></a>範例  
 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 此程式碼顯示下列文字：  
  
 `Phone type: home`  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
