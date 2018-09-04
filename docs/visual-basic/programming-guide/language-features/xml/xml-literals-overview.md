---
title: XML 常值概觀 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 03fc8c11b5553c9c3a63bdcb69bf6135050e2c89
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507644"
---
# <a name="xml-literals-overview-visual-basic"></a>XML 常值概觀 (Visual Basic)
*XML 常值*可讓您將 XML 直接併入您的 Visual Basic 程式碼。 XML 常值語法表示[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件，而且這是類似 XML 1.0 語法。 這可讓您更輕鬆地以程式設計方式建立 XML 項目和文件，因為您的程式碼有相同的結構，為最後的 XML。  
  
 Visual Basic 編譯 XML 常值[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供一種簡單的物件模型來建立及操作 XML，且此模型將整合搭配[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。  
  
 您可以在 XML 常值中內嵌 Visual Basic 運算式。 在執行階段，您的應用程式會建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]每個常值，將內嵌的運算式值的物件。 這可讓您指定在 XML 常值內的動態內容。 如需詳細資訊，請參閱 < [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 如需有關 XML 常值語法與 XML 1.0 語法之間差異的詳細資訊，請參閱[XML 常值和 XML 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="simple-literals"></a>簡單的常值  
 您可以建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]輸入或貼上有效的 XML 中的 Visual Basic 程式碼中的物件。 常值的 XML 項目傳回<xref:System.Xml.Linq.XElement>物件。 如需詳細資訊，請參閱 < [XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)並[XML 常值和 XML 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。 下列範例會建立數個項目子系的 XML 項目。  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 您可以建立 XML 文件從 XML 常值與`<?xml version="1.0"?>`，如下列範例所示。 XML 文件常值傳回<xref:System.Xml.Linq.XDocument>物件。 如需詳細資訊，請參閱 < [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  在 Visual Basic 中的 XML 常值語法不等同於 XML 1.0 規格中的語法。 如需詳細資訊，請參閱 < [XML 常值和 XML 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="line-continuation"></a>行接續符號  
 XML 常值可以跨越多行，而不使用行接續字元 （此空間底線輸入順序）。 這可讓您更輕鬆地比較 XML 文件的程式碼中的 XML 常值。  
  
 編譯器會將行接續字元視為 XML 常值的一部分。 因此，您應該使用的空間底線輸入的順序只有在其所屬中時，才[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。  
  
 不過，如果您需要行接續字元內嵌的運算式中有多行的運算式。 如需詳細資訊，請參閱 < [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
## <a name="embedding-queries-in-xml-literals"></a>內嵌在 XML 常值的查詢  
 您可以使用查詢中內嵌的運算式。 當您這樣做時，查詢所傳回的項目會加入 XML 項目。 這可讓您加入 XML 常值中的動態內容，例如使用者查詢的結果。  
  
 例如，下列的程式碼會使用內嵌的查詢來建立 XML 元素的成員`phoneNumbers2`陣列，然後將這些項目新增為子系`contact2`。  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>編譯器從 XML 常值所建立的物件  
 Visual Basic 編譯器會將 XML 常值轉譯成呼叫對等[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]建構函式來建置[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。 例如，Visual Basic 編譯器會轉譯為下列程式碼範例呼叫<xref:System.Xml.Linq.XProcessingInstruction>建構函式 XML 版本指令時，呼叫<xref:System.Xml.Linq.XElement>建構函式`<contact>`， `<name>`，和`<phone>`項目，以及呼叫<xref:System.Xml.Linq.XAttribute>建構函式`type`屬性。 具體來說，假設屬性有下列的範例中，Visual Basic 編譯器會呼叫<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>建構函式兩次。 第一個會將值傳遞`type`for`name`參數和值`home`如`value`參數。 第二個也會將值傳遞`type`for`name`參數，但值`work`如`value`參數。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)
