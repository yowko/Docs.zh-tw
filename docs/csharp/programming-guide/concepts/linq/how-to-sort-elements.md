---
title: 如何對元素 （C#） 進行排序
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 7fad9fcb43905072c88a5704c56672917bfc377c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347371"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="5b6eb-102">如何對元素 （C#） 進行排序</span><span class="sxs-lookup"><span data-stu-id="5b6eb-102">How to sort elements (C#)</span></span>
<span data-ttu-id="5b6eb-103">此範例顯示如何撰寫排序其結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="5b6eb-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b6eb-104">範例</span><span class="sxs-lookup"><span data-stu-id="5b6eb-104">Example</span></span>  
 <span data-ttu-id="5b6eb-105">此範例使用下列 XML 文件︰[範例 XML 檔：數值資料 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5b6eb-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="5b6eb-106">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5b6eb-106">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="5b6eb-107">範例</span><span class="sxs-lookup"><span data-stu-id="5b6eb-107">Example</span></span>  
 <span data-ttu-id="5b6eb-108">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="5b6eb-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="5b6eb-109">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="5b6eb-109">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5b6eb-110">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的數值資料](./sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="5b6eb-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="5b6eb-111">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5b6eb-111">This code produces the following output:</span></span>  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b6eb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b6eb-112">See also</span></span>

- [<span data-ttu-id="5b6eb-113">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="5b6eb-113">Sorting Data (C#)</span></span>](./sorting-data.md)
