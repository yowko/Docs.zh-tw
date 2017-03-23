---
title: "XML 常值概觀 (Visual Basic) |Microsoft 文件"
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
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 57d036910ba9e49385caca28de222a8a8e28ec56
ms.lasthandoff: 03/13/2017

---
# <a name="xml-literals-overview-visual-basic"></a>XML 常值概觀 (Visual Basic)
*XML 常值*可讓您將 XML 直接載入您[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼。 XML 常值語法代表[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件，並且很相似的 XML 1.0 語法。 這可讓您更輕鬆地以程式設計方式建立 XML 項目和文件，因為您的程式碼有最後的 XML 的結構相同。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯 XML 常值[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]提供一種簡單的物件模型來建立及操作 XML，與此模型整合[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>  
  
 您可以將內嵌[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]在 XML 常值的運算式。 在執行階段，您的應用程式會建立[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]每個常值，將內嵌的運算式值的物件。 這可讓您指定在 XML 常值的動態內容。 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 如需 XML 常值語法與 XML 1.0 語法之間差異的詳細資訊，請參閱[XML 常值和 XML 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="simple-literals"></a>簡單的常值  
 您可以建立[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件存放至您[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]輸入或貼上有效的 XML 中的程式碼。 XML 項目常值傳回<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement> 如需詳細資訊，請參閱[XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)和[XML 常值和 XML 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。 下列範例會建立數個項目子系的 XML 項目。  
  
 [!code-vb[VbXMLSamples #&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 您可以建立 XML 文件從 XML 常值與`<?xml version="1.0"?>`，如下列範例所示。 XML 文件常值傳回<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument> 如需詳細資訊，請參閱[XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
 [!code-vb[VbXMLSamples #&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  中的 XML 常值語法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不等同於 XML 1.0 規格中的語法。 如需詳細資訊，請參閱[XML 常值和 XML 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="line-continuation"></a>行接續符號  
 XML 常值可以跨越多行程式碼，而不需使用行接續字元 （空間底線輸入序列）。 這可讓您更輕鬆地比較 XML 文件的程式碼中的 XML 常值。  
  
 編譯器會將行接續字元視為 XML 常值的一部分。 因此，您的空間底線輸入的順序時才應該使用它屬於[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。  
  
 不過，如果您需要行接續字元內嵌的運算式中有多行的運算式。 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
## <a name="embedding-queries-in-xml-literals"></a>內嵌在 XML 常值的查詢  
 您可以使用查詢中內嵌的運算式。 當您這樣做時，查詢所傳回的項目會加入至 XML 項目。 這可讓您將動態內容，例如使用者查詢的結果加入至 XML 常值。  
  
 例如，下列的程式碼會使用內嵌的查詢來建立 XML 項目中的成員`phoneNumbers2`陣列，然後將這些項目新增為子系的`contact2`。  
  
 [!code-vb[VbXMLSamples #&7;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>編譯器從 XML 常值所建立的物件  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 常值轉譯為對等呼叫[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]建構函式來建置[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]物件。 例如，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將下列程式碼範例轉譯成呼叫<xref:System.Xml.Linq.XProcessingInstruction>XML 版本指令時，建構函式呼叫<xref:System.Xml.Linq.XElement>建構函式`<contact>`， `<name>`，和`<phone>`項目，並呼叫<xref:System.Xml.Linq.XAttribute>建構函式`type`屬性。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XProcessingInstruction> 具體來說，在下列範例中，指定屬性[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會呼叫<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>建構函式兩次。</xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> 第一個會將值傳遞`type`的`name`參數和值`home`的`value`參數。 第二個也會將值傳遞`type`的`name`參數，但值`work`的`value`參數。  
  
 [!code-vb[VbXMLSamples #&6;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>   
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)
