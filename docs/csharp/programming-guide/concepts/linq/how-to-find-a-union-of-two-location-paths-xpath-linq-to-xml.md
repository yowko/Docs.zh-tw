---
title: '如何尋找兩個位置路徑的聯集（XPath-LINQ to XML）（c #）'
description: 瞭解如何使用 XPath 運算式來尋找兩個 XPath 位置路徑的聯集。 請參閱使用範例 XML 檔案的程式碼範例。
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: 65b20fe25a0990fd82ce3bd08c3433499e728512
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303318"
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="9a94d-104">如何尋找兩個位置路徑的聯集（XPath-LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="9a94d-104">How to find a union of two location paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9a94d-105">XPath 可讓您尋找兩個 XPath 位置路徑結果的等位。</span><span class="sxs-lookup"><span data-stu-id="9a94d-105">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="9a94d-106">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="9a94d-106">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="9a94d-107">您可以使用 <xref:System.Linq.Enumerable.Concat%2A> 標準查詢運算子，達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="9a94d-107">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a94d-108">範例</span><span class="sxs-lookup"><span data-stu-id="9a94d-108">Example</span></span>  
 <span data-ttu-id="9a94d-109">此範例會尋找所有 `Category` 項目與所有 `Price` 項目，然後將它們串連為單一集合。</span><span class="sxs-lookup"><span data-stu-id="9a94d-109">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="9a94d-110">請注意，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會呼叫 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> 來排列結果。</span><span class="sxs-lookup"><span data-stu-id="9a94d-110">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="9a94d-111">XPath 運算式評估的結果也是以文件的順序排列。</span><span class="sxs-lookup"><span data-stu-id="9a94d-111">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="9a94d-112">此範例使用下列 XML 文件︰[範例 XML 檔：數值資料 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="9a94d-112">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9a94d-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9a94d-113">This example produces the following output:</span></span>  
  
```output  
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
  