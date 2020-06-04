---
title: XML CDATA 常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: b9cc830d27625f192d8f5e059bd3783d05d8ba3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400224"
---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA 常值 (Visual Basic)
代表物件的常值 <xref:System.Xml.Linq.XCData> 。  
  
## <a name="syntax"></a>語法  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>組件  
 `<![CDATA[`  
 必要。 表示 XML CDATA 區段的開頭。  
  
 `content`  
 必要。 要出現在 XML CDATA 區段中的文字內容。  
  
 `]]>`  
 必要。 表示區段的結尾。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XCData> 物件。  
  
## <a name="remarks"></a>備註  
 XML CDATA 區段包含應包含但未剖析的原始文字，以及包含它的 XML。 XML CDATA 區段可以包含任何文字。 這包括保留的 XML 字元。 XML CDATA 區段的結尾是序列 "]] >"。 這表示下列幾點：  
  
- 您不能在 XML CDATA 常值中使用內嵌運算式，因為內嵌的運算式分隔符號是有效的 XML CDATA 內容。  
  
- XML CDATA 區段無法嵌套，因為 `content` 不能包含值 "]] >"。  
  
 您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 元素常值中。  
  
> [!NOTE]
> XML 常值可以跨越多行，但不會使用行接續字元。 這可讓您從 XML 檔案複製內容，並將它直接貼到 Visual Basic 程式中。  
  
 Visual Basic 編譯器會將 XML CDATA 常值轉換為對此函式的呼叫 <xref:System.Xml.Linq.XCData.%23ctor%2A> 。  
  
## <a name="example"></a>範例  
 下列範例會建立 CDATA 區段，其中包含「可以包含常值標記」文字 \<XML> 。  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XCData>
- [XML 元素常值](xml-element-literal.md)
- [XML 常值](index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
