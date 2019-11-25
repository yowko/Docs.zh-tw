---
title: LINQ to XML 軸
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 73c5325c23c4724a28a123af5c2f8c25b2fd02de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352025"
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML Axes (Visual Basic)
建立 XML 樹狀結構，或將 XML 文件載入到 XML 樹狀結構後，您可以進行查詢以尋找項目和屬性並擷取其值。  
  
 在撰寫任何查詢之前，您必須了解 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 座標軸。 有兩種類型的座標軸方法：首先，有可以在單一 <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件或 <xref:System.Xml.Linq.XNode> 物件上呼叫的方法。 這些方法會在單一物件上運算，然後傳回 <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute> 或 <xref:System.Xml.Linq.XNode> 物件的集合。 第二，在集合上有可運算的擴充方法，並傳回集合。 擴充方法會列舉來源集合、在集合的每個項目上呼叫適當的座標軸方法，然後串連結果。  
  
## <a name="in-this-section"></a>本章節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[LINQ to XML Axes Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|定義座標軸並說明如何在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的內容中使用這些座標軸。|  
|[How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|介紹 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。 此方法會擷取項目之子項目的集合。|  
|[How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|示範如何取得項目的值。|  
|[How to: Filter on Element Names (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|顯示使用座標軸時，如何在項目名稱上篩選。|  
|[How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|示範如何將呼叫鏈結到座標軸方法。|  
|[How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|顯示如何擷取項目的單一子項目 (假設有子項目的標記名稱)。|  
|[How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|介紹 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。 這個方法會擷取項目的屬性。|  
|[How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|顯示如何擷取項目的單一屬性 (假設有屬性名稱)。|  
|[How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|示範如何取得屬性的值。|  
|[How to: Retrieve the Shallow Value of an Element (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|示範如何擷取項目的表層值。|  
|[Language-Integrated Axes in Visual Basic (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Summarizes the Visual Basic integrated axes.|  
  
## <a name="see-also"></a>請參閱

- [Programming Guide (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
