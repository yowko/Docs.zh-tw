---
title: 如何：尋找根項目 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: a0197a34f2e9d1b42a71d3c8cb1a4281ba495c4f
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261081"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>如何：尋找根項目 (XPath-LINQ to XML) (C#)
本主題顯示如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得根項目。  
  
 XPath 運算式為：  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>範例  
 這個範例會尋找根項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 這個範例會產生下列輸出：  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>請參閱

- [XPath 使用者適用的 LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
