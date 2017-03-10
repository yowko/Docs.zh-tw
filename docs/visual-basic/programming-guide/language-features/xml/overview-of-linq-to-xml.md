---
title: "Overview of LINQ to XML in Visual Basic | Microsoft Docs"
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
  - "LINQ to XML [Visual Basic], about LINQ to XML"
  - "LINQ [Visual Basic], LINQ to XML"
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Overview of LINQ to XML in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會透過 XML 常值 \(Literal\) 和 XML 軸屬性，提供 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 支援。  這可讓您使用既熟悉又方便的語法，在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式碼中處理 XML。「*XML 常值*」\(XML Literal\) 可讓您在程式碼中直接包含 XML。  「*XML 軸屬性*」\(XML Axis Property\) 可讓您存取 XML 常值的子節點、子代 \(Descendant\) 節點和屬性。  如需詳細資訊，請參閱[XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)和[Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] 是特別為了利用 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] 所設計的記憶體中 XML 程式設計 API。  雖然您可以直接呼叫 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] API，但只有 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可讓您宣告 XML 常值及直接存取 XML 軸屬性。  
  
> [!NOTE]
>  ASP.NET 網頁的宣告式程式碼中不支援 XML 常值和 XML 軸屬性。  若要使用 Visual Basic XML 功能，請將您的程式碼放在 ASP.NET 應用程式的程式碼後置頁面中。  
  
 ![視訊的連結](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") 如需相關示範影片，請參閱[如何開始使用 LINQ to XML？](http://go.microsoft.com/fwlink/?LinkId=143034) \(英文\) 以及[如何使用 LINQ to XML 建立 Excel 試算表？](http://go.microsoft.com/fwlink/?LinkId=143536) \(英文\)。  
  
## 建立 XML  
 有兩種方式可以在 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中建立 XML 樹狀結構。  您可以直接在程式碼中宣告 XML 常值，也可以使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] API 建立樹狀結構。  這兩個處理序都可讓程式碼反映出 XML 樹狀結構的最終結構。  例如，下列程式碼範例會建立 XML 項目：  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_1.vb)]  
  
 如需詳細資訊，請參閱[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)。  
  
## 存取和巡覽 XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 所提供的 XML 軸屬性可用以存取和巡覽 XML 結構。  這些屬性可讓您經由指定 XML 子項目名稱，存取 XML 項目和屬性。  此外，您也可以明確地呼叫用以巡覽及尋找項目和屬性的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 方法。  例如，下列程式碼範例會使用 XML 軸屬性來參考 XML 項目的屬性和子項目。  此程式碼範例會使用 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] 查詢來擷取子項目並將其輸出為 XML 項目，也就是有效地執行轉換。  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_2.vb)]  
  
 如需詳細資訊，請參閱[Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
## XML 命名空間  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 可讓您使用 `Imports` 陳述式，指定全域 XML 命名空間的別名。  下列範例顯示如何使用 `Imports` 陳述式來匯入 XML 命名空間：  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_3.vb)]  
  
 當您存取 XML 軸屬性並宣告 XML 文件和項目的 XML 常值時，可以使用 XML 命名空間別名。  
  
 您可以使用 [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)來擷取特定命名空間前置字元的 <xref:System.Xml.Linq.XNamespace> 物件。  
  
 如需詳細資訊，請參閱 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
### 在 XML 常值中使用 XML 命名空間  
 下列範例顯示如何建立會使用全域命名空間 `ns` 的 <xref:System.Xml.Linq.XElement> 物件：  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_4.vb)]  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會使用 `xmlns` 屬性，將包含 XML 命名空間別名的 XML 常值轉譯成採用 XML 標記法的同等程式碼，以便使用 XML 命名空間。  編譯之後，上一節範例中的程式碼基本上會產生與下列範例相同的可執行程式碼：  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_5.vb)]  
  
### 在 XML 軸屬性中使用 XML 命名空間  
 在 XML 常值中宣告的 XML 命名空間無法用於 XML 軸屬性中。  但是，全域命名空間則可用於 XML 軸屬性。  使用冒號來分隔 XML 命名空間前置字元與區域項目名稱。  下列為範例：  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/overview-of-linq-to-xml_6.vb)]  
  
## 請參閱  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)