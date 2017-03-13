---
title: "XML Literals Overview (Visual Basic) | Microsoft Docs"
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
  - "XML literals [Visual Basic], about XML literals"
  - "declaring XML literals [Visual Basic]"
  - "LINQ to XML [Visual Basic], XML literals"
  - "literals [Visual Basic], XML"
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# XML Literals Overview (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

「*XML 常值*」\(XML Literal\) 可供您直接將 XML 加入 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼中。XML 常值語法代表 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件，類似 XML 1.0 語法。因為您的程式碼會具有與最終 XML 相同的結構，因此很容易以程式設計的方式建立 XML 項目及文件。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會將 XML 常值編譯成 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件。  [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)]提供用於建立和操作 XML 的簡單物件模型，此模式可與 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] 完美整合。  如需詳細資訊，請參閱 <xref:System.Xml.Linq.XElement>。  
  
 您可以將 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 運算式內嵌至 XML 常值中。  在執行階段，您的應用程式會為每個常值各建立一個 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件，其中納入內嵌運算式的值。  這樣可讓您在 XML 常值中指定動態內容。  如需詳細資訊，請參閱 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 如需 XML 常值語法和 XML 1.0 語法之間差異的詳細資訊，請參閱 [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## 簡單常值  
 您可以在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼中建立 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件，只需輸入或貼上有效的 XML 即可。  XML 項目常值會傳回 <xref:System.Xml.Linq.XElement> 物件。  如需詳細資訊，請參閱 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)和 [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  下列範例會建立具有數個子項目的 XML 項目。  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 您可以從 `<?xml version="1.0"?>` 開始建立 XML 常值，即可建立 XML 文件，如下列範例所示。  XML 文件常值會傳回 <xref:System.Xml.Linq.XDocument> 物件。  如需詳細資訊，請參閱 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中的 XML 常值語法與 XML 1.0 規格中的語法不盡相同。  如需詳細資訊，請參閱 [XML Literals and the XML 1.0 Specification](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)。  
  
## 行接續字元  
 XML 常值可以在不需使用行接續字元 \(空格\-底線\-ENTER 鍵順序\) 的情況下跨越數行。  如此有利於比對程式碼中的 XML 常值與 XML 文件。  
  
 編譯器 \(Compiler\) 會將行接續字元視為 XML 常值的一部分。  因此，只有在空格\-底線\-ENTER 鍵順序適用於 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件時，才應使用該順序。  
  
 不過，如果在內嵌運算式中有多行運算式，這時就需使用行接續字元。  如需詳細資訊，請參閱 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
## XML 常值中的內嵌查詢  
 您可以以內嵌運算式的形式使用查詢。  執行這項作業時，查詢所傳回的項目會加入至 XML 項目。  這樣一來，您便能將動態內容 \(例如使用者查詢的結果\) 加入至 XML 常值。  
  
 例如，下列程式碼使用內嵌查詢，從 `phoneNumbers2` 陣列的成員建立 XML 項目，然後再將這些項目加入成為 `contact2` 的子系。  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## 編譯器如何從 XML 常值建立物件  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將 XML 常值轉譯為對對等 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 建構函式的呼叫，以建置 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 物件。  例如，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將下列程式碼範例轉譯為呼叫 <xref:System.Xml.Linq.XProcessingInstruction> 建構函式以建置 XML 版本指示、呼叫 <xref:System.Xml.Linq.XElement> 建構函式以建置 `<contact>`、`<name>` 和 `<phone>`，以及呼叫 <xref:System.Xml.Linq.XAttribute> 建構函式以建置 `type` 屬性。  更精確地說，以下列範例中提供的屬性而言，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會呼叫 <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> 建構函式兩次。  第一次呼叫會傳遞 `type` 值做為 `name` 參數，並傳遞 `home` 值做為 `value` 參數。  第二次呼叫同樣會傳遞 `type` 值做為 `name` 參數，但會傳遞 `work` 值做為 `value` 參數。  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement>   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)