---
title: 如何尋找根項目（XPath-LINQ to XML）（C#）
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1c5526f436b5b9d88ca359ef7e0fc04c5c3cf43c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345953"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>如何尋找根項目（XPath-LINQ to XML）（C#）
本主題顯示如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得根項目。  
  
 XPath 運算式為：  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>範例  
 這個範例會尋找根項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：多份採購單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。  
  
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
  
```output  
Results are identical  
PurchaseOrders  
```  
