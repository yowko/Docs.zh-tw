---
title: 如何： 尋找子項目 (XPATH-LINQ to XML) 的位置為基礎 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: 9f18da12786b4c44dc21e54c8d5020f49ef9ecb6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a>如何： 尋找子項目 (XPATH-LINQ to XML) 的位置為基礎 (Visual Basic)
有時候您會想要根據項目的位置尋找這些項目。 您可能想要尋找第二個項目，或者想要尋找第三到第五個項目。  
  
 XPath 運算式為：  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 以延遲的方式撰寫這個 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢的方法有兩種。 您可以使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 運算子，或者，您可以使用採用索引的 <xref:System.Linq.Enumerable.Where%2A> 多載。 當您使用 <xref:System.Linq.Enumerable.Where%2A> 多載時，您可以使用採用兩個引數的 Lambda 運算式。 下列範例顯示根據位置進行選擇的兩種方法。  
  
## <a name="example"></a>範例  
 這個範例會尋找第二到第四個 `Test` 項目。 結果為項目的集合。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：測試組態 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)。  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
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
 [LINQ to XML (Visual Basic) 的 XPath 使用者適用的](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
