---
title: 如何：存取 XML 子代項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347162"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>如何：存取 XML 子代項目 (Visual Basic)
這個範例示範如何使用子代軸屬性來存取所有具有指定名稱且包含在 XML 專案底下的 XML 專案。 特別是，它會使用 `Value` 屬性，取得集合中 `name` 下階軸屬性傳回的第一個元素的值。 [`name` 下階軸] 屬性會取得包含在 `contacts` 物件中名為 `name` 的所有元素。 這個範例也會使用 `phone` 子代軸屬性來存取包含在 `contacts` 物件中名為 `phone` 的所有子系。  
  
## <a name="example"></a>範例  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System.Xml.Linq> 命名空間的參考。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML 子系軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
