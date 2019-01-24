---
title: HOW TO：產生文字檔案，從 XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3b33f191-4abe-4419-b81b-3cb81d9a317f
ms.openlocfilehash: bd3c8b0f9faf0b465d9b0f6a5c17ceef62ddb285
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687712"
---
# <a name="how-to-generate-text-files-from-xml-visual-basic"></a><span data-ttu-id="6bf3a-102">HOW TO：產生文字檔案，從 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bf3a-102">How to: Generate Text Files from XML (Visual Basic)</span></span>
<span data-ttu-id="6bf3a-103">此範例顯示如何從 XML 檔案產生以逗號分隔的 (CSV) 檔案。</span><span class="sxs-lookup"><span data-stu-id="6bf3a-103">This example shows how to generate a comma-separated values (CSV) file from an XML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bf3a-104">範例</span><span class="sxs-lookup"><span data-stu-id="6bf3a-104">Example</span></span>  
 <span data-ttu-id="6bf3a-105">Visual Basic 版本會使用程序程式碼，來彙總成單一字串的字串集合。</span><span class="sxs-lookup"><span data-stu-id="6bf3a-105">The Visual Basic version uses procedural code to aggregate the collection of strings into a single string.</span></span>  
  
 <span data-ttu-id="6bf3a-106">此範例使用下列 XML 文件：[範例 XML 檔：客戶和訂單 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6bf3a-106">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim custOrd As XElement = XElement.Load("CustomersOrders.xml")  
Dim strCollection As IEnumerable(Of String) = _  
    From el In custOrd.<Customers>.<Customer> _  
    Select _  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}", _  
            el.@CustomerID, _  
            el.<CompanyName>.Value, _  
            el.<ContactName>.Value, _  
            el.<ContactTitle>.Value, _  
            el.<Phone>.Value, _  
            el.<FullAddress>.<Address>.Value, _  
            el.<FullAddress>.<City>.Value, _  
            el.<FullAddress>.<Region>.Value, _  
            el.<FullAddress>.<PostalCode>.Value, _  
            el.<FullAddress>.<Country>.Value, _  
            Environment.NewLine _  
        )  
Dim sb As StringBuilder = New StringBuilder()  
For Each str As String In strCollection  
    sb.Append(str)  
Next  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="6bf3a-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="6bf3a-107">This code produces the following output:</span></span>  
  
```  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bf3a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bf3a-108">See also</span></span>
- [<span data-ttu-id="6bf3a-109">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6bf3a-109">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
