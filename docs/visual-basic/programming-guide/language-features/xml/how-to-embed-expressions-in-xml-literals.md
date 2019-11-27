---
title: 如何：將運算式內嵌在 XML 常值中
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332933"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>如何：將運算式內嵌在 XML 常值中 (Visual Basic)
您可以結合 XML 常值與內嵌運算式，建立 XML 檔、片段或包含在執行時間建立之內容的元素。 下列範例示範如何在執行時間使用內嵌運算式來填入元素內容、屬性和專案名稱。  
  
 內嵌運算式的語法是 `<%=` `exp` `%>`，這是 ASP.NET 所使用的相同語法。 如需詳細資訊，請參閱[XML 中的內嵌運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 您也可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Api 來建立 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。 如需詳細資訊，請參閱 <xref:System.Xml.Linq.XElement>。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-insert-text-as-element-content"></a>插入文字做為元素內容  
  
- 下列範例示範如何在開頭和結尾名稱元素之間插入 `contactName` 變數中包含的文字。  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>若要將文字插入為屬性值  
  
- 下列範例示範如何插入包含在 `phoneType` 變數中的文字，做為 `type` 屬性的值。  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>若要插入元素名稱的文字  
  
- 下列範例示範如何插入包含在 `elementName` 變數中的文字，做為元素的名稱。  
  
     使用這項技術來建立專案時，您必須使用 \</> 標記來關閉它們。  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>另請參閱

- [如何：建立 XML 常值](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
