---
title: 如何：存取 XML 子項目
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 9c33bec9b9ea865d570bab08f27227129867cce9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058296"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>如何：存取 XML 子項目 (Visual Basic)

這個範例示範如何使用子軸屬性來存取 XML 專案中具有指定名稱的所有 XML 子項目。 尤其是，它會使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性，取得集合中子軸屬性傳回之第一個元素的值 `name` 。 `name`子軸屬性會取得 `phone` 物件中所命名的所有子項目 `contact` 。 此範例也會使用 [ `phone` 子軸] 屬性來存取物件中所包含的所有子專案（名稱為 `phone` ） `contact` 。  
  
## <a name="example"></a>範例  

 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>編譯程式碼  

 這個範例需要：  
  
- <xref:System.Xml.Linq> 命名空間的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML Child Axis Property](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [XML 值屬性](../../../language-reference/xml-axis/xml-value-property.md)
- [在 Visual Basic 中存取 XML](accessing-xml.md)
- [XML](index.md)
