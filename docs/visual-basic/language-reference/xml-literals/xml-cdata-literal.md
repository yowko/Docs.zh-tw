---
title: XML CDATA 常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349439"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA 常值 (Visual Basic)
A literal representing an <xref:System.Xml.Linq.XCData> object.  
  
## <a name="syntax"></a>語法  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>組件  
 `<![CDATA[`  
 必要項。 Denotes the start of the XML CDATA section.  
  
 `content`  
 必要項。 Text content to appear in the XML CDATA section.  
  
 `]]>`  
 必要項。 Denotes the end of the section.  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XCData> 物件。  
  
## <a name="remarks"></a>備註  
 XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it. A XML CDATA section can contain any text. This includes reserved XML characters. The XML CDATA section ends with the sequence "]]>". This implies the following points:  
  
- You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.  
  
- XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".  
  
 You can assign an XML CDATA literal to a variable, or include it in an XML element literal.  
  
> [!NOTE]
> An XML literal can span multiple lines but does not use line continuation characters. This enables you to copy content from an XML document and paste it directly into a Visual Basic program.  
  
 The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.  
  
## <a name="example"></a>範例  
 The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XCData>
- [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
