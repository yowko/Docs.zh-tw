---
title: '如何取出元素的淺層值（c #）'
description: 瞭解如何取得元素的淺層值。 淺層值僅適用于特定元素。
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 597859e5b66606aa0cff9c1a475e79e6b66c39fc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301576"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="91aeb-104">如何取出元素的淺層值（c #）</span><span class="sxs-lookup"><span data-stu-id="91aeb-104">How to retrieve the shallow value of an element (C#)</span></span>
<span data-ttu-id="91aeb-105">本主題說明如何取得項目的表層值。</span><span class="sxs-lookup"><span data-stu-id="91aeb-105">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="91aeb-106">表層值僅是特定項目的值。與深層值不同的是，深層值包含了由所有子代項目連結成單一字串的值。</span><span class="sxs-lookup"><span data-stu-id="91aeb-106">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="91aeb-107">當您使用轉換或 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性，您擷取的是深層值。</span><span class="sxs-lookup"><span data-stu-id="91aeb-107">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="91aeb-108">若要擷取表層值，您可以使用 `ShallowValue` 擴充方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="91aeb-108">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="91aeb-109">當您想要根據項目的內容進行選取時，擷取表層值就非常有用。</span><span class="sxs-lookup"><span data-stu-id="91aeb-109">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="91aeb-110">下列範例會宣告擷取項目表層值的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="91aeb-110">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="91aeb-111">接著會在查詢中使用此擴充方法，將所有包含計算值的項目列出。</span><span class="sxs-lookup"><span data-stu-id="91aeb-111">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91aeb-112">範例</span><span class="sxs-lookup"><span data-stu-id="91aeb-112">Example</span></span>  
 <span data-ttu-id="91aeb-113">下列文字檔 Report.xml 是此範例的原始檔。</span><span class="sxs-lookup"><span data-stu-id="91aeb-113">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="91aeb-114">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="91aeb-114">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="91aeb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91aeb-115">See also</span></span>

- [<span data-ttu-id="91aeb-116">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="91aeb-116">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
