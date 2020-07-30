---
title: '如何取出屬性的值（LINQ to XML）（c #）'
description: 瞭解如何取得屬性的值。 請參閱程式碼範例，並查看其他可用的資源。
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 5ee6995a54829b6d992e2982e6a6effcabf76470
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301550"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="cb31b-104">如何取出屬性的值（LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="cb31b-104">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="cb31b-105">這個主題顯示如何取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="cb31b-105">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="cb31b-106">有兩個主要方式：您可以將 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別；然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別。</span><span class="sxs-lookup"><span data-stu-id="cb31b-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="cb31b-107">或者，您可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cb31b-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="cb31b-108">不過，轉型通常是較好的方法。</span><span class="sxs-lookup"><span data-stu-id="cb31b-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="cb31b-109">如果您將屬性轉換成可為 null 的實值型別，則在抓取可能或可能不存在之屬性的值時，程式碼會比較容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="cb31b-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="cb31b-110">如需這項技術的範例，請參閱[如何取出元素的值（LINQ to XML）（c #）](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cb31b-110">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb31b-111">範例</span><span class="sxs-lookup"><span data-stu-id="cb31b-111">Example</span></span>  
 <span data-ttu-id="cb31b-112">若要擷取屬性的值，只要將 <xref:System.Xml.Linq.XAttribute> 物件轉型為您所需的型別即可。</span><span class="sxs-lookup"><span data-stu-id="cb31b-112">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="cb31b-113">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cb31b-113">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="cb31b-114">範例</span><span class="sxs-lookup"><span data-stu-id="cb31b-114">Example</span></span>  
 <span data-ttu-id="cb31b-115">下列範例顯示如何擷取屬性位於命名空間之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="cb31b-115">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="cb31b-116">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cb31b-116">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="cb31b-117">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cb31b-117">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb31b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb31b-118">See also</span></span>

- [<span data-ttu-id="cb31b-119">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="cb31b-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
