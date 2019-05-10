---
title: HOW TO：存取 XML 子代項目 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 008fd599e527ad4a8d483d2468a57ece1d2b4bdc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598590"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>HOW TO：存取 XML 子代項目 (Visual Basic)
此範例示範如何使用 descendant 軸屬性來存取所有的 XML 項目中具有指定的名稱，以及包含在 XML 項目。 特別是，它會使用`Value`屬性的第一個項目值取得集合中`name`子代 axis 屬性會傳回。 `name`子代 axis 屬性會取得名為的所有項目`name`包含在`contacts`物件。 此範例也會使用`phone`子代 axis 屬性來存取名為的所有下階`phone`包含在`contacts`物件。  
  
## <a name="example"></a>範例  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System.Xml.Linq> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML 子系軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
