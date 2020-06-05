---
title: 如何：存取 XML 子代項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 03c403aa3c187b0b9d2006104eccaa1f9cd8aec5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392632"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>如何：存取 XML 子代項目 (Visual Basic)
這個範例示範如何使用子代軸屬性來存取所有具有指定名稱且包含在 XML 專案底下的 XML 專案。 特別是，它會使用 `Value` 屬性來取得子代 axis 屬性傳回之集合中第一個元素的值 `name` 。 [下階 `name` 軸] 屬性會取得 `name` 包含在物件中名為的所有元素 `contacts` 。 這個範例也會使用 [下階 `phone` 軸] 屬性來存取 `phone` 包含在物件中名為的所有子系 `contacts` 。  
  
## <a name="example"></a>範例  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- <xref:System.Xml.Linq> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML Descendant Axis Property](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML 值屬性](../../../language-reference/xml-axis/xml-value-property.md)
- [在 Visual Basic 中存取 XML](accessing-xml.md)
- [XML](index.md)
