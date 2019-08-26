---
title: 作法：尋找具有特定子項目的項目 (C#)
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 80539c7ccd21bc38967479d7b724e6f3361d24ac
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593556"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="cf065-102">作法：尋找具有特定子項目的項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="cf065-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="cf065-103">本主題顯示如何利用特定的值尋找具有子項目的特定項目。</span><span class="sxs-lookup"><span data-stu-id="cf065-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf065-104">範例</span><span class="sxs-lookup"><span data-stu-id="cf065-104">Example</span></span>  
 <span data-ttu-id="cf065-105">此範例會利用 "Examp2.EXE" 這個值，尋找具有 `Test` 子項目的 `CommandLine` 項目。</span><span class="sxs-lookup"><span data-stu-id="cf065-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="cf065-106">此範例使用下列 XML 文件：[XML 範例檔：測試組態 (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cf065-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="cf065-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cf065-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="cf065-108">範例</span><span class="sxs-lookup"><span data-stu-id="cf065-108">Example</span></span>  
 <span data-ttu-id="cf065-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="cf065-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cf065-110">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="cf065-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cf065-111">此範例使用下列 XML 文件：[XML 範例檔：測試命名空間中的組態](./sample-xml-file-test-configuration-in-a-namespace1.md)。</span><span class="sxs-lookup"><span data-stu-id="cf065-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](./sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="cf065-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="cf065-112">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf065-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf065-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="cf065-114">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="cf065-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="cf065-115">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="cf065-115">Projection Operations (C#)</span></span>](./projection-operations.md)
