---
title: 如何計算中繼值（C#）
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141443"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="df29e-102">如何計算中繼值（C#）</span><span class="sxs-lookup"><span data-stu-id="df29e-102">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="df29e-103">這個範例顯示如何計算可用於排序、篩選與選取的中繼值。</span><span class="sxs-lookup"><span data-stu-id="df29e-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df29e-104">範例</span><span class="sxs-lookup"><span data-stu-id="df29e-104">Example</span></span>  
 <span data-ttu-id="df29e-105">下列範例使用 `Let` 子句。</span><span class="sxs-lookup"><span data-stu-id="df29e-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="df29e-106">此範例使用下列 XML 文件︰[範例 XML 檔：數值資料 (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="df29e-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="df29e-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="df29e-107">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="df29e-108">範例</span><span class="sxs-lookup"><span data-stu-id="df29e-108">Example</span></span>  
 <span data-ttu-id="df29e-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="df29e-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="df29e-110">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="df29e-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="df29e-111">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的數值資料](./sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="df29e-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="df29e-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="df29e-112">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
