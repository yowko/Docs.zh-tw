---
title: "基本查詢 (LINQ to XML) (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: d333bb7d-20c1-448a-95b7-e5ba07915744
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e3879dfe92f158c545a1f4a42c6bfc35aae06f3c
ms.lasthandoff: 03/13/2017


---
# <a name="basic-queries-linq-to-xml-c"></a>基本查詢 (LINQ to XML) (C#)
本節提供 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 基本查詢的範例。  
  
## <a name="in-this-section"></a>本章節內容  
  
|主題|說明|  
|-----------|-----------------|  
|[如何：尋找具有特定屬性的項目 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md)|顯示如何尋找其屬性具有特定值的特定項目。|  
|[如何：尋找具有特定子項目的項目 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-child-element.md)|顯示如何尋找其子項目具有特定值的特定項目。|  
|[查詢 XDocument 與查詢 XElement (C#)](../../../../csharp/programming-guide/concepts/linq/querying-an-xdocument-vs-querying-an-xelement.md)|說明在根目錄為 <xref:System.Xml.Linq.XElement> 之 XML 樹狀結構上撰寫查詢與在根目錄為 <xref:System.Xml.Linq.XDocument> 之 XML 樹狀結構上撰寫查詢的差異。|  
|[如何：尋找具有特定項目名稱的子系 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-with-a-specific-element-name.md)|顯示如何尋找具有特定名稱之項目的所有子代。 這個範例使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸。|  
|[如何：使用 Descendants 方法尋找單一子系 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-single-descendant-using-the-descendants-method.md)|顯示如何使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 座標軸方法來尋找單一的唯一具名項目。|  
|[如何：撰寫具有複雜篩選功能的查詢 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md)|顯示如何使用更複雜的篩選條件撰寫查詢。|  
|[如何：篩選選擇性項目 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-optional-element.md)|顯示如何在不規則組織的樹狀中尋找節點。|  
|[如何：在命名空間中尋找所有節點 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-all-nodes-in-a-namespace.md)|顯示如何尋找特定命名空間中的所有節點。|  
|[如何：排序項目 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-elements.md)|顯示如何撰寫排序其結果的查詢。|  
|[如何：根據多個索引鍵排序項目 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md)|顯示如何在多個索引鍵上排序。|  
|[如何：計算中繼值 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-calculate-intermediate-values.md)|顯示如何使用 `Let` 子句來計算 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢中的中繼值。|  
|[如何：撰寫可根據內容尋找項目的查詢 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-query-that-finds-elements-based-on-context.md)|顯示如何根據樹狀中的其他項目選取項目。|  
|[如何：偵錯空的查詢結果集 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md)|針對預設命名空間中的 XML 偵錯查詢時，顯示適當的修正。|  
  
## <a name="see-also"></a>另請參閱  
 [查詢 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
