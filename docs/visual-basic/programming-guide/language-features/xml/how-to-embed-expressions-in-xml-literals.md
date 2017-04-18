---
title: "如何︰ 將運算式內嵌在 XML 常值 (Visual Basic) |Microsoft 文件"
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
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
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
ms.openlocfilehash: 40b0e4273223093262bc54a2b13d28fc93a44c69
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>如何：將運算式內嵌在 XML 常值中 (Visual Basic)
您可以結合 XML 常值的內嵌的運算式，來建立 XML 文件、 片段中或包含在執行階段建立的內容項目。 下列範例示範如何使用內嵌的運算式來填入項目內容、 屬性和項目名稱，在執行階段。  
  
 內嵌運算式的語法是`<%=` `exp` `%>`，這是相同的語法，[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]使用。 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 您也可以使用[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]Api 來建立[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-insert-text-as-element-content"></a>若要為項目內容中插入文字  
  
-   下列範例示範如何插入文字中包含的`contactName`變數之間的開頭和結尾的名稱項目。  
  
     [!code-vb[VbXMLSamples #&39;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>若要插入文字做為屬性值  
  
-   下列範例示範如何插入文字中包含的`phoneType`變數的值為`type`屬性。  
  
     [!code-vb[VbXMLSamples #&40;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>若要插入的項目名稱的文字  
  
-   下列範例示範如何插入文字中包含的`elementName`變數做為項目的名稱。  
  
     當使用這項技術建立的項目，您必須先關閉它們與\</ > 標記。  
  
     [!code-vb[VbXMLSamples #&41;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 建立 XML 常值](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)   
 [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
