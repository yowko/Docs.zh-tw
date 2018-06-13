---
title: 如何：擷取項目集合 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 8d2aab59a6c2a72d796bfaf40755bdf280c81b6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320413"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="7a509-102">如何：擷取項目集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7a509-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7a509-103">這個主題會示範 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7a509-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="7a509-104">此方法會擷取項目之子項目的集合。</span><span class="sxs-lookup"><span data-stu-id="7a509-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a509-105">範例</span><span class="sxs-lookup"><span data-stu-id="7a509-105">Example</span></span>  
 <span data-ttu-id="7a509-106">此範例會逐一查看 `purchaseOrder` 項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="7a509-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="7a509-107">此範例使用下列 XML 文件︰[範例 XML 檔：典型採購訂單 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="7a509-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="7a509-108">此範例會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="7a509-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a509-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="7a509-109">See Also</span></span>  
 [<span data-ttu-id="7a509-110">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="7a509-110">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
