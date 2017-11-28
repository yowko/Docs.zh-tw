---
title: "LINQ to XML 座標軸 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 212754ca8bafb8c8e2d0dbe076b88d3818e39a68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-xml-axes-c"></a>LINQ to XML 座標軸 (C#)
建立 XML 樹狀結構，或將 XML 文件載入到 XML 樹狀結構後，您可以進行查詢以尋找項目和屬性並擷取其值。  
  
 在撰寫任何查詢之前，您必須了解 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 座標軸。 有兩種類型的座標軸方法：首先，有可以在單一 <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件或 <xref:System.Xml.Linq.XNode> 物件上呼叫的方法。 這些方法會在單一物件上運算，然後傳回 <xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute> 或 <xref:System.Xml.Linq.XNode> 物件的集合。 第二，在集合上有可運算的擴充方法，並傳回集合。 擴充方法會列舉來源集合、在集合的每個項目上呼叫適當的座標軸方法，然後串連結果。  
  
## <a name="in-this-section"></a>本章節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[LINQ to XML 座標軸概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|定義座標軸並說明如何在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的內容中使用這些座標軸。|  
|[如何：擷取項目集合 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|介紹 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。 此方法會擷取項目之子項目的集合。|  
|[如何：擷取項目的值 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|示範如何取得項目的值。|  
|[如何：篩選項目名稱 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|顯示使用座標軸時，如何在項目名稱上篩選。|  
|[如何：鏈結軸方法呼叫 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|示範如何將呼叫鏈結到座標軸方法。|  
|[如何：擷取單一子項目 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|顯示如何擷取項目的單一子項目 (假設有子項目的標記名稱)。|  
|[如何：擷取屬性集合 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|介紹 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。 這個方法會擷取項目的屬性。|  
|[如何：擷取單一屬性 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|顯示如何擷取項目的單一屬性 (假設有屬性名稱)。|  
|[如何：擷取屬性的值 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|示範如何取得屬性的值。|  
|[如何：擷取項目的表層值 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|示範如何擷取項目的表層值。|  
  
## <a name="see-also"></a>另請參閱  
 [擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [程式設計手冊 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
