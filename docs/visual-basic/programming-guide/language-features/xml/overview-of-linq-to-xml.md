---
title: LINQ to XML 概觀
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 4ec1c96bdca96a6e9b68b240c147b70536514d85
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91099186"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic 中的 LINQ to XML 概觀

Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 透過 xml 常值和 xml 軸屬性提供支援。 這可讓您使用熟悉且方便的語法，在 Visual Basic 程式碼中使用 XML。 *Xml 常* 值可讓您直接在程式碼中包含 xml。 *Xml 軸屬性* 可讓您存取子節點、子系節點，以及 xml 常值的屬性。 如需詳細資訊，請參閱 [Xml 常值總覽](xml-literals-overview.md) 和 [存取 VISUAL BASIC 中的 xml](accessing-xml.md)。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 是記憶體中的 XML 程式設計 API，專為利用 (LINQ) 的語言整合式查詢所設計。 雖然您可以直接呼叫 LINQ Api，但只有 Visual Basic 可讓您宣告 XML 常值，並直接存取 XML 軸屬性。  
  
> [!NOTE]
> ASP.NET 網頁中的宣告式程式碼不支援 XML 常值和 XML 軸屬性。 若要使用 Visual Basic XML 功能，請將您的程式碼放在 ASP.NET 應用程式的程式碼後置頁面中。  
  
 [[播放] 按鈕](./media/overview-of-linq-to-xml/play-video-icon-example.gif)如需相關的影片示範，請參閱[如何使用 LINQ to XML 開始？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)以及[如何使用 LINQ to XML 建立 Excel 試算表？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)。
  
## <a name="creating-xml"></a>建立 XML  

 有兩種方式可以在 Visual Basic 中建立 XML 樹狀結構。 您可以直接在程式碼中宣告 XML 常值，也可以使用 LINQ Api 來建立樹狀結構。 這兩個進程都可讓程式碼反映 XML 樹狀結構的最終結構。 例如，下列程式碼範例會建立 XML 元素：  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 如需詳細資訊，請參閱 [在 Visual Basic 中建立 XML](creating-xml.md)。  
  
## <a name="accessing-and-navigating-xml"></a>存取和流覽 XML  

 Visual Basic 提供 XML 軸屬性來存取和流覽 XML 結構。 這些屬性可讓您藉由指定 XML 子項目名稱，來存取 XML 專案和屬性。 或者，您也可以明確地呼叫 LINQ 方法，以流覽和尋找元素和屬性。 例如，下列程式碼範例會使用 XML 軸屬性來參考 XML 專案的屬性和子項目。 程式碼範例會使用 LINQ 查詢來取出子專案，並將它們輸出為 XML 專案，以有效地執行轉換。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 如需詳細資訊，請參閱 [存取 Visual Basic 中的 XML](accessing-xml.md)。  
  
## <a name="xml-namespaces"></a>XML 命名空間  

 Visual Basic 可讓您使用語句來指定全域 XML 命名空間的別名 `Imports` 。 下列範例顯示如何使用 `Imports` 語句匯入 XML 命名空間：  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 當您存取 XML 軸屬性，並宣告 xml 檔和元素的 XML 常值時，您可以使用 XML 命名空間別名。  
  
 您可以 <xref:System.Xml.Linq.XNamespace> 使用 [GetXmlNamespace 運算子](../../../language-reference/operators/getxmlnamespace-operator.md)，來取得特定命名空間前置詞的物件。  
  
 如需詳細資訊，請參閱 [ (XML 命名空間) 的 Imports 語句 ](../../../language-reference/statements/imports-statement-xml-namespace.md)。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>使用 xml 常值中的 XML 命名空間  

 下列範例顯示如何建立 <xref:System.Xml.Linq.XElement> 使用全域命名空間的物件 `ns` ：  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic 編譯器會將包含 XML 命名空間別名的 XML 常值轉譯為對等的程式碼，該程式碼使用 xml 標記法搭配屬性來使用 xml 命名空間 `xmlns` 。 編譯時，上一節範例中的程式碼基本上會產生與下列範例相同的可執行程式碼：  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>在 XML 軸屬性中使用 XML 命名空間  

 Xml 常值中宣告的 XML 命名空間不能用於 XML 軸屬性。 不過，全域命名空間可以與 XML 軸屬性搭配使用。 使用冒號來分隔 XML 命名空間前置詞與本機專案名稱。 以下是範例：  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [XML](index.md)
- [在 Visual Basic 中建立 XML](creating-xml.md)
- [在 Visual Basic 中存取 XML](accessing-xml.md)
- [在 Visual Basic 中管理 XML](manipulating-xml.md)
