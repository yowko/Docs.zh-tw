---
title: 作法：擷取屬性的值 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 54ea4b532669ed2c615fcde02011fdd1228705a3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592476"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="e83b5-102">作法：擷取屬性的值 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e83b5-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="e83b5-103">這個主題顯示如何取得屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e83b5-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="e83b5-104">有兩個主要方式：您可以將 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別；然後，明確的轉換運算子會將元素或屬性的內容轉換為指定的型別。</span><span class="sxs-lookup"><span data-stu-id="e83b5-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="e83b5-105">或者，您可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e83b5-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="e83b5-106">不過，轉型通常是較好的方法。</span><span class="sxs-lookup"><span data-stu-id="e83b5-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="e83b5-107">如果您要將屬性轉型為可為 Null 的型別 (Nullable Type)，擷取可能存在或可能不存在之屬性的值時，程式碼比較容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="e83b5-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="e83b5-108">如需此技術的範例，請參閱[如何：擷取項目的值 (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e83b5-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e83b5-109">範例</span><span class="sxs-lookup"><span data-stu-id="e83b5-109">Example</span></span>  
 <span data-ttu-id="e83b5-110">若要擷取屬性的值，只要將 <xref:System.Xml.Linq.XAttribute> 物件轉型為您所需的型別即可。</span><span class="sxs-lookup"><span data-stu-id="e83b5-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="e83b5-111">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e83b5-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="e83b5-112">範例</span><span class="sxs-lookup"><span data-stu-id="e83b5-112">Example</span></span>  
 <span data-ttu-id="e83b5-113">下列範例顯示如何擷取屬性位於命名空間之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="e83b5-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="e83b5-114">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e83b5-114">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="e83b5-115">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e83b5-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="e83b5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e83b5-116">See also</span></span>

- [<span data-ttu-id="e83b5-117">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="e83b5-117">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
