---
title: 如何使用 LINQ to XML （C#）處理字典
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 1a98293f208e80e969362fca27014ecd2e5c4183
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347231"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>如何使用 LINQ to XML （C#）處理字典
將各種資料結構轉換為 XML，以及將 XML 轉回其他資料結構通常很方便。 這個主題藉由來回轉換 <xref:System.Collections.Generic.Dictionary%602> 和 XML 來顯示這個一般方法的特定實作。  
  
## <a name="example"></a>範例  
 這個範例會使用查詢評估新 <xref:System.Xml.Linq.XElement> 物件之功能結構的形式，並將產生的集合當作 <xref:System.Xml.Linq.XElement> 根物件之建構函式的引數傳遞。  
  
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
  
 此程式碼會產生下列輸出：  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>範例  
 下列程式碼會從 XML 建立字典。  
  
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
  
 此程式碼會產生下列輸出：  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
