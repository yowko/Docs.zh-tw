---
title: XML 範例檔：在 3 中的典型採購訂單
ms.date: 07/20/2015
ms.assetid: 38260901-c9f9-4240-9cbf-652c8b05021d
ms.openlocfilehash: 2929900865814127250acb2e24c7f674995705da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646025"
---
# <a name="sample-xml-file-typical-purchase-order-in-a-namespace"></a><span data-ttu-id="cdc1e-102">XML 範例檔：命名空間中的典型採購訂單</span><span class="sxs-lookup"><span data-stu-id="cdc1e-102">Sample XML File: Typical Purchase Order in a Namespace</span></span>
<span data-ttu-id="cdc1e-103">下列 XML 檔案用於 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 文件的各種範例中。</span><span class="sxs-lookup"><span data-stu-id="cdc1e-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="cdc1e-104">這個檔案是典型的採購訂單。</span><span class="sxs-lookup"><span data-stu-id="cdc1e-104">This file is a typical purchase order.</span></span> <span data-ttu-id="cdc1e-105">XML 位於命名空間中。</span><span class="sxs-lookup"><span data-stu-id="cdc1e-105">The XML is in a namespace.</span></span>  
  
## <a name="purchaseorderinnamespacexml"></a><span data-ttu-id="cdc1e-106">PurchaseOrderInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="cdc1e-106">PurchaseOrderInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<aw:PurchaseOrder  
    aw:PurchaseOrderNumber="99503"  
    aw:OrderDate="1999-10-20"  
    xmlns:aw="http://www.adventure-works.com">  
  <aw:Address aw:Type="Shipping">  
    <aw:Name>Ellen Adams</aw:Name>  
    <aw:Street>123 Maple Street</aw:Street>  
    <aw:City>Mill Valley</aw:City>  
    <aw:State>CA</aw:State>  
    <aw:Zip>10999</aw:Zip>  
    <aw:Country>USA</aw:Country>  
  </aw:Address>  
  <aw:Address aw:Type="Billing">  
    <aw:Name>Tai Yee</aw:Name>  
    <aw:Street>8 Oak Avenue</aw:Street>  
    <aw:City>Old Town</aw:City>  
    <aw:State>PA</aw:State>  
    <aw:Zip>95819</aw:Zip>  
    <aw:Country>USA</aw:Country>  
  </aw:Address>  
  <aw:DeliveryNotes>Please leave packages in shed by driveway.</aw:DeliveryNotes>  
  <aw:Items>  
    <aw:Item aw:PartNumber="872-AA">  
      <aw:ProductName>Lawnmower</aw:ProductName>  
      <aw:Quantity>1</aw:Quantity>  
      <aw:USPrice>148.95</aw:USPrice>  
      <aw:Comment>Confirm this is electric</aw:Comment>  
    </aw:Item>  
    <aw:Item aw:PartNumber="926-AA">  
      <aw:ProductName>Baby Monitor</aw:ProductName>  
      <aw:Quantity>2</aw:Quantity>  
      <aw:USPrice>39.98</aw:USPrice>  
      <aw:ShipDate>1999-05-21</aw:ShipDate>  
    </aw:Item>  
  </aw:Items>  
</aw:PurchaseOrder>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdc1e-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdc1e-107">See also</span></span>
- [<span data-ttu-id="cdc1e-108">範例 XML 文件 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cdc1e-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
