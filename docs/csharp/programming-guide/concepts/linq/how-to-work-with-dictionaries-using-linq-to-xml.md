---
title: "如何：利用 LINQ to XML 使用字典 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 422b9381596e06214e6116a3ba3c9d2b63c8651f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="e6d32-102">如何：利用 LINQ to XML 使用字典 (C#)</span><span class="sxs-lookup"><span data-stu-id="e6d32-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="e6d32-103">將各種資料結構轉換為 XML，以及將 XML 轉回其他資料結構通常很方便。</span><span class="sxs-lookup"><span data-stu-id="e6d32-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="e6d32-104">這個主題藉由來回轉換 <xref:System.Collections.Generic.Dictionary%602> 和 XML 來顯示這個一般方法的特定實作。</span><span class="sxs-lookup"><span data-stu-id="e6d32-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6d32-105">範例</span><span class="sxs-lookup"><span data-stu-id="e6d32-105">Example</span></span>  
 <span data-ttu-id="e6d32-106">這個範例會使用查詢評估新 <xref:System.Xml.Linq.XElement> 物件之功能結構的形式，並將產生的集合當作 <xref:System.Xml.Linq.XElement> 根物件之建構函式的引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="e6d32-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="e6d32-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e6d32-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e6d32-108">範例</span><span class="sxs-lookup"><span data-stu-id="e6d32-108">Example</span></span>  
 <span data-ttu-id="e6d32-109">下列程式碼會從 XML 建立字典。</span><span class="sxs-lookup"><span data-stu-id="e6d32-109">The following code creates a dictionary from XML.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 <span data-ttu-id="e6d32-110">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e6d32-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6d32-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6d32-111">See Also</span></span>  
 [<span data-ttu-id="e6d32-112">投影和轉換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e6d32-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
