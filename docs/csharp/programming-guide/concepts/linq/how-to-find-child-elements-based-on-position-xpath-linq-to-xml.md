---
title: '如何尋找以位置為基礎的子項目（XPath-LINQ to XML）（c #）'
description: 瞭解如何使用 XPath 運算式根據位置尋找子項目。 請參閱使用範例 XML 檔案的程式碼範例。
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 2603d3ac94ace645bde1ce85a43a43af7321014e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301667"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="bd34d-104">如何尋找以位置為基礎的子項目（XPath-LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="bd34d-104">How to find child elements based on position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="bd34d-105">有時候您會想要根據項目的位置尋找這些項目。</span><span class="sxs-lookup"><span data-stu-id="bd34d-105">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="bd34d-106">您可能想要尋找第二個項目，或者想要尋找第三到第五個項目。</span><span class="sxs-lookup"><span data-stu-id="bd34d-106">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="bd34d-107">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="bd34d-107">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="bd34d-108">以延遲的方式撰寫這個 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="bd34d-108">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="bd34d-109">您可以使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 運算子，或者，您可以使用採用索引的 <xref:System.Linq.Enumerable.Where%2A> 多載。</span><span class="sxs-lookup"><span data-stu-id="bd34d-109">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="bd34d-110">當您使用 <xref:System.Linq.Enumerable.Where%2A> 多載時，您可以使用採用兩個引數的 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="bd34d-110">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="bd34d-111">下列範例顯示根據位置進行選擇的兩種方法。</span><span class="sxs-lookup"><span data-stu-id="bd34d-111">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd34d-112">範例</span><span class="sxs-lookup"><span data-stu-id="bd34d-112">Example</span></span>  
 <span data-ttu-id="bd34d-113">這個範例會尋找第二到第四個 `Test` 項目。</span><span class="sxs-lookup"><span data-stu-id="bd34d-113">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="bd34d-114">結果為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="bd34d-114">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="bd34d-115">此範例使用下列 XML 文件︰[範例 XML 檔：測試組態 (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bd34d-115">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="bd34d-116">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bd34d-116">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
