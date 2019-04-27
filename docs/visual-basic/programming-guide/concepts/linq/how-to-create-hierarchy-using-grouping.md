---
title: HOW TO：使用群組 (Visual Basic) 建立階層
ms.date: 07/20/2015
ms.assetid: 4eb3ca6b-1aed-43de-b8b9-41c769c993f8
ms.openlocfilehash: dea189d9d689cfba661fd84cb52f8e6658935a30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855409"
---
# <a name="how-to-create-hierarchy-using-grouping-visual-basic"></a><span data-ttu-id="21a7f-102">HOW TO：使用群組 (Visual Basic) 建立階層</span><span class="sxs-lookup"><span data-stu-id="21a7f-102">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>
<span data-ttu-id="21a7f-103">此範例顯示如何群組資料，然後根據該群組產生 XML。</span><span class="sxs-lookup"><span data-stu-id="21a7f-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21a7f-104">範例</span><span class="sxs-lookup"><span data-stu-id="21a7f-104">Example</span></span>  
 <span data-ttu-id="21a7f-105">此範例會先按照類別群組資料，然後產生 XML 階層會反映群組的新 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="21a7f-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="21a7f-106">此範例使用下列 XML 文件：[XML 範例檔：數值資料 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="21a7f-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim doc As XElement = XElement.Load("Data.xml")  
Dim newData As XElement = _  
    <Root>  
        <%= _  
            From data In doc.<Data> _  
            Group By category = data.<Category>(0).Value _  
            Into groupedData = Group _  
            Select <Group ID=<%= category %>>  
                       <%= _  
                           From g In groupedData _  
                           Select _  
                           <Data>  
                               <%= g.<Quantity>(0) %>  
                               <%= g.<Price>(0) %>  
                           </Data> _  
                       %>  
                   </Group> _  
        %>  
    </Root>  
Console.WriteLine(newData)  
```  
  
 <span data-ttu-id="21a7f-107">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="21a7f-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Group ID="A">  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>24.50</Price>  
    </Data>  
    <Data>  
      <Quantity>5</Quantity>  
      <Price>4.95</Price>  
    </Data>  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>66.00</Price>  
    </Data>  
    <Data>  
      <Quantity>15</Quantity>  
      <Price>29.00</Price>  
    </Data>  
  </Group>  
  <Group ID="B">  
    <Data>  
      <Quantity>1</Quantity>  
      <Price>89.99</Price>  
    </Data>  
    <Data>  
      <Quantity>10</Quantity>  
      <Price>.99</Price>  
    </Data>  
    <Data>  
      <Quantity>8</Quantity>  
      <Price>6.99</Price>  
    </Data>  
  </Group>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21a7f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21a7f-108">See also</span></span>

- [<span data-ttu-id="21a7f-109">進階查詢技術 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21a7f-109">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
