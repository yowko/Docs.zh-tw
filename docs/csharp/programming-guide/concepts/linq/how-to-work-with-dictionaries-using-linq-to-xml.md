---
title: '如何使用 LINQ to XML 處理字典（c #）'
description: 瞭解如何使用 LINQ to XML 來處理字典。 請參閱將字典轉換成 XML 的範例和 XML 回到其他資料結構。
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: bdba7a2b3dfc16fab1e239ac804c317dfefb7d9e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302616"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="e2cd3-104">如何使用 LINQ to XML 處理字典（c #）</span><span class="sxs-lookup"><span data-stu-id="e2cd3-104">How to work with dictionaries using LINQ to XML (C#)</span></span>
<span data-ttu-id="e2cd3-105">將各種資料結構轉換為 XML，以及將 XML 轉回其他資料結構通常很方便。</span><span class="sxs-lookup"><span data-stu-id="e2cd3-105">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="e2cd3-106">這個主題藉由來回轉換 <xref:System.Collections.Generic.Dictionary%602> 和 XML 來顯示這個一般方法的特定實作。</span><span class="sxs-lookup"><span data-stu-id="e2cd3-106">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2cd3-107">範例</span><span class="sxs-lookup"><span data-stu-id="e2cd3-107">Example</span></span>  
 <span data-ttu-id="e2cd3-108">這個範例會使用查詢評估新 <xref:System.Xml.Linq.XElement> 物件之功能結構的形式，並將產生的集合當作 <xref:System.Xml.Linq.XElement> 根物件之建構函式的引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="e2cd3-108">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="e2cd3-109">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e2cd3-109">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e2cd3-110">範例</span><span class="sxs-lookup"><span data-stu-id="e2cd3-110">Example</span></span>  
 <span data-ttu-id="e2cd3-111">下列程式碼會從 XML 建立字典。</span><span class="sxs-lookup"><span data-stu-id="e2cd3-111">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="e2cd3-112">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e2cd3-112">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
