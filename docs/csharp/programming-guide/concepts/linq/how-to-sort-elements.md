---
title: 如何：排序項目 (C#)
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: a49b4fea8410075ca8b28f2ef7792738d063e256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319763"
---
# <a name="how-to-sort-elements-c"></a><span data-ttu-id="836ce-102">如何：排序項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="836ce-102">How to: Sort Elements (C#)</span></span>
<span data-ttu-id="836ce-103">此範例顯示如何撰寫排序其結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="836ce-103">This example shows how to write a query that sorts its results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="836ce-104">範例</span><span class="sxs-lookup"><span data-stu-id="836ce-104">Example</span></span>  
 <span data-ttu-id="836ce-105">此範例使用下列 XML 文件︰[範例 XML 檔：數值資料 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="836ce-105">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="836ce-106">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="836ce-106">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a><span data-ttu-id="836ce-107">範例</span><span class="sxs-lookup"><span data-stu-id="836ce-107">Example</span></span>  
 <span data-ttu-id="836ce-108">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="836ce-108">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="836ce-109">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="836ce-109">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="836ce-110">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的數值資料](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="836ce-110">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="836ce-111">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="836ce-111">This code produces the following output:</span></span>  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a><span data-ttu-id="836ce-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="836ce-112">See Also</span></span>  
 [<span data-ttu-id="836ce-113">排序資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="836ce-113">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
 [<span data-ttu-id="836ce-114">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="836ce-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
