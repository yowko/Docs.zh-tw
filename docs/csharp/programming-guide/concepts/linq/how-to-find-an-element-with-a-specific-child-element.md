---
title: '如何尋找具有特定子專案的元素（c #）'
description: 瞭解如何尋找具有特定子專案的元素。 請參閱程式碼範例和其他資源。
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301706"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="a70cb-104">如何尋找具有特定子專案的元素（c #）</span><span class="sxs-lookup"><span data-stu-id="a70cb-104">How to find an element with a specific child element (C#)</span></span>
<span data-ttu-id="a70cb-105">本主題顯示如何利用特定的值尋找具有子項目的特定項目。</span><span class="sxs-lookup"><span data-stu-id="a70cb-105">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a70cb-106">範例</span><span class="sxs-lookup"><span data-stu-id="a70cb-106">Example</span></span>  
 <span data-ttu-id="a70cb-107">此範例會利用 "Examp2.EXE" 這個值，尋找具有 `Test` 子項目的 `CommandLine` 項目。</span><span class="sxs-lookup"><span data-stu-id="a70cb-107">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="a70cb-108">此範例使用下列 XML 文件︰[範例 XML 檔：測試組態 (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a70cb-108">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="a70cb-109">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a70cb-109">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="a70cb-110">範例</span><span class="sxs-lookup"><span data-stu-id="a70cb-110">Example</span></span>  
 <span data-ttu-id="a70cb-111">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="a70cb-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a70cb-112">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="a70cb-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a70cb-113">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的測試組態](./sample-xml-file-test-configuration-in-a-namespace1.md)。</span><span class="sxs-lookup"><span data-stu-id="a70cb-113">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="a70cb-114">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a70cb-114">This code produces the following output:</span></span>  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="a70cb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a70cb-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="a70cb-116">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="a70cb-116">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="a70cb-117">投射作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="a70cb-117">Projection Operations (C#)</span></span>](./projection-operations.md)
