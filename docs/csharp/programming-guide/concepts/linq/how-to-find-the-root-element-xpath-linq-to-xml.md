---
title: 作法：尋找根項目 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1fea4cc630dd708a86a0f0595ac727f8b8fa40af
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593387"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="95f72-102">作法：尋找根項目 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="95f72-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="95f72-103">本主題顯示如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得根項目。</span><span class="sxs-lookup"><span data-stu-id="95f72-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="95f72-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="95f72-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="95f72-105">範例</span><span class="sxs-lookup"><span data-stu-id="95f72-105">Example</span></span>  
 <span data-ttu-id="95f72-106">這個範例會尋找根項目。</span><span class="sxs-lookup"><span data-stu-id="95f72-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="95f72-107">此範例使用下列 XML 文件：[XML 範例檔：多個訂購單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="95f72-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="95f72-108">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="95f72-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
