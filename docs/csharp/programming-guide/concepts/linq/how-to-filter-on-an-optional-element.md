---
title: HOW TO：篩選選擇性項目 (C#)
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 1aeb234365fa5d02911f70bb70a860258ce62f30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540103"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="df9e4-102">HOW TO：篩選選擇性項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="df9e4-102">How to: Filter on an Optional Element (C#)</span></span>
<span data-ttu-id="df9e4-103">有時候即使您不確定項目是否存在於 XML 文件中，您都會想要針對該項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="df9e4-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="df9e4-104">搜尋應該會執行，因此，如果特定的項目沒有子項目，您就不會篩選該項目來觸發 Null 參考例外狀況。</span><span class="sxs-lookup"><span data-stu-id="df9e4-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="df9e4-105">在下列範例中，`Child5` 項目沒有 `Type` 子項目，但查詢仍會正確執行。</span><span class="sxs-lookup"><span data-stu-id="df9e4-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df9e4-106">範例</span><span class="sxs-lookup"><span data-stu-id="df9e4-106">Example</span></span>  
 <span data-ttu-id="df9e4-107">此範例使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="df9e4-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="df9e4-108">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="df9e4-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="df9e4-109">範例</span><span class="sxs-lookup"><span data-stu-id="df9e4-109">Example</span></span>  
 <span data-ttu-id="df9e4-110">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="df9e4-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="df9e4-111">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="df9e4-111">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="df9e4-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="df9e4-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="df9e4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df9e4-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="df9e4-114">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="df9e4-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="df9e4-115">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="df9e4-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="df9e4-116">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="df9e4-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
