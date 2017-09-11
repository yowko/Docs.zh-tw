---
title: "如何：利用 LINQ to XML 使用字典 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 32ee8e1d80e78417b76d62b8801b222c21bef077
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017


---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="d8020-102">如何：利用 LINQ to XML 使用字典 (C#)</span><span class="sxs-lookup"><span data-stu-id="d8020-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="d8020-103">將各種資料結構轉換為 XML，以及將 XML 轉回其他資料結構通常很方便。</span><span class="sxs-lookup"><span data-stu-id="d8020-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="d8020-104">本主題藉由來回轉換 <xref:System.Collections.Generic.Dictionary%602> 和 XML 來顯示這個一般方法的特定實作。</span><span class="sxs-lookup"><span data-stu-id="d8020-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8020-105">範例</span><span class="sxs-lookup"><span data-stu-id="d8020-105">Example</span></span>  
 <span data-ttu-id="d8020-106">此範例會使用查詢投影新 <xref:System.Xml.Linq.XElement> 物件之函數式建構的形式，並將產生的集合當做 <xref:System.Xml.Linq.XElement> 根物件之建構函式的引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="d8020-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="d8020-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d8020-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="d8020-108">範例</span><span class="sxs-lookup"><span data-stu-id="d8020-108">Example</span></span>  
 <span data-ttu-id="d8020-109">下列程式碼會從 XML 建立字典。</span><span class="sxs-lookup"><span data-stu-id="d8020-109">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="d8020-110">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d8020-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8020-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8020-111">See Also</span></span>  
 [<span data-ttu-id="d8020-112">投影和轉換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8020-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
