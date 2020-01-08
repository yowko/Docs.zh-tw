---
title: 如何取出屬性的集合（LINQ to XML）（C#）
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 02871b38c3b1a1ed64fa6ca808e193811cd7f721
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347635"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="21cb9-102">如何取出屬性的集合（LINQ to XML）（C#）</span><span class="sxs-lookup"><span data-stu-id="21cb9-102">How to retrieve a collection of attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="21cb9-103">本主題說明 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="21cb9-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="21cb9-104">這個方法會擷取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="21cb9-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21cb9-105">範例</span><span class="sxs-lookup"><span data-stu-id="21cb9-105">Example</span></span>  
 <span data-ttu-id="21cb9-106">下列範例顯示如何逐一查看項目之屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="21cb9-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="21cb9-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="21cb9-107">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="21cb9-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="21cb9-108">See also</span></span>

- [<span data-ttu-id="21cb9-109">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="21cb9-109">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
