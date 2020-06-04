---
title: 作法：尋找具有特定子項目的項目
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: a05504070fe3d2ea5eb6135fd3bf697b131686c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405283"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a><span data-ttu-id="1f3c3-102">如何：尋找具有特定子專案的專案（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1f3c3-102">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>
<span data-ttu-id="1f3c3-103">本主題顯示如何利用特定的值尋找具有子項目的特定項目。</span><span class="sxs-lookup"><span data-stu-id="1f3c3-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f3c3-104">範例</span><span class="sxs-lookup"><span data-stu-id="1f3c3-104">Example</span></span>  
 <span data-ttu-id="1f3c3-105">此範例會利用 "Examp2.EXE" 這個值，尋找具有 `Test` 子項目的 `CommandLine` 項目。</span><span class="sxs-lookup"><span data-stu-id="1f3c3-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="1f3c3-106">此範例使用下列 XML 文件︰[範例 XML 檔：測試組態 (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3c3-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 <span data-ttu-id="1f3c3-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1f3c3-107">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
 <span data-ttu-id="1f3c3-108">請注意，此範例使用[Xml 子軸屬性](../../../language-reference/xml-axis/xml-child-axis-property.md)、 [xml 屬性軸屬性](../../../language-reference/xml-axis/xml-attribute-axis-property.md)和[xml 值屬性](../../../language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3c3-108">Note that this example uses the [XML Child axis property](../../../language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f3c3-109">範例</span><span class="sxs-lookup"><span data-stu-id="1f3c3-109">Example</span></span>  
 <span data-ttu-id="1f3c3-110">下列範例顯示命名空間中之 XML 的相同查詢。</span><span class="sxs-lookup"><span data-stu-id="1f3c3-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1f3c3-111">如需詳細資訊，請參閱[命名空間總覽（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3c3-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1f3c3-112">此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的測試組態](sample-xml-file-test-configuration-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="1f3c3-112">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](sample-xml-file-test-configuration-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="1f3c3-113">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1f3c3-113">This code produces the following output:</span></span>  
  
```console  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f3c3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f3c3-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="1f3c3-115">基本查詢（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1f3c3-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
- [<span data-ttu-id="1f3c3-116">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f3c3-116">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="1f3c3-117">投射作業（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="1f3c3-117">Projection Operations (Visual Basic)</span></span>](projection-operations.md)
