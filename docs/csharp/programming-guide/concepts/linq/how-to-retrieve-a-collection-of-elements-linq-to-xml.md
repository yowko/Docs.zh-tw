---
title: 作法：擷取項目的集合 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 0ca40b77a78f155292dfbb26471442450bf16b9b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592634"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="373f6-102">作法：擷取項目的集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="373f6-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="373f6-103">這個主題會示範 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="373f6-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="373f6-104">此方法會擷取項目之子項目的集合。</span><span class="sxs-lookup"><span data-stu-id="373f6-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="373f6-105">範例</span><span class="sxs-lookup"><span data-stu-id="373f6-105">Example</span></span>  
 <span data-ttu-id="373f6-106">此範例會逐一查看 `purchaseOrder` 項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="373f6-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="373f6-107">此範例使用下列 XML 文件：[XML 範例檔：典型訂購單 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="373f6-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="373f6-108">此範例會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="373f6-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="373f6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="373f6-109">See also</span></span>

- [<span data-ttu-id="373f6-110">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="373f6-110">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
