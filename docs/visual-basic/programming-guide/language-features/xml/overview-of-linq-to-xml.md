---
title: Visual Basic 中的 LINQ to XML 概觀
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 91f622b9eecdd1aec8b9361493095e92a851988e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761818"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic 中的 LINQ to XML 概觀
Visual Basic 提供的支援[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]透過 XML 常值和 XML 軸屬性。 這可讓您使用熟悉、 便利的語法，在 Visual Basic 程式碼中使用的 XML。 *XML 常值*可讓您直接在您的程式碼中包含 XML。 *XML 軸屬性*讓您存取子節點、 子代節點和 XML 常值的屬性。 如需詳細資訊，請參閱 < [XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)並[Visual Basic 中的存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 記憶體中的 XML 程式設計 API，專門設計為利用[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]。 雖然您可以呼叫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Api 直接為唯一的 Visual Basic 可讓您宣告 XML 常值，並直接存取 XML 軸屬性。  
  
> [!NOTE]
>  在 ASP.NET 網頁中的宣告式程式碼中不支援 XML 常值和 XML 軸屬性。 若要使用 Visual Basic XML 功能，請將程式碼放在 ASP.NET 應用程式中的程式碼後置頁面。  
  
 ![影片連結](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo")相關的影片示範，請參閱[如何開始使用 LINQ to XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)並[How Do I 建立 Excel 試算表使用 LINQ to XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)。  
  
## <a name="creating-xml"></a>建立 XML  
 有兩種方式可在 Visual Basic 中建立 XML 樹狀結構。 您可以宣告 XML 常值直接在程式碼，或者您可以使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Api 來建立樹狀結構。 這兩個處理序啟用的程式碼，以反映最終 XML 樹狀結構的結構。 例如，下列程式碼範例會建立 XML 項目：  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中建立的 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)。  
  
## <a name="accessing-and-navigating-xml"></a>存取和瀏覽 XML  
 Visual Basic 提供存取，並瀏覽 XML 結構的 XML 軸的屬性。 這些屬性可讓您指定的 XML 子元素名稱來存取 XML 元素和屬性。 或者，您可以明確呼叫[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]瀏覽和尋找項目和屬性的方法。 比方說，下列程式碼範例會使用 XML 軸屬性來參考的屬性和子項目的 XML 項目。 此程式碼範例會使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢來擷取子項目和其輸出做為 XML 項目，有效地執行轉換。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 如需詳細資訊，請參閱 < [Visual Basic 中的存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)。  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 Visual Basic 可讓您藉由使用指定的全域 XML 命名空間的別名`Imports`陳述式。 下列範例示範如何使用`Imports`陳述式匯入 XML 命名空間：  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 當您存取 XML 軸屬性，並宣告 XML 常值的 XML 文件和項目時，您可以使用 XML 命名空間別名。  
  
 您可以擷取<xref:System.Xml.Linq.XNamespace>物件所使用的特定命名空間前置詞[GetXmlNamespace 運算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)。  
  
 如需詳細資訊，請參閱 < [Imports 陳述式 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>使用 XML 常值中的 XML 命名空間  
 下列範例示範如何建立<xref:System.Xml.Linq.XElement>會使用全域命名空間的物件`ns`:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic 編譯器將轉譯為對等的程式碼使用的 XML 表示法搭配使用 XML 命名空間，包含 XML 命名空間別名的 XML 常值`xmlns`屬性。 編譯時，如上一節的範例中的程式碼會產生基本上相同可執行檔的程式碼在下列範例所示：  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>使用 XML 命名空間中 XML 軸屬性  
 在 XML 常值中宣告的 XML 命名空間不適用於 XML 軸屬性。 不過，全域命名空間可以搭配 XML 軸屬性。 您可以使用冒號來分開的本機項目名稱的 XML 命名空間前置詞。 以下是一個範例：  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
