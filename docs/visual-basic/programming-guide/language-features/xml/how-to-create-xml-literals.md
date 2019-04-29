---
title: HOW TO：建立 XML 常值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 836ec4390e7675effe57c75c79768272d66925a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775904"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>HOW TO：建立 XML 常值 (Visual Basic)
您可以直接在程式碼中建立 XML 文件、 片段中或項目，藉由使用 XML 常值。 本主題中的範例將示範如何建立 XML 項目具有三個子項目，以及如何建立 XML 文件。  
  
 您也可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Api 來建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。  
  
### <a name="to-create-an-xml-element"></a>若要建立的 XML 項目  
  
- 使用 XML 常值語法，與實際的 XML 語法相同，以建立內嵌的 XML。  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     執行程式碼。 此程式碼的輸出為：  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>若要建立 XML 文件  
  
- 建立內嵌的 XML 文件。 下列程式碼會建立 XML 文件常值語法，XML 宣告、 處理指示、 註解，和此項目包含另一個項目。  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     執行程式碼。 此程式碼的輸出為：  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>另請參閱

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
