---
title: XML 常值概觀
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: c65cac4f6e8f5f314587f20d5c373c92ea0c51e5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085382"
---
# <a name="xml-literals-overview-visual-basic"></a>XML 常值概觀 (Visual Basic)

*Xml 常*值可讓您將 xml 直接併入 Visual Basic 程式碼中。 XML 常值語法代表 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件，它類似于 XML 1.0 語法。 這可讓您更輕鬆地以程式設計方式建立 XML 元素和檔，因為您的程式碼與最後一個 XML 具有相同的結構。  
  
 Visual Basic 將 XML 常值編譯為 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供簡單的物件模型，可用於建立和操作 XML，此模型會與 (LINQ) 的語言整合式查詢妥善整合。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。  
  
 您可以在 XML 常值中內嵌 Visual Basic 運算式。 在執行時間，您的應用程式會 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 為每個常值建立一個物件，其中包含內嵌運算式的值。 這可讓您在 XML 常值內指定動態內容。 如需詳細資訊，請參閱 [XML 中的內嵌運算式](embedded-expressions-in-xml.md)。  
  
 如需 XML 常值語法和 XML 1.0 語法之間差異的詳細資訊，請參閱 [Xml 常值和 xml 1.0 規格](xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="simple-literals"></a>簡單常值  

 您可以在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic 程式碼中，藉由輸入或貼上有效的 XML 來建立物件。 XML 元素常值會傳回 <xref:System.Xml.Linq.XElement> 物件。 如需詳細資訊，請參閱 [Xml 元素常](../../../language-reference/xml-literals/xml-element-literal.md) 值和 [xml 常值和 xml 1.0 規格](xml-literals-and-the-xml-1-0-specification.md)。 下列範例會建立具有多個子項目的 XML 專案。  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 您可以使用啟動 XML 常值來建立 XML 檔 `<?xml version="1.0"?>` ，如下列範例所示。 XML 檔常值會傳回 <xref:System.Xml.Linq.XDocument> 物件。 如需詳細資訊，請參閱 [XML 檔常](../../../language-reference/xml-literals/xml-document-literal.md)值。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Visual Basic 中的 XML 常值語法與 XML 1.0 規格中的語法不相同。 如需詳細資訊，請參閱 [Xml 常值和 xml 1.0 規格](xml-literals-and-the-xml-1-0-specification.md)。  
  
## <a name="line-continuation"></a>行接續  

 XML 常值可以跨多行，而不使用行接續字元 (空格-底線輸入順序) 。 這可讓您更輕鬆地將程式碼中的 XML 常值與 XML 檔比較。  
  
 編譯器會將行接續字元視為 XML 常值的一部分。 因此，只有當它屬於物件時，才應該使用空格-底線輸入順序 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。  
  
 但是，如果內嵌運算式中有多行運算式，則需要行接續字元。 如需詳細資訊，請參閱 [XML 中的內嵌運算式](embedded-expressions-in-xml.md)。  
  
## <a name="embedding-queries-in-xml-literals"></a>在 XML 常值中嵌入查詢  

 您可以在內嵌運算式中使用查詢。 當您這樣做時，查詢所傳回的專案就會加入至 XML 元素。 這可讓您將動態內容（例如使用者查詢的結果）新增至 XML 常值。  
  
 例如，下列程式碼會使用內嵌查詢從陣列的成員建立 XML 元素 `phoneNumbers2` ，然後將這些專案加入為的子系 `contact2` 。  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>編譯器如何從 XML 常值建立物件  

 Visual Basic 編譯器會將 XML 常值轉譯為對等的函式的呼叫 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ，以建立 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 物件。 例如，Visual Basic 編譯器會將下列程式碼範例轉譯為 XML 版本指令的函式呼叫 <xref:System.Xml.Linq.XProcessingInstruction> 、呼叫、和專案的函式， <xref:System.Xml.Linq.XElement> 以及對 `<contact>` `<name>` `<phone>` <xref:System.Xml.Linq.XAttribute> `type` 屬性的函式的呼叫。 明確地說，在下列範例中，Visual Basic 編譯器會呼叫兩次的函式 <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> 。 第一個會傳遞參數的值 `type` `name` 和參數的值 `home` `value` 。 第二個也會傳遞 `type` 參數的值 `name` ，但參數的值 `work` `value` 。  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- [在 Visual Basic 中建立 XML](creating-xml.md)
- [XML 中內嵌的運算式](embedded-expressions-in-xml.md)
- [XML 文件常值](../../../language-reference/xml-literals/xml-document-literal.md)
- [XML 元素常值](../../../language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../language-reference/xml-literals/index.md)
