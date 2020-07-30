---
title: '如何尋找子項目的清單（XPath-LINQ to XML）（c #）'
description: 瞭解如何使用 XPath 運算式尋找子項目的清單。 檢查程式碼範例，以尋找特定專案的所有子專案。
ms.date: 07/20/2015
ms.assetid: 7c589dd8-f680-4cdb-9d6a-78d57e2555e8
ms.openlocfilehash: a3025aca7fb1055acd55e5ce98914d8359ebe4b7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301719"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-c"></a>如何尋找子項目的清單（XPath-LINQ to XML）（c #）
本主題會比較 XPath 子專案座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 座標軸。  
  
 XPath 運算式為：`./*`  
  
## <a name="example"></a>範例  
 此範例會尋找 `Address` 項目的所有子項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder").Element("Address");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Elements();  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("./*");  
  
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
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
