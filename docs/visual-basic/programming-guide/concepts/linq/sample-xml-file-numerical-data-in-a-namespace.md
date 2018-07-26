---
title: Namespace1 中的範例 XML 檔： 數值資料
ms.date: 07/20/2015
ms.assetid: f01cc0a1-fb55-4b42-8380-16f4be47d6f4
ms.openlocfilehash: 71ff5229d4f2342880bdf50f288355a676b78722
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244305"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="05adb-102">範例 XML 檔：命名空間中的數值資料</span><span class="sxs-lookup"><span data-stu-id="05adb-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="05adb-103">下列 XML 檔案用於 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文件的各種範例中。</span><span class="sxs-lookup"><span data-stu-id="05adb-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="05adb-104">此檔案包含數值資料以進行加總、平均和群組。</span><span class="sxs-lookup"><span data-stu-id="05adb-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="05adb-105">XML 位於命名空間中。</span><span class="sxs-lookup"><span data-stu-id="05adb-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="05adb-106">資料</span><span class="sxs-lookup"><span data-stu-id="05adb-106">Data</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05adb-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05adb-107">See Also</span></span>  
 [<span data-ttu-id="05adb-108">範例 XML 文件 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="05adb-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
