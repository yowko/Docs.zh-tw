---
title: 作法：擷取屬性的集合 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: b37600f02cd012e688d161a079c3c8647545cb2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592672"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="fc397-102">作法：擷取屬性的集合 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fc397-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="fc397-103">本主題說明 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fc397-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="fc397-104">這個方法會擷取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="fc397-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc397-105">範例</span><span class="sxs-lookup"><span data-stu-id="fc397-105">Example</span></span>  
 <span data-ttu-id="fc397-106">下列範例顯示如何逐一查看項目之屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="fc397-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="fc397-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fc397-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc397-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc397-108">See also</span></span>

- [<span data-ttu-id="fc397-109">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="fc397-109">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
