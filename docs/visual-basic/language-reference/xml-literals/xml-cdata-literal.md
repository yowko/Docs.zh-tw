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
ms.openlocfilehash: 999531d8146748fe491255663f0d2d17d056bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603830"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA 常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XCData>物件。  
  
## <a name="syntax"></a>語法  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>組件  
 `<![CDATA[`  
 必要。 代表 XML CDATA 區段的開頭。  
  
 `content`  
 必要。 在 XML CDATA 區段中顯示的文字內容。  
  
 `]]>`  
 必要。 表示區段的結尾。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XCData> 物件。  
  
## <a name="remarks"></a>備註  
 XML CDATA 區段包含應該包括但不是剖析 xml 包含它的原始文字。 XML CDATA 區段都可以包含任何文字。 這包括保留的 XML 字元。 XML CDATA 區段結尾序列"]] > 」。 這表示下列各點：  
  
-   您無法在 XML CDATA 常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML 註解內容。  
  
-   XML CDATA 區段不可為巢狀，因為`content`不能包含值 「]] > 」。  
  
 您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 元素常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行，但不會使用行接續字元。 這可讓您從 XML 文件內容複製並貼上直接在 Visual Basic 程式。  
  
 Visual Basic 編譯器會將 XML CDATA 常值轉換成呼叫<xref:System.Xml.Linq.XCData.%23ctor%2A>建構函式。  
  
## <a name="example"></a>範例  
 下列範例會建立包含文字的 CDATA 區段 」 可以包含常值\<XML > 標記 」。  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XCData>  
 [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
