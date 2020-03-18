---
title: 如何查找根項目（XPath-LINQ 到 XML）（C#）
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1c5526f436b5b9d88ca359ef7e0fc04c5c3cf43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345953"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="00c5d-102">如何查找根項目（XPath-LINQ 到 XML）（C#）</span><span class="sxs-lookup"><span data-stu-id="00c5d-102">How to find the root element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="00c5d-103">本主題顯示如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得根項目。</span><span class="sxs-lookup"><span data-stu-id="00c5d-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="00c5d-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="00c5d-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="00c5d-105">範例</span><span class="sxs-lookup"><span data-stu-id="00c5d-105">Example</span></span>  
 <span data-ttu-id="00c5d-106">這個範例會尋找根項目。</span><span class="sxs-lookup"><span data-stu-id="00c5d-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="00c5d-107">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="00c5d-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="00c5d-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="00c5d-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
