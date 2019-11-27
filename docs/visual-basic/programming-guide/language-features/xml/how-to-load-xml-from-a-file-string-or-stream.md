---
title: 如何：從檔案、字串或資料流載入 XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330965"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>如何：從檔案、字串或資料流載入 XML (Visual Basic)

您可以使用數種方法來建立[XML 常](../../../../visual-basic/language-reference/xml-literals/index.md)值，並以外部來源（例如檔案、字串或資料流程）的內容填入。 下列範例會顯示這些方法。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>從檔案載入 XML

若要從檔案填入 XML 常值（例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件），請使用 `Load` 方法。 這個方法可以接受檔案路徑、文字資料流程或 XML 資料流程做為輸入。

下列程式碼範例示範如何使用 <xref:System.Xml.Linq.XDocument.Load%28System.String%29> 方法，將文字檔中的 XML 填入 <xref:System.Xml.Linq.XDocument> 物件。

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>從字串載入 XML

若要將字串中的 XML 常值（例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件）填入，您可以使用 `Parse` 方法。

下列程式碼範例示範如何使用 <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> 方法，將字串中的 XML 填入 <xref:System.Xml.Linq.XDocument> 物件。

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>從資料流程載入 XML

若要從資料流程填入 XML 常值（例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件），您可以使用 `Load` 方法或 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> 方法。

下列程式碼範例示範如何使用 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法，以 xml 資料流程的 XML 填入 <xref:System.Xml.Linq.XDocument> 物件。

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
