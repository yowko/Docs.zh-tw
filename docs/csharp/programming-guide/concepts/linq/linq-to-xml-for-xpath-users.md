---
title: XPath 使用者適用的 LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 91774511-1dca-4f06-ac0b-913746f104fe
ms.openlocfilehash: e55e763db2169b704b0b1fcc72e21d9e339b01f6
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199117"
---
# <a name="linq-to-xml-for-xpath-users-c"></a>XPath 使用者適用的 LINQ to XML (C#)
這組主題顯示多個 XPath 運算式及其 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 對等用法。  
  
 所有範例都使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> 的擴充方法所提供的 XPath 功能。 這些範例會同時執行 XPath 運算式與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 運算式。 接著，每個範例都會比較兩個查詢的結果，以驗證 XPath 運算式在功能上等同於 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢。 由於兩種類型的查詢都會從相同的 XML 樹狀結構傳回節點，因此會使用參考識別進行查詢結果比較。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[XPath 和 LINQ to XML 的比較](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|提供 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 之間的相同處與相異處概觀。|  
|[如何：尋找子項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|比較 XPath 子項目座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> 方法。<br /><br /> 相關聯的 XPath 運算式為：`"DeliveryNotes"`。|  
|[如何：尋找子項目清單 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|比較 XPath 子項目座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。<br /><br /> 相關聯的 XPath 運算式為：`"./*"`|  
|[如何：尋找根項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|比較如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得根項目。<br /><br /> 相關聯的 XPath 運算式為：`"/PurchaseOrders"`|  
|[如何：尋找子系項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|比較如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得具有特定名稱的子代項目。<br /><br /> 相關聯的 XPath 運算式為：`"//Name"`|  
|[如何：篩選屬性 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|比較如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得具有指定之名稱以及具有指定值之屬性的子代項目。<br /><br /> 相關聯的 XPath 運算式為：`".//Address[@Type='Shipping']"`|  
|[如何：尋找相關項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|比較如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得在另一個項目值參考的屬性上選取的項目。<br /><br /> 相關聯的 XPath 運算式為：`".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[如何：尋找命名空間中的項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace-xpath-linq-to-xml.md)|比較 XPath <xref:System.Xml.XmlNamespaceManager> 類別的用法與 <xref:System.Xml.Linq.XName> 類別的 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> 屬性，以便與 XML 命名空間搭配使用。<br /><br /> 相關聯的 XPath 運算式為：`"./aw:*"`|  
|[如何：尋找前面同層級項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|比較 XPath `preceding-sibling` 座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 子系 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 座標軸。<br /><br /> 相關聯的 XPath 運算式為：`"preceding-sibling::*"`|  
|[如何：尋找子項目的子系 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|比較如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得具有特定名稱之子項目的子代項目。<br /><br /> 相關聯的 XPath 運算式為：`"./Paragraph//Text/text()"`|  
|[如何：尋找兩個位置路徑的聯集 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml.md)|比較等位運算子 <code>&#124;</code> 在 XPath 中的用法與 <xref:System.Linq.Enumerable.Concat%2A> 標準查詢運算子在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的用法。<br /><br /> 相關聯的 XPath 運算式為：<code>"//Category&#124;//Price"</code>|  
|[如何：尋找同層級節點 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|比較如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 尋找具有特定名稱之節點的所有同層級。<br /><br /> 相關聯的 XPath 運算式為：`"../Book"`|  
|[如何：尋找父代的屬性 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|比較如何使用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 導覽到父項目並尋找相關聯的屬性。<br /><br /> 相關聯的 XPath 運算式為：`"../@id"`|  
|[如何：利用特定名稱尋找同層級的屬性 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml.md)|比較如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 尋找內容節點之同層級的特定屬性。<br /><br /> 相關聯的 XPath 運算式為：`"``../Book/@id``"`|  
|[如何：尋找具有特定屬性的項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml.md)|比較如何使用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 尋找包含特定屬性的所有項目。<br /><br /> 相關聯的 XPath 運算式為：`"./*[@Select]"`|  
|[如何：根據位置尋找子項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position-xpath-linq-to-xml.md)|比較如何使用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，根據其相對位置尋找項目。<br /><br /> 相關聯的 XPath 運算式為：`"Test[position() >= 2 and position() <= 4]"`|  
|[如何：尋找正前面的同層級項目 (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|比較如何使用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 尋找節點正前面的同層級。<br /><br /> 相關聯的 XPath 運算式為：`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Xml.XPath?displayProperty=nameWithType>  
 [查詢 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)  
 [使用 XPath 資料模型處理 XML 資料](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
