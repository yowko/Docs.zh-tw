---
title: "How to: Embed Expressions in XML Literals (Visual Basic) | Microsoft Docs"
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
  - "embedded expressions [Visual Basic]"
  - "XML literals [Visual Basic], embedded expressions"
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Embed Expressions in XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

您可以將 XML 常值 \(Literal\) 與內嵌運算式合併使用，以建立在執行階段才會產生內容的 XML 文件、片段或項目。  下列範例示範如何使用內嵌運算式填入 \(Populate\) 執行階段時的項目內容、屬性和項目名稱。  
  
 內嵌運算式的語法為 `<%=` `exp` `%>`，與 [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] 使用的語法相同。如需詳細資訊，請參閱 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 您也可以使用 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] API 來建立 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件。  如需詳細資訊，請參閱 <xref:System.Xml.Linq.XElement>。  
  
## 程序  
  
#### 若要插入文字做為項目內容  
  
-   下列範例顯示如何在 name 項目的開頭標記和結尾標記之間，插入 `contactName` 變數中包含的文字。  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### 若要插入文字做為屬性值  
  
-   下列範例顯示如何插入 `phoneType` 變數中包含的文字，做為 `type` 屬性 \(Attribute\) 的值。  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### 若要插入文字做為項目名稱  
  
-   下列範例顯示如何插入 `elementName` 變數中包含的文字，做為項目的名稱。  
  
     使用這個方法建立項目時，必須以 \<\/\> 標記做結尾。  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## 請參閱  
 [How to: Create XML Literals](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)   
 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)