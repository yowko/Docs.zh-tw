---
title: XML CDATA 常值 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: ee269ca5cf9635fec35165d1ea65d6a6483cadef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828589"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA 常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XCData>物件。  
  
## <a name="syntax"></a>語法  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>組件  
 `<![CDATA[`  
 必要項。 代表 XML CDATA 區段的開始。  
  
 `content`  
 必要項。 在 XML CDATA 區段中顯示的文字內容。  
  
 `]]>`  
 必要項。 表示區段的結尾。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XCData> 物件。  
  
## <a name="remarks"></a>備註  
 XML CDATA 區段包含應該包括但不是剖析 xml，其中包含它的原始文字。 XML CDATA 區段可以包含任何文字。 這包括保留的 XML 字元。 XML CDATA 區段結尾序列"]] > 」。 這表示下列各點：  
  
-   您無法在 XML CDATA 常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML 註解內容。  
  
-   XML CDATA 區段不能巢狀，因為`content`不能包含值"]] > 」。  
  
 您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 元素常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行，但不會使用行接續字元。 這可讓您從 XML 文件複製內容，並將它貼到 Visual Basic 程式直接。  
  
 Visual Basic 編譯器會將 XML CDATA 常值轉換成呼叫<xref:System.Xml.Linq.XCData.%23ctor%2A>建構函式。  
  
## <a name="example"></a>範例  
 下列範例會建立包含文字的 CDATA 區段 」 可以包含常值\<XML > 標記 」。  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XCData>
- [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
