---
title: HOW TO：計算中繼值 (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 12c8a87114859ce7b47b8206acb454cdc2838470
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604319"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="6796d-102">HOW TO：計算中繼值 (C#)</span><span class="sxs-lookup"><span data-stu-id="6796d-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="6796d-103">這個範例顯示如何計算可用於排序、篩選與選取的中繼值。</span><span class="sxs-lookup"><span data-stu-id="6796d-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6796d-104">範例</span><span class="sxs-lookup"><span data-stu-id="6796d-104">Example</span></span>  
 <span data-ttu-id="6796d-105">下列範例使用 `Let` 子句。</span><span class="sxs-lookup"><span data-stu-id="6796d-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="6796d-106">此範例使用下列 XML 文件：[XML 範例檔：數值資料 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6796d-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="6796d-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="6796d-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="6796d-108">範例</span><span class="sxs-lookup"><span data-stu-id="6796d-108">Example</span></span>  
 <span data-ttu-id="6796d-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="6796d-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6796d-110">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="6796d-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="6796d-111">此範例使用下列 XML 文件：[XML 範例檔：命名空間中的數值資料](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="6796d-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="6796d-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="6796d-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="6796d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6796d-113">See also</span></span>

- [<span data-ttu-id="6796d-114">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6796d-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
