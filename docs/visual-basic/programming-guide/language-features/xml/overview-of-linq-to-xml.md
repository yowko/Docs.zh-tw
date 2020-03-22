---
title: LINQ to XML 概觀
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266894"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic 中的 LINQ to XML 概觀
Visual Basic[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]通過 XML 文本和 XML 軸屬性提供支援。 這使您能夠使用熟悉、方便的語法在 Visual Basic 代碼中使用 XML。 *XML 文本*使您能夠直接在代碼中包括 XML。 *XML 軸屬性*使您能夠訪問 XML 文本的子節點、子節點和屬性。 有關詳細資訊，請參閱視覺化基礎 中的[XML 文本概述](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)和[訪問 XML。](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]是一個記憶體中的XML程式設計API，專門用於利用語言集成查詢 （LINQ）。 儘管可以直接調用 LINQ API，但只有 Visual Basic 才能聲明 XML 文本並直接存取 XML 軸屬性。  
  
> [!NOTE]
> ASP.NET頁中的聲明性代碼不支援 XML 文本和 XML 軸屬性。 要使用 Visual Basic XML 功能，請將代碼放在ASP.NET應用程式中的代碼背後頁中。  
  
 [播放按鈕](./media/overview-of-linq-to-xml/play-video-icon-example.gif)有關相關的視頻演示，請參閱[如何開始使用 LINQ 到 XML？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)以及如何[使用 LINQ 創建 Excel 試算表？](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)
  
## <a name="creating-xml"></a>建立 XML  
 在 Visual Basic 中創建 XML 樹有兩種方法。 可以直接在代碼中聲明 XML 文本，也可以使用 LINQ API 創建樹。 這兩個進程使代碼能夠反映 XML 樹的最終結構。 例如，以下代碼示例創建一個 XML 元素：  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 有關詳細資訊，請參閱[在視覺化基本 中創建 XML。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
  
## <a name="accessing-and-navigating-xml"></a>訪問和導航 XML  
 Visual Basic 提供了用於訪問和導航 XML 結構的 XML 軸屬性。 這些屬性使您能夠通過指定 XML 子項目名稱來訪問 XML 元素和屬性。 或者，您可以顯式調用 LINQ 方法來導航和定位元素和屬性。 例如，以下代碼示例使用 XML 軸屬性來引用 XML 元素的屬性和子項目。 代碼示例使用 LINQ 查詢檢索子項目並將其輸出為 XML 元素，從而有效地執行轉換。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 有關詳細資訊，請參閱[在視覺化基本 中訪問 XML。](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
  
## <a name="xml-namespaces"></a>XML 命名空間  
 Visual Basic 使您能夠通過使用`Imports`語句將別名指定為全域 XML 命名空間。 下面的示例演示如何使用 語句`Imports`導入 XML 命名空間：  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 訪問 XML 軸屬性並為 XML 文檔和元素聲明 XML 文本時，可以使用 XML 命名空間別名。  
  
 可以使用<xref:System.Xml.Linq.XNamespace>[GetXml 命名空間運算子](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)檢索特定命名空間首碼的物件。  
  
 有關詳細資訊，請參閱[導入語句 （XML 命名空間）](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>在 XML 文本中使用 XML 命名空間  
 下面的示例演示如何創建<xref:System.Xml.Linq.XElement>使用全域命名空間`ns`的物件：  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic 編譯器將包含 XML 命名空間別名的 XML 文本轉換為等效代碼，這些代碼使用 XML 標記法使用 XML`xmlns`命名空間，以及屬性。 編譯後，上一節示例中的代碼生成與以下示例基本相同的可執行代碼：  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>在 XML 軸屬性中使用 XML 命名空間  
 在 XML 文本中聲明的 XML 命名空間不適用於 XML 軸屬性。 但是，全域命名空間可以與 XML 軸屬性一起使用。 使用冒號將 XML 命名空間首碼與本地元素名稱分開。 以下是範例：  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [Xml](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [在 Visual Basic 中存取 XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [在 Visual Basic 中管理 XML](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
