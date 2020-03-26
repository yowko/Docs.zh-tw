---
title: 如何檢索屬性的值（LINQ 到 XML）（C#）
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249190"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="fd06a-102">如何檢索屬性的值（LINQ 到 XML）（C#）</span><span class="sxs-lookup"><span data-stu-id="fd06a-102">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="fd06a-103">這個主題顯示如何取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="fd06a-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="fd06a-104">有兩個主要方式：您可以將 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別；然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別。</span><span class="sxs-lookup"><span data-stu-id="fd06a-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="fd06a-105">或者，您可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fd06a-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="fd06a-106">不過，轉型通常是較好的方法。</span><span class="sxs-lookup"><span data-stu-id="fd06a-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="fd06a-107">如果將屬性強制轉換為可 null 數值型別，則在檢索可能存在或可能不存在的屬性的值時，代碼的編寫更簡單。</span><span class="sxs-lookup"><span data-stu-id="fd06a-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="fd06a-108">有關此技術的示例，請參閱[如何檢索元素的值（LINQ 到 XML）（C#）。](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="fd06a-108">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd06a-109">範例</span><span class="sxs-lookup"><span data-stu-id="fd06a-109">Example</span></span>  
 <span data-ttu-id="fd06a-110">若要擷取屬性的值，只要將 <xref:System.Xml.Linq.XAttribute> 物件轉型為您所需的型別即可。</span><span class="sxs-lookup"><span data-stu-id="fd06a-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="fd06a-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fd06a-111">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="fd06a-112">範例</span><span class="sxs-lookup"><span data-stu-id="fd06a-112">Example</span></span>  
 <span data-ttu-id="fd06a-113">下列範例顯示如何擷取屬性位於命名空間之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="fd06a-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="fd06a-114">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="fd06a-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="fd06a-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="fd06a-115">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd06a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd06a-116">See also</span></span>

- [<span data-ttu-id="fd06a-117">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="fd06a-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
