---
title: 作法：排序項目 (C#)
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 074428413fa57d8f0e5ae94970c2aeeeb9e4cc7c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592464"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="f43aa-102">作法：排序項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="f43aa-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="f43aa-103">此範例顯示如何撰寫排序其結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="f43aa-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f43aa-104">範例</span><span class="sxs-lookup"><span data-stu-id="f43aa-104">Example</span></span>  
 <span data-ttu-id="f43aa-105">此範例使用下列 XML 文件：[XML 範例檔：數值資料 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="f43aa-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f43aa-106">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f43aa-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="f43aa-107">範例</span><span class="sxs-lookup"><span data-stu-id="f43aa-107">Example</span></span>  
 <span data-ttu-id="f43aa-108">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="f43aa-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="f43aa-109">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="f43aa-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f43aa-110">此範例使用下列 XML 文件：[XML 範例檔：命名空間中的數值資料](./sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="f43aa-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f43aa-111">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="f43aa-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="f43aa-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f43aa-112">See also</span></span>

- [<span data-ttu-id="f43aa-113">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="f43aa-113">Sorting Data (C#)</span></span>](./sorting-data.md)
