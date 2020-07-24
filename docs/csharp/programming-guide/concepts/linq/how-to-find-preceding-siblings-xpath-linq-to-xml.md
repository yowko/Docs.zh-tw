---
title: '如何尋找先前的同級（XPath-LINQ to XML）（c #）'
description: '這個 c # 範例會比較 XPath 先前的-同輩軸與 LINQ to XML 子 System.xml.linq.xnode>. System.xml.linq.xnode.elementsbeforeself 軸。'
ms.date: 07/20/2015
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
ms.openlocfilehash: 4150c94fe1e30e7a72bb53b4c6c12481ee0bad19
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103465"
---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>如何尋找先前的同級（XPath-LINQ to XML）（c #）
這個主題會比較 XPath `preceding-sibling` 座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 子系 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 座標軸。  
  
 XPath 運算式為：  
  
 `preceding-sibling::*`  
  
 請注意，<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 和 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> 的結果都會以文件的順序排列。  
  
## <a name="example"></a>範例  
 下列範例會尋找 `FullAddress` 項目，然後使用 `preceding-sibling` 座標軸擷取先前的項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：客戶和訂單 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)。  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
