---
title: 如何：尋找兩個位置路徑的聯集 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 069622d3-2b58-4919-8903-710a564c0788
ms.openlocfilehash: cd98c1da2f2f8653c5db36f89a63dfdc7a7ab691
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-c"></a><span data-ttu-id="bad07-102">如何：尋找兩個位置路徑的聯集 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bad07-102">How to: Find a Union of Two Location Paths (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="bad07-103">XPath 可讓您尋找兩個 XPath 位置路徑結果的等位。</span><span class="sxs-lookup"><span data-stu-id="bad07-103">XPath allows you to find the union of the results of two XPath location paths.</span></span>  
  
 <span data-ttu-id="bad07-104">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="bad07-104">The XPath expression is:</span></span>  
  
 `//Category|//Price`  
  
 <span data-ttu-id="bad07-105">您可以使用 <xref:System.Linq.Enumerable.Concat%2A> 標準查詢運算子，達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="bad07-105">You can achieve the same results by using the <xref:System.Linq.Enumerable.Concat%2A> standard query operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bad07-106">範例</span><span class="sxs-lookup"><span data-stu-id="bad07-106">Example</span></span>  
 <span data-ttu-id="bad07-107">此範例會尋找所有 `Category` 項目與所有 `Price` 項目，然後將它們串連為單一集合。</span><span class="sxs-lookup"><span data-stu-id="bad07-107">This example finds all of the `Category` elements and all of the `Price` elements, and concatenates them into a single collection.</span></span> <span data-ttu-id="bad07-108">請注意，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢會呼叫 <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> 來排列結果。</span><span class="sxs-lookup"><span data-stu-id="bad07-108">Note that the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query calls <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> to order the results.</span></span> <span data-ttu-id="bad07-109">XPath 運算式評估的結果也是以文件的順序排列。</span><span class="sxs-lookup"><span data-stu-id="bad07-109">The results of the XPath expression evaluation are also in document order.</span></span>  
  
 <span data-ttu-id="bad07-110">此範例使用下列 XML 文件︰[範例 XML 檔：數值資料 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bad07-110">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="bad07-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bad07-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bad07-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="bad07-112">See Also</span></span>  
 [<span data-ttu-id="bad07-113">XPath 使用者適用的 LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bad07-113">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
