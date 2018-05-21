---
title: 如何：擷取項目的表層值 (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 47c7cdd118a14070ea3a005bda88b55cc7075185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="ea1f1-102">如何：擷取項目的表層值 (C#)</span><span class="sxs-lookup"><span data-stu-id="ea1f1-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="ea1f1-103">本主題說明如何取得項目的表層值。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="ea1f1-104">表層值僅是特定項目的值。與深層值不同的是，深層值包含了由所有子代項目連結成單一字串的值。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="ea1f1-105">當您使用轉換或 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性，您擷取的是深層值。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="ea1f1-106">若要擷取表層值，您可以使用 `ShallowValue` 擴充方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="ea1f1-107">當您想要根據項目的內容進行選取時，擷取表層值就非常有用。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="ea1f1-108">下列範例會宣告擷取項目表層值的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="ea1f1-109">接著會在查詢中使用此擴充方法，將所有包含計算值的項目列出。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea1f1-110">範例</span><span class="sxs-lookup"><span data-stu-id="ea1f1-110">Example</span></span>  
 <span data-ttu-id="ea1f1-111">下列文字檔 Report.xml 是此範例的原始檔。</span><span class="sxs-lookup"><span data-stu-id="ea1f1-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="ea1f1-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="ea1f1-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea1f1-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea1f1-113">See Also</span></span>  
 [<span data-ttu-id="ea1f1-114">LINQ to XML 座標軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="ea1f1-114">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
