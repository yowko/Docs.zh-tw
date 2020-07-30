---
title: '如何尋找具有特定名稱之同級的屬性（XPath-LINQ to XML）（c #）'
description: 瞭解如何尋找內容節點之同級的所有屬性。 請參閱使用範例 XML 檔案的程式碼範例。
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 12bba22c91fef92fc3383d028ff9dfb8bd3cfa3e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301693"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="13d22-104">如何尋找具有特定名稱之同級的屬性（XPath-LINQ to XML）（c #）</span><span class="sxs-lookup"><span data-stu-id="13d22-104">How to find attributes of siblings with a specific name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="13d22-105">本主題顯示如何尋找內容節點之同層級的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="13d22-105">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="13d22-106">在集合中，只會傳回具有特定名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="13d22-106">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="13d22-107">XPath 運算式為：</span><span class="sxs-lookup"><span data-stu-id="13d22-107">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="13d22-108">範例</span><span class="sxs-lookup"><span data-stu-id="13d22-108">Example</span></span>  
 <span data-ttu-id="13d22-109">此範例會先尋找 `Book` 項目，接著尋找名稱為 `Book` 的所有同層級項目，然後尋找名稱為 `id` 的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="13d22-109">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="13d22-110">結果為屬性的集合。</span><span class="sxs-lookup"><span data-stu-id="13d22-110">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="13d22-111">此範例使用下列 XML 文件︰[範例 XML 檔：書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="13d22-111">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="13d22-112">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="13d22-112">This example produces the following output:</span></span>  
  
```output  
Results are identical  
id="bk101"  
id="bk102"  
```  
  