---
title: "如何：根據位置尋找子項目 (XPath-LINQ to XML) (C#) | Microsoft Docs"
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
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ce711d5e0ce82d4fcb0351c21ac7a769c414b2a4
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>如何：根據位置尋找子項目 (XPath-LINQ to XML) (C#)
有時候您會想要根據項目的位置尋找這些項目。 您可能想要尋找第二個項目，或者想要尋找第三到第五個項目。  
  
 XPath 運算式為：  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 以延遲的方式撰寫這個 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 查詢的方法有兩種。 您可以使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 運算子，或使用採用索引的 <xref:System.Linq.Enumerable.Where%2A> 多載。 當您使用 <xref:System.Linq.Enumerable.Where%2A> 多載時，您可以使用採用兩個引數的 Lambda 運算式。 下列範例顯示根據位置進行選擇的兩種方法。  
  
## <a name="example"></a>範例  
 這個範例會尋找第二到第四個 `Test` 項目。 結果為項目的集合。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：測試組態 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)。  
  
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
  
 這個範例會產生下列輸出：  
  
```  
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
  
## <a name="see-also"></a>另請參閱  
 [XPath 使用者適用的 LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
