---
title: "如何︰ 從檔案、 字串或資料流 (Visual Basic) 載入 XML |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 242c8b79cbe1329b6f53e9fd4e5495d4a157e08c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>如何：從檔案、字串或資料流載入 XML (Visual Basic)
您可以建立[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)和它們的內容填入從外部來源，例如檔案、 字串或資料流使用幾種方法。 在下列範例會顯示這些方法。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>若要從檔案載入 XML  
  
-   若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件從檔案、 使用`Load`方法。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> 這個方法可能需要的檔案路徑、 文字資料流或 XML 資料流，做為輸入。  
  
     下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Load%28System.String%29>方法填入<xref:System.Xml.Linq.XDocument>物件與 XML 的文字檔。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument.Load%28System.String%29>  
  
     [!code-vb[VbXMLSamples #&43;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>從字串載入 XML  
  
-   若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件的字串，您可以使用`Parse`方法。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
     下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName>方法填入<xref:System.Xml.Linq.XDocument>以 XML 字串中的物件。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName>  
  
     [!code-vb[VbXMLSamples #&47;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>若要從資料流載入 XML  
  
-   若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件從資料流中，您可以使用`Load`方法或<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>方法。</xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
 下列程式碼範例示範使用<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法填入<xref:System.Xml.Linq.XDocument>物件以從 XML 資料流的 XML。</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XNode.ReadFrom%2A>  
  
 [!code-vb[VbXMLSamples #&46;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>   
 [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)

