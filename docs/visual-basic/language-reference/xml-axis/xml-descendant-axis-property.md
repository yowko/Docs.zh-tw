---
title: "XML 子代軸屬性 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 434dc90c643381bdc27b2da54a7418e39bf15e98
ms.lasthandoff: 03/13/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML 子代軸屬性 (Visual Basic)
可讓您存取下列的下階︰<xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或一系列<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
## <a name="syntax"></a>語法  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a>組件  
 `object`  
 必要項。 <xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或一系列<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
 ...<  
 必要項。 代表子代軸屬性開始。  
  
 `descendant`  
 必要項。 若要存取，表單的下階節點的名稱 [`prefix``:`]`name`。  
  
|組件|描述|  
|----------|-----------------|  
|`prefix`|選擇項。 XML 子代節點的命名空間前置詞。 必須是全域的 XML 命名空間定義使用`Imports`陳述式。|  
|`name`|必要項。 子系節點的本機名稱。 請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 必要項。 代表子代軸屬性的結尾。  
  
## <a name="return-value"></a>傳回值  
 一系列<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement>  
  
## <a name="remarks"></a>備註  
 您可以使用 XML 子代軸屬性存取子系節點，依名稱從<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件，或從一堆<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> 使用 XML`Value`屬性來存取所傳回集合中的第一個子系節點的值。 如需詳細資訊，請參閱[XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器將子代軸屬性轉換成呼叫<xref:System.Xml.Linq.XContainer.Descendants%2A>方法。</xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 子代 axis 屬性中的名稱可以使用僅與全域宣告的 XML 命名空間`Imports`陳述式。 它不能使用 XML 項目常值內本機宣告的 XML 命名空間。 如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何存取名為第一個子系節點的值`name`和值的所有子系的節點，名為`phone`從`contacts`物件。  
  
 [!code-vb[VbXMLSamples #&25;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>範例  
 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點的值`ns:name`。  
  
 [!code-vb[VbXMLSamples #&26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>   
 [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)   
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
