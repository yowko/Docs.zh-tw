---
title: 如何篩選選擇性元素（C#）
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: c9f844619cbb3d7a66ca66989baa900e0fd7bc2f
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141249"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="e559f-102">如何篩選選擇性元素（C#）</span><span class="sxs-lookup"><span data-stu-id="e559f-102">How to filter on an optional element (C#)</span></span>
<span data-ttu-id="e559f-103">有時候即使您不確定項目是否存在於 XML 文件中，您都會想要針對該項目進行篩選。</span><span class="sxs-lookup"><span data-stu-id="e559f-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="e559f-104">搜尋應該會執行，因此，如果特定的項目沒有子項目，您就不會篩選該項目來觸發 Null 參考例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e559f-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="e559f-105">在下列範例中，`Child5` 項目沒有 `Type` 子項目，但查詢仍會正確執行。</span><span class="sxs-lookup"><span data-stu-id="e559f-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e559f-106">範例</span><span class="sxs-lookup"><span data-stu-id="e559f-106">Example</span></span>  
 <span data-ttu-id="e559f-107">此範例使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="e559f-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="e559f-108">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e559f-108">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="e559f-109">範例</span><span class="sxs-lookup"><span data-stu-id="e559f-109">Example</span></span>  
 <span data-ttu-id="e559f-110">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="e559f-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e559f-111">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e559f-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e559f-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e559f-112">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="e559f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="e559f-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e559f-114">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="e559f-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e559f-115">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="e559f-115">Projection Operations (C#)</span></span>](./projection-operations.md)
