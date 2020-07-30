---
title: '如何尋找子項目（XPath-LINQ to XML）（c #）'
description: 瞭解如何藉由比較 XPath 子專案座標軸與 LINQ to XML 元素方法來尋找子專案。
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 57d1a4e636e3443512020129a76cc2de7bb3f244
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301732"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="426df-103">如何尋找子項目（XPath-LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="426df-103">How to find a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="426df-104">本主題會比較 XPath 子專案座標軸與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="426df-104">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="426df-105">XPath 運算式為 `DeliveryNotes`。</span><span class="sxs-lookup"><span data-stu-id="426df-105">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="426df-106">範例</span><span class="sxs-lookup"><span data-stu-id="426df-106">Example</span></span>  
 <span data-ttu-id="426df-107">這個範例會尋找子項目 `DeliveryNotes`。</span><span class="sxs-lookup"><span data-stu-id="426df-107">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="426df-108">此範例使用下列 XML 文件︰[範例 XML 檔：多份採購訂單 (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="426df-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="426df-109">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="426df-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  