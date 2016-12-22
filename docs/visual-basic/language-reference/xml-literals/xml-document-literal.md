---
title: "XML Document Literal (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralDocument"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML document literal [Visual Basic]"
  - "XML literals [Visual Basic], document"
  - "XML documents [Visual Basic], creating"
  - "document literal [Visual Basic]"
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Document Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

常值 \(Literal\)，表示 <xref:System.Xml.Linq.XDocument> 物件。  
  
## 語法  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`encoding`|選擇項。  常值文字，宣告文件要使用哪種編碼。|  
|`standalone`|選擇項。  常值文字，  必須是 "yes" 或 "no"。|  
|`piCommentList`|選擇項。  XML 處理指示和 XML 註解的清單。  採用下列格式：<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 每個 `piComment` ``  都可以是下列其中一項：<br /><br /> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|必要項。  文件的根項目。  格式為下列其中一種：<br /><br /> <ul><li>[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>`<%=` `elementExp` `%>` 格式的內嵌運算式。  `elementExp` 會傳回下列其中一項：<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> 物件。</li><li>包含一個 <xref:System.Xml.Linq.XElement> 物件和任意數量之 <xref:System.Xml.Linq.XProcessingInstruction> 和 <xref:System.Xml.Linq.XComment> 物件的集合。</li></ul></li></ul><br /> 如需詳細資訊，請參閱 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。|  
  
## 傳回值  
 <xref:System.Xml.Linq.XDocument> 物件。  
  
## 備註  
 XML 文件常值是由常值開頭的 XML 宣告來識別。  每個 XML 文件常值都必須剛好有一個根 XML 項目，但可以有任意數量的 XML 處理指示和 XML 註解。  
  
 XML 文件常值無法顯示在 XML 項目中。  
  
> [!NOTE]
>  XML 常值 \(Literal\) 可以在不需使用行接續字元的情況下跨越數行。  這可讓您複製 XML 文件中的內容，並直接貼上至 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器會將 XML 文件常值轉換為對 <xref:System.Xml.Linq.XDocument.%23ctor%2A> 和 <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> 建構函式的呼叫。  
  
## 範例  
 下列範例會建立 XML 文件，其具有 XML 宣告、處理指示、註解以及包含其他項目的項目。  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument>   
 [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)