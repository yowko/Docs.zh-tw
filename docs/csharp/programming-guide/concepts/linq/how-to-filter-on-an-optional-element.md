---
title: "如何：篩選選擇性項目 (C#) | Microsoft Docs"
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
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bc732e029b1548a551128b7f8daca5f10dc19c03
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-filter-on-an-optional-element-c"></a>如何：篩選選擇性項目 (C#)
有時候即使您不確定項目是否存在於 XML 文件中，您都會想要針對該項目進行篩選。 搜尋應該會執行，因此，如果特定的項目沒有子項目，您就不會篩選該項目來觸發 Null 參考例外狀況。 在下列範例中，`Child5` 項目沒有 `Type` 子項目，但查詢仍會正確執行。  
  
## <a name="example"></a>範例  
 此範例使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 擴充方法。  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 此程式碼會產生下列輸出：  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 此程式碼會產生下列輸出：  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>   
 [基本查詢 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)   
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [投影作業 (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
