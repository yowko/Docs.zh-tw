---
title: 範例 XML 檔：命名空間中的數值資料
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: 02788b73a7af9922b5a50237f2d2e401cba8abe2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483698"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="20d02-102">範例 XML 檔：命名空間中的數值資料</span><span class="sxs-lookup"><span data-stu-id="20d02-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="20d02-103">下列 XML 檔案用於 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文件的各種範例中。</span><span class="sxs-lookup"><span data-stu-id="20d02-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="20d02-104">此檔案包含數值資料以進行加總、平均和群組。</span><span class="sxs-lookup"><span data-stu-id="20d02-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="20d02-105">XML 位於命名空間中。</span><span class="sxs-lookup"><span data-stu-id="20d02-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="20d02-106">資料</span><span class="sxs-lookup"><span data-stu-id="20d02-106">Data</span></span>  
  
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
