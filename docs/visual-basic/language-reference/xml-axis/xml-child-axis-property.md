---
title: XML Child Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: c6af9584931206fecde3154a91a60cfd38278ec0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873070"
---
# <a name="xml-child-axis-property-visual-basic"></a>XML 子代軸屬性 (Visual Basic)

提供下列任一項目之子系的存取：<xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件的集合，或是 <xref:System.Xml.Linq.XDocument> 物件的集合。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`object`|必要。 <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。|  
|。 <|必要。 代表子軸屬性的開頭。|  
|`child`|必要。 要存取之子節點的名稱，格式為 `[prefix:]name` 。<br /><br /> -   `Prefix` 參數. 子節點的 XML 命名空間前置詞。 必須是以 `Imports` 陳述式定義的全域 XML 命名空間。<br />-   `Name` 必. 本機子節點名稱。 請參閱宣告 [的 XML 專案和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
|>|必要。 代表子軸屬性的結尾。|  
  
## <a name="return-value"></a>傳回值  

 <xref:System.Xml.Linq.XElement> 物件的集合。  
  
## <a name="remarks"></a>備註  

 您可以使用 XML 子軸屬性，從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件，或從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件集合依據名稱存取子節點。 使用 XML `Value` 屬性來存取傳回的集合中第一個子節點的值。 如需詳細資訊，請參閱 [XML 值屬性](xml-value-property.md)。  
  
 Visual Basic 編譯器會將子軸屬性轉換成方法的呼叫 <xref:System.Xml.Linq.XContainer.Elements%2A> 。  
  
## <a name="xml-namespaces"></a>XML 命名空間  

 子軸屬性中的名稱只可以使用以 `Imports` 陳述式全域宣告的 XML 命名空間前置詞。 它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。 如需詳細資訊，請參閱 [ (XML 命名空間) 的 Imports 語句 ](../statements/imports-statement-xml-namespace.md)。  
  
## <a name="example"></a>範例  

 下列範例示範如何從 `contact` 物件存取名為 `phone` 的子節點。  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 此程式碼顯示下列文字：  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>範例  

 下列範例示範如何從 `contacts` 物件的 `contact` 子軸屬性傳回的集合存取名為 `phone` 的子節點。  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 此程式碼顯示下列文字：  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>範例  

 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。 然後它會使用命名空間的前置詞來建立 XML 常值，以及存取完整名稱為 `ns:name` 的第一個子節點。  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 此程式碼顯示下列文字：  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- [XML 軸屬性](index.md)
- [XML 常值](../xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
- [宣告的 XML 項目和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
