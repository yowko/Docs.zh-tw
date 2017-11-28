---
title: "如何：擷取屬性集合 (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 165c807735bfc73375d4ddec125786750ad08ad1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="8cd39-102">如何：擷取屬性集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8cd39-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8cd39-103">本主題說明 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8cd39-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="8cd39-104">這個方法會擷取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="8cd39-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cd39-105">範例</span><span class="sxs-lookup"><span data-stu-id="8cd39-105">Example</span></span>  
 <span data-ttu-id="8cd39-106">下列範例顯示如何逐一查看項目之屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="8cd39-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 <span data-ttu-id="8cd39-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8cd39-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cd39-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cd39-108">See Also</span></span>  
 [<span data-ttu-id="8cd39-109">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="8cd39-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
