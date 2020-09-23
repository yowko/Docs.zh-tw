---
title: 如何：將運算式內嵌在 XML 常值中
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 5ce1386e6a1ff8ffce296f5cea694499633eb011
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071205"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>如何：將運算式內嵌在 XML 常值中 (Visual Basic)

您可以結合 XML 常值與內嵌運算式，建立 XML 檔、片段或元素，其中包含在執行時間建立的內容。 下列範例示範如何在執行時間使用內嵌運算式來填入專案內容、屬性和專案名稱。  
  
 內嵌運算式的語法是 `<%=` `exp` `%>` ，它與 ASP.NET 使用的語法相同。 如需詳細資訊，請參閱 [XML 中的內嵌運算式](embedded-expressions-in-xml.md)。  
  
 您也可以使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] api 來建立 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-insert-text-as-element-content"></a>將文字插入為元素內容  
  
- 下列範例示範如何在 `contactName` 開頭和結尾名稱專案之間插入變數中所包含的文字。  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>將文字插入為屬性值  
  
- 下列範例示範如何將變數中包含的文字插入 `phoneType` 為屬性的值 `type` 。  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>若要插入元素名稱的文字  
  
- 下列範例示範如何將變數中所包含的文字插入 `elementName` 元素的名稱。  
  
     使用這項技術來建立專案時，您必須以標記關閉 \</> 。  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>另請參閱

- [如何：建立 XML 常值](how-to-create-xml-literals.md)
- [XML 中內嵌的運算式](embedded-expressions-in-xml.md)
- [在 Visual Basic 中建立 XML](creating-xml.md)
- [XML](index.md)
