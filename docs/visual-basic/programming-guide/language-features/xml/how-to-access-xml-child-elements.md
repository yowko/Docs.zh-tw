---
title: 如何：存取 XML 子項目 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 4ec7743a30b8101d813ac414a8f5164aeb6c593d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>如何：存取 XML 子項目 (Visual Basic)
這個範例會示範如何使用子軸屬性，來存取所有的 XML 項目具有指定的名稱的 XML 子項目。 特別是，它會使用<xref:System.Xml.Linq.XElement.Value%2A>屬性集合中取得的第一個項目值`name`子軸屬性傳回。 `name`子軸屬性會取得名為的所有子項目`phone`中`contact`物件。 此範例也會使用`phone`子軸屬性，來存取具名的所有子項目`phone`包含在`contact`物件。  
  
## <a name="example"></a>範例  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   <xref:System.Xml.Linq> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [XML 子代軸屬性](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML Value 屬性](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
