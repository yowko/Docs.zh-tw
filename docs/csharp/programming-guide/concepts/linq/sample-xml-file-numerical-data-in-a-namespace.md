---
title: XML 範例檔：命名空間中的數值資料
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: d00ad41c6703945b80dd49ff5f375a3896b43bed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702128"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="85322-102">XML 範例檔：命名空間中的數值資料</span><span class="sxs-lookup"><span data-stu-id="85322-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="85322-103">下列 XML 檔案用於 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文件的各種範例中。</span><span class="sxs-lookup"><span data-stu-id="85322-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="85322-104">此檔案包含數值資料以進行加總、平均和群組。</span><span class="sxs-lookup"><span data-stu-id="85322-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="85322-105">XML 位於命名空間中。</span><span class="sxs-lookup"><span data-stu-id="85322-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="85322-106">資料</span><span class="sxs-lookup"><span data-stu-id="85322-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85322-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85322-107">See also</span></span>

- [<span data-ttu-id="85322-108">範例 XML 文件 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="85322-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
