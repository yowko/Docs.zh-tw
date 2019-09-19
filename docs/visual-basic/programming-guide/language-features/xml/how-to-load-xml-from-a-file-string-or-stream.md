---
title: 作法：從檔案、字串或資料流程載入 XML （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054171"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>HOW TO：從檔案、字串或資料流程載入 XML （Visual Basic）

您可以使用數種方法來建立[XML 常](../../../../visual-basic/language-reference/xml-literals/index.md)值，並以外部來源（例如檔案、字串或資料流程）的內容填入。 下列範例會顯示這些方法。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>從檔案載入 XML

若要從檔案填入 XML 常值<xref:System.Xml.Linq.XElement> （ <xref:System.Xml.Linq.XDocument>例如）或物件，請使用`Load`方法。 這個方法可以接受檔案路徑、文字資料流程或 XML 資料流程做為輸入。

下列程式碼範例示範如何使用<xref:System.Xml.Linq.XDocument.Load%28System.String%29>方法，將文字檔中的 XML <xref:System.Xml.Linq.XDocument>填入物件。

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>從字串載入 XML

若要從字串填入 XML 常值<xref:System.Xml.Linq.XElement> （ <xref:System.Xml.Linq.XDocument>例如或物件`Parse` ），您可以使用方法。

下列程式碼範例示範如何使用<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>方法，將字串中的 XML <xref:System.Xml.Linq.XDocument>填入物件。

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>從資料流程載入 XML

若要從資料流程填入 XML 常值<xref:System.Xml.Linq.XElement> （ <xref:System.Xml.Linq.XDocument>例如或物件`Load` ），您可以<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>使用方法或方法。

下列程式碼範例示範如何使用<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法，以 xml 資料流程的 xml <xref:System.Xml.Linq.XDocument>填入物件。

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
