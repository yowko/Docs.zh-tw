---
title: HOW TO：從檔案、 字串或 Stream (Visual Basic) 載入 XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 2b9da2062068ef25c5df97ef19b1502999ea78ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052530"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>HOW TO：從檔案、 字串或 Stream (Visual Basic) 載入 XML
您可以建立[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)並且填入從外部來源，例如檔案、 字串或資料流的內容使用幾種方法。 在下列範例會顯示這些方法。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>若要從檔案載入 XML  
  
- 若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>檔案中，使用從物件`Load`方法。 這個方法可能需要的檔案路徑、 文字資料流或 XML 資料流，做為輸入。  
  
     下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Load%28System.String%29>方法來填入<xref:System.Xml.Linq.XDocument>具有來自文字檔案的 XML 物件。  
  
     [!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]  
  
### <a name="to-load-xml-from-a-string"></a>從字串載入 XML  
  
- 若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>物件的字串，您可以使用`Parse`方法。  
  
     下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>方法來填入<xref:System.Xml.Linq.XDocument>以 XML 字串中的物件。  
  
     [!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]  
  
### <a name="to-load-xml-from-a-stream"></a>若要從資料流載入 XML  
  
- 若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>物件從資料流中，您可以使用`Load`方法或<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>方法。  
  
 下列程式碼範例示範使用<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法來填入<xref:System.Xml.Linq.XDocument>具有從 XML 資料流的 XML 物件。  
  
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
