---
title: "如何：尋找具有特定子項目的項目 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7d4d865b6e412f6f039df3578340db046ca59fa6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a><span data-ttu-id="58a4c-102">如何：尋找具有特定子項目的項目 (C#)</span><span class="sxs-lookup"><span data-stu-id="58a4c-102">How to: Find an Element with a Specific Child Element (C#)</span></span>
<span data-ttu-id="58a4c-103">本主題顯示如何利用特定的值尋找具有子項目的特定項目。</span><span class="sxs-lookup"><span data-stu-id="58a4c-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a4c-104">範例</span><span class="sxs-lookup"><span data-stu-id="58a4c-104">Example</span></span>  
 <span data-ttu-id="58a4c-105">此範例會利用 "Examp2.EXE" 這個值，尋找具有 `Test` 子項目的 `CommandLine` 項目。</span><span class="sxs-lookup"><span data-stu-id="58a4c-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="58a4c-106">此範例使用下列 XML 文件︰[範例 XML 檔：測試組態 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="58a4c-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 <span data-ttu-id="58a4c-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="58a4c-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="example"></a><span data-ttu-id="58a4c-108">範例</span><span class="sxs-lookup"><span data-stu-id="58a4c-108">Example</span></span>  
 <span data-ttu-id="58a4c-109">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="58a4c-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="58a4c-110">如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="58a4c-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="58a4c-111">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的測試組態](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md)。</span><span class="sxs-lookup"><span data-stu-id="58a4c-111">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).</span></span>  
  
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
  
 <span data-ttu-id="58a4c-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="58a4c-112">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="58a4c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58a4c-113">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="58a4c-114">基本查詢 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="58a4c-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="58a4c-115">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="58a4c-115">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="58a4c-116">投影作業 (C#)</span><span class="sxs-lookup"><span data-stu-id="58a4c-116">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
