---
title: XML 常值概觀
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 4eaa9399ca0038e3142886abf2161266f8c77782
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636077"
---
# <a name="xml-literals-overview-visual-basic"></a>XML 常值概觀 (Visual Basic)
*Xml 常*值可讓您將 xml 直接併入 Visual Basic 的程式碼中。 XML 常值語法代表 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件，而且類似于 XML 1.0 語法。 這可讓您更輕鬆地以程式設計方式建立 XML 元素和檔，因為您的程式碼與最終 XML 的結構相同。  
  
 Visual Basic 會將 XML 常值編譯成 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供簡單的物件模型來建立和管理 XML，而此模型與語言整合式查詢（LINQ）緊密整合。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。  
  
 您可以將 Visual Basic 運算式內嵌在 XML 常值中。 在執行時間，您的應用程式會為每個常值建立 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件，並併入內嵌運算式的值。 這可讓您指定 XML 常值內的動態內容。 如需詳細資訊，請參閱[XML 中的內嵌運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 如需 XML 常值語法與 XML 1.0 語法之間差異的詳細資訊，請參閱[Xml 常值和 xml 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="simple-literals"></a>簡單常值  
 您可以藉由輸入或貼上有效的 XML，在您的 Visual Basic 程式碼中建立 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。 XML 元素常值會傳回 <xref:System.Xml.Linq.XElement> 物件。 如需詳細資訊，請參閱[Xml 元素常](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)值和[xml 常值和 xml 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。 下列範例會建立具有數個子項目的 XML 專案。  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 您可以使用 `<?xml version="1.0"?>`啟動 XML 常值，以建立 XML 檔，如下列範例所示。 XML 檔常值會傳回 <xref:System.Xml.Linq.XDocument> 物件。 如需詳細資訊，請參閱[XML 檔常](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)值。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Visual Basic 中的 XML 常值語法與 XML 1.0 規格中的語法不相同。 如需詳細資訊，請參閱[Xml 常值和 xml 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="line-continuation"></a>行接續  
 XML 常值可以跨越多行，而不需要使用行接續字元（空格-底線-enter 順序）。 這可讓您更輕鬆地比較程式碼中的 XML 常值與 XML 檔。  
  
 編譯器會將行接續字元視為 XML 常值的一部分。 因此，只有當它屬於 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件時，您才應該使用空格鍵-底線-enter 序列。  
  
 不過，如果內嵌運算式中有多行運算式，您就需要行接續字元。 如需詳細資訊，請參閱[XML 中的內嵌運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
## <a name="embedding-queries-in-xml-literals"></a>在 XML 常值中嵌入查詢  
 您可以使用內嵌運算式中的查詢。 當您執行這項操作時，查詢所傳回的元素會加入至 XML 元素。 這可讓您將動態內容（例如使用者查詢的結果）新增至 XML 常值。  
  
 例如，下列程式碼會使用內嵌查詢，從 `phoneNumbers2` 陣列的成員建立 XML 元素，然後將這些元素加入 `contact2`的子系。  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>編譯器如何從 XML 常值建立物件  
 Visual Basic 編譯器會將 XML 常值轉譯為對等的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 處理函式的呼叫，以建立 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。 例如，Visual Basic 編譯器會將下列程式碼範例轉譯為 XML 版本指令的 <xref:System.Xml.Linq.XProcessingInstruction> 函式呼叫、針對 `<contact>`、`<name>`和 `<phone>` 元素呼叫 <xref:System.Xml.Linq.XElement> 的函式，以及呼叫 <xref:System.Xml.Linq.XAttribute> 屬性的 `type` 函式。 具體而言，假設下列範例中的屬性，Visual Basic 編譯器會呼叫 <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> 的兩次函式。 第一個會傳遞 `name` 參數的值 `type`，以及 `value` 參數的值 `home`。 第二個也會傳遞 `name` 參數的值 `type`，但 `value` 參數的值 `work`。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XElement>
- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)
