---
title: "How to: Load XML from a File, String, or Stream (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML [Visual Basic], loading"
  - "LINQ to XML [Visual Basic], loading XML from files"
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Load XML from a File, String, or Stream (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以使用數種方法建立 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)，並且以外部來源 \(例如檔案、字串或資料流\) 的內容加以填入 \(Populate\)。  以下範例會顯示這些方法。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要從檔案載入 XML  
  
-   若要從檔案填入 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件之類的 XML 常值 \(Literal\)，請使用 `Load` 方法。  此方法可以採用檔案路徑、文字資料流或 XML 資料流做為輸入項目。  
  
     下列程式碼範例顯示使用 <xref:System.Xml.Linq.XDocument.Load%28System.String%29> 方法，從文字檔案填入 XML 的 <xref:System.Xml.Linq.XDocument> 物件。  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### 若要從字串載入 XML  
  
-   若要從字串填入 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件之類的 XML 常值，您可以使用 `Parse` 方法。  
  
     下列程式碼範例顯示使用 <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName> 方法，從字串填入 XML 的 <xref:System.Xml.Linq.XDocument> 物件。  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### 若要從資料流載入 XML  
  
-   若要從資料流填入 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件之類的 XML 常值，您可以使用 `Load` 方法或 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName> 方法。  
  
 下列程式碼範例顯示使用 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 方法，從 XML 資料流填入 XML 的 <xref:System.Xml.Linq.XDocument> 物件。  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## 請參閱  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>   
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)