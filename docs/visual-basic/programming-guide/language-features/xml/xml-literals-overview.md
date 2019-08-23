---
title: XML 常值概觀 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 4024f4ad2b2aa8cb1897e83d87a7a00b1ba25e67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964699"
---
# <a name="xml-literals-overview-visual-basic"></a>XML 常值概觀 (Visual Basic)
*Xml 常*值可讓您將 xml 直接併入 Visual Basic 的程式碼中。 Xml 常值語法代表[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件, 而且類似于 XML 1.0 語法。 這可讓您更輕鬆地以程式設計方式建立 XML 元素和檔, 因為您的程式碼與最終 XML 的結構相同。  
  
 Visual Basic 會將 XML 常[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]值編譯成物件。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]提供用來建立和管理 XML 的簡單物件模型, 而此模型可與[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]完美整合。 如需詳細資訊，請參閱 <xref:System.Xml.Linq.XElement>。  
  
 您可以將 Visual Basic 運算式內嵌在 XML 常值中。 在執行時間, 您的應用程式[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]會為每個常值建立一個物件, 並併入內嵌運算式的值。 這可讓您指定 XML 常值內的動態內容。 如需詳細資訊, 請參閱[XML 中的內嵌運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 如需 XML 常值語法與 XML 1.0 語法之間差異的詳細資訊, 請參閱[Xml 常值和 xml 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="simple-literals"></a>簡單常值  
 您可以輸入或[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]貼上有效的 XML, 在 Visual Basic 程式碼中建立物件。 XML 元素常<xref:System.Xml.Linq.XElement>值會傳回物件。 如需詳細資訊, 請參閱[Xml 元素常](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)值和[xml 常值和 xml 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。 下列範例會建立具有數個子項目的 XML 專案。  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 您可以使用`<?xml version="1.0"?>`來啟動 xml 常值, 以建立 xml 檔, 如下列範例所示。 XML 檔常<xref:System.Xml.Linq.XDocument>值會傳回物件。 如需詳細資訊, 請參閱[XML 檔常](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)值。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Visual Basic 中的 XML 常值語法與 XML 1.0 規格中的語法不相同。 如需詳細資訊, 請參閱[Xml 常值和 xml 1.0 規格](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="line-continuation"></a>行接續  
 XML 常值可以跨越多行, 而不需要使用行接續字元 (空格-底線-enter 順序)。 這可讓您更輕鬆地比較程式碼中的 XML 常值與 XML 檔。  
  
 編譯器會將行接續字元視為 XML 常值的一部分。 因此, 只有當它屬於[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件時, 您才應該使用空格鍵-底線-enter 序列。  
  
 不過, 如果內嵌運算式中有多行運算式, 您就需要行接續字元。 如需詳細資訊, 請參閱[XML 中的內嵌運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
## <a name="embedding-queries-in-xml-literals"></a>在 XML 常值中嵌入查詢  
 您可以使用內嵌運算式中的查詢。 當您執行這項操作時, 查詢所傳回的元素會加入至 XML 元素。 這可讓您將動態內容 (例如使用者查詢的結果) 新增至 XML 常值。  
  
 例如, 下列程式碼會使用內嵌查詢, 從`phoneNumbers2`陣列的成員建立 XML 專案, 然後將這些專案當做的`contact2`子系加入。  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>編譯器如何從 XML 常值建立物件  
 Visual Basic 編譯器會將 XML 常值轉譯為對等[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]的函式的呼叫[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , 以建立物件。 例如, Visual Basic 編譯器會將下列程式碼範例轉譯為 XML 版本<xref:System.Xml.Linq.XProcessingInstruction>指令的函式呼叫, 呼叫`<contact>`、 `<name>`和`<phone>`的<xref:System.Xml.Linq.XElement>函式元素, 並呼叫<xref:System.Xml.Linq.XAttribute> `type`屬性的函式。 具體而言, 假設下列範例中的屬性, Visual Basic 編譯器會呼叫兩次<xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29>此函式。 `type`第一個會傳遞`name`參數的值`value`和參數的值`home` 。 第二`type`個也會傳遞`name`參數的值, `value`但參數的值`work`為。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)
