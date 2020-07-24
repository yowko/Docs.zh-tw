---
title: '如何尋找根項目（XPath-LINQ to XML）（c #）'
description: '這個 c # 範例會比較 XPath 與 LINQ to XML，以瞭解如何取得範例 XML 檔的根項目。'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 220899823210c5cd6e9834541ca87e4d8394b4ff
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105191"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="f8672-103">如何尋找根項目（XPath-LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="f8672-103">How to find the root element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="f8672-104">本主題顯示如何利用 XPath 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 取得根項目。</span><span class="sxs-lookup"><span data-stu-id="f8672-104">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="f8672-105">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="f8672-105">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="f8672-106">範例</span><span class="sxs-lookup"><span data-stu-id="f8672-106">Example</span></span>  
 <span data-ttu-id="f8672-107">這個範例會尋找根項目。</span><span class="sxs-lookup"><span data-stu-id="f8672-107">This example finds the root element.</span></span>  
  
 <span data-ttu-id="f8672-108">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="f8672-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="f8672-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f8672-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
