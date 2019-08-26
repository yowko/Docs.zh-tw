---
title: 作法：尋找兩個位置路徑的集合聯集 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 9fc88a8784958294ba6077893a5d54110de335a0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593750"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="9c1e2-102">作法：尋找兩個位置路徑的集合聯集 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9c1e2-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9c1e2-103">XPath 可讓您尋找兩個 XPath 位置路徑結果的等位。</span><span class="sxs-lookup"><span data-stu-id="9c1e2-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="9c1e2-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="9c1e2-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="9c1e2-105">您可以使用 <xref:System.Linq.Enumerable.Concat%2A> 標準查詢運算子，達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="9c1e2-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c1e2-106">範例</span><span class="sxs-lookup"><span data-stu-id="9c1e2-106">Example</span></span>  
 <span data-ttu-id="9c1e2-107">此範例會尋找所有 `Category` 項目與所有 `Price` 項目，然後將它們串連為單一集合。</span><span class="sxs-lookup"><span data-stu-id="9c1e2-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="9c1e2-108">請注意，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會呼叫 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> 來排列結果。</span><span class="sxs-lookup"><span data-stu-id="9c1e2-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="9c1e2-109">XPath 運算式評估的結果也是以文件的順序排列。</span><span class="sxs-lookup"><span data-stu-id="9c1e2-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="9c1e2-110">此範例使用下列 XML 文件：[XML 範例檔：數值資料 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="9c1e2-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument data = XDocument.Load("Data.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    data  
    .Descendants("Category")  
    .Concat(  
        data  
        .Descendants("Price")  
    )  
    .InDocumentOrder();  
  
// XPath expression  
IEnumerable<XElement> list2 = data.XPathSelectElements("//Category|//Price");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9c1e2-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9c1e2-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  