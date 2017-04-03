---
title: "如何：篩選項目名稱 (LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0b6d2acd628d823caa78076ebbf9b4236a9935f3
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a>如何：篩選項目名稱 (LINQ to XML) (C#)
當您呼叫傳回 <xref:System.Xml.Linq.XElement> 之 <xref:System.Collections.Generic.IEnumerable%601> 的其中一個方法時，您可以篩選項目名稱。  
  
## <a name="example"></a>範例  
 這個範例會擷取子代 (Descendant) 的集合，而且該集合會篩選成僅包含具有指定之名稱的子代。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 此程式碼會產生下列輸出：  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 傳回 <xref:System.Xml.Linq.XElement> 集合之 <xref:System.Collections.Generic.IEnumerable%601> 的其他方法會遵循相同的模式。 其簽章類似於 <xref:System.Xml.Linq.XContainer.Elements%2A> 和 <xref:System.Xml.Linq.XContainer.Descendants%2A>。 下列是具有類似方法簽章之方法的完整清單：  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的典型採購訂單](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md)。  
  
```cs  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 此程式碼會產生下列輸出：  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINQ to XML 座標軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
