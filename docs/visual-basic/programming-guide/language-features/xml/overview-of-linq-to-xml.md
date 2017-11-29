---
title: "Visual Basic 中的 LINQ to XML 概觀"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: baa60939654857f40d323b6412978ed4ff918177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic 中的 LINQ to XML 概觀
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供的支援[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]透過 XML 常值和 XML 軸屬性。 這可讓您使用熟悉且方便的語法使用中的 XML 程式[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式碼。 *XML 常值*可讓您直接在您的程式碼中包含 XML。 *XML 軸屬性*讓您存取子節點、 子代節點和 XML 常值的屬性。 如需詳細資訊，請參閱[XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)和[存取 Visual Basic 中的 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]為記憶體中 XML 程式設計 API 專門設計為利用[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]。 雖然您可以呼叫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Api 直接只[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]可讓您宣告 XML 常值及直接存取 XML 軸屬性。  
  
> [!NOTE]
>  ASP.NET 網頁中的宣告式程式碼中不支援 XML 常值和 XML 軸屬性。 若要使用 Visual Basic XML 功能，將程式碼放在 ASP.NET 應用程式中的程式碼後置頁面。  
  
 ![影片連結](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")相關的影片示範，請參閱[如何開始使用 LINQ to XML？](http://go.microsoft.com/fwlink/?LinkId=143034)和[如何建立 Excel 試算表使用 LINQ to XML？](http://go.microsoft.com/fwlink/?LinkId=143536)。  
  
## <a name="creating-xml"></a>建立 XML  
 有兩種方式來建立 XML 樹狀結構中的[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。 您可以宣告 XML 常值，直接在程式碼中，或者您可以使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Api 來建立樹狀結構。 這兩個程序允許以反映最終的 XML 樹狀結構的程式碼。 例如，下列程式碼範例會建立 XML 項目：  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 如需詳細資訊，請參閱[在 Visual Basic 中建立的 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)。  
  
## <a name="accessing-and-navigating-xml"></a>存取和巡覽 XML  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供 XML 軸屬性，可存取及巡覽 XML 結構。 這些屬性可讓您指定的 XML 子元素名稱來存取 XML 元素和屬性。 或者，您可以明確地呼叫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]巡覽及尋找項目和屬性的方法。 例如，下列的程式碼範例會使用 XML 軸屬性來參考的屬性和子項目的 XML 項目。 此程式碼範例會使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢來擷取子項目和其輸出為 XML 項目，有效地執行轉換。  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 如需詳細資訊，請參閱[存取 Visual Basic 中的 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]可讓您使用指定的全域 XML 命名空間別名`Imports`陳述式。 下列範例示範如何使用`Imports`陳述式匯入的 XML 命名空間：  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 當您存取 XML 軸屬性，並宣告 XML 常值的 XML 文件和項目時，您可以使用 XML 命名空間別名。  
  
 您可以擷取<xref:System.Xml.Linq.XNamespace>物件使用的特定命名空間前置詞[GetXmlNamespace 運算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)。  
  
 如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>使用 XML 常值中的 XML 命名空間  
 下列範例示範如何建立<xref:System.Xml.Linq.XElement>使用全域命名空間的物件`ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器將轉譯 XML 常值到對等程式碼中使用的 XML 表示法搭配使用 XML 命名空間，包含 XML 命名空間別名`xmlns`屬性。 編譯時，在上一節的範例程式碼會產生基本上相同可執行程式碼，如下列範例：  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML 軸屬性中使用 XML 命名空間  
 在 XML 常值中宣告的 XML 命名空間不適用於 XML 軸屬性。 不過，全域命名空間可以搭配 XML 軸屬性。 您可以使用冒號來分開的本機項目名稱的 XML 命名空間前置詞。 以下是一個範例：  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
