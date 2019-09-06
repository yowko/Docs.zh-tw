---
title: 作法：尋找子系項目 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
ms.openlocfilehash: 602e04eaf5dff9f95a495daea9606afb8c162bb2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253716"
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a>作法：尋找子系項目 (XPath-LINQ to XML) (C#)
本主題顯示如何利用特定名稱取得子代項目。  
  
 XPath 運算式為 `//Name`。  
  
## <a name="example"></a>範例  
 此範例會尋找名稱為 `Name` 的所有子代。  
  
 此範例使用下列 XML 文件：[XML 範例檔：多個訂購單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
