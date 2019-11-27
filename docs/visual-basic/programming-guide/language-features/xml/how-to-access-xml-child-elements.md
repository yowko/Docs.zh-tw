---
title: 如何：存取 XML 子項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: af5ea809cb0777b16230f20e133764dd5f1f86d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332319"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>如何：存取 XML 子項目 (Visual Basic)
這個範例示範如何使用子軸屬性來存取 XML 元素中具有指定名稱的所有 XML 子專案。 特別是，它會使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來取得集合中的第一個專案的值，`name` 的子軸屬性會傳回該元素。 `name` 的子軸屬性會取得 `contact` 物件中名為 `phone` 的所有子項目。 這個範例也會使用 `phone` 的子軸屬性，存取包含在 `contact` 物件中名為 `phone` 的所有子項目。  
  
## <a name="example"></a>範例  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System.Xml.Linq> 命名空間的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML 子代軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
