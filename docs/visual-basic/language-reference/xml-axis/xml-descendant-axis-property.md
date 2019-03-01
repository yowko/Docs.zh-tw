---
title: XML 子代軸屬性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: f6d8a958b5a33c236ca5273cccda0e13693b564e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973531"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML 子代軸屬性 (Visual Basic)
可讓您存取下列的下階：<xref:System.Xml.Linq.XElement>物件，<xref:System.Xml.Linq.XDocument>物件、 集合<xref:System.Xml.Linq.XElement>物件或集合<xref:System.Xml.Linq.XDocument>物件。  
  
## <a name="syntax"></a>語法  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>組件  
 `object`  
 必要項。 
  <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。  
  
 ...<  
 必要項。 表示子系軸屬性的開頭。  
  
 `descendant`  
 必要項。 若要存取，在表單的子系節點的名稱 [`prefix:]name`。  
  
|組件|描述|  
|----------|-----------------|  
|`prefix`|選擇性。 子代節點的 XML 命名空間前置詞。 必須是全域的 XML 命名空間定義使用`Imports`陳述式。|  
|`name`|必要項。 子系節點的本機名稱。 請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 必要項。 代表子系軸屬性的結尾。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XElement> 物件的集合。  
  
## <a name="remarks"></a>備註  
 您可以使用 XML 子代軸屬性存取子系節點，依名稱從<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>物件，或從集合<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件。 使用 XML`Value`屬性來存取傳回之集合中的第一個子系節點的值。 如需詳細資訊，請參閱 < [XML Value 屬性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
 Visual Basic 編譯器會將子系軸屬性轉換成呼叫<xref:System.Xml.Linq.XContainer.Descendants%2A>方法。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 子代 axis 屬性中的名稱可以使用僅有全域宣告的 XML 命名空間`Imports`陳述式。 它不能使用 XML 元素常值內本機宣告的 XML 命名空間。 如需詳細資訊，請參閱 < [Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何存取名為第一個子系節點的值`name`和名為所有的子代節點的值`phone`從`contacts`物件。  
  
 [!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]  
  
 此程式碼顯示下列文字：  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>範例  
 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點的值`ns:name`。  
  
 [!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]  
  
 此程式碼顯示下列文字：  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
