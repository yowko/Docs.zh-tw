---
title: "範例 XML 檔：命名空間中的數值資料3 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 62f46f216a08d9eba425adc60354cf6fa7325c96
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="bba42-102">範例 XML 檔：命名空間中的數值資料</span><span class="sxs-lookup"><span data-stu-id="bba42-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="bba42-103">下列 XML 檔案用於 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 文件的各種範例中。</span><span class="sxs-lookup"><span data-stu-id="bba42-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] documentation.</span></span> <span data-ttu-id="bba42-104">此檔案包含數值資料以進行加總、平均和群組。</span><span class="sxs-lookup"><span data-stu-id="bba42-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="bba42-105">XML 位於命名空間中。</span><span class="sxs-lookup"><span data-stu-id="bba42-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="bba42-106">資料</span><span class="sxs-lookup"><span data-stu-id="bba42-106">Data</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bba42-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bba42-107">See Also</span></span>  
 [<span data-ttu-id="bba42-108">範例 XML 文件 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bba42-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
