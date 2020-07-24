---
title: '如何取出屬性的集合（LINQ to XML）（c #）'
description: 'C # 中的 Attributes 方法會抓取元素的屬性。 這個 LINQ to XML 範例會逐一查看元素的屬性集合。'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 5994086db6133530e63eb1328a7b524d30a0797d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103381"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="08943-104">如何取出屬性的集合（LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="08943-104">How to retrieve a collection of attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="08943-105">本主題說明 <xref:System.Xml.Linq.XElement.Attributes%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="08943-105">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="08943-106">這個方法會擷取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="08943-106">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08943-107">範例</span><span class="sxs-lookup"><span data-stu-id="08943-107">Example</span></span>  
 <span data-ttu-id="08943-108">下列範例顯示如何逐一查看項目之屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="08943-108">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="08943-109">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="08943-109">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="08943-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="08943-110">See also</span></span>

- [<span data-ttu-id="08943-111">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="08943-111">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
