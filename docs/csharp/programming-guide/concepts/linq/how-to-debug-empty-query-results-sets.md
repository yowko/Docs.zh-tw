---
title: "如何：偵錯空的查詢結果集 (C#) | Microsoft Docs"
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
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: afa7e63f4224a91c072c99d04a4851d2548166e5
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-debug-empty-query-results-sets-c"></a>如何：偵錯空的查詢結果集 (C#)
查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。  
  
 本主題中的第一組範例會顯示將 XML 載入預設命名空間而且查詢錯誤的常見方式。  
  
 第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。  
  
 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
## <a name="example"></a>範例  
 此範例顯示 XML 在命名空間中的建立，以及傳回空結果集的查詢。  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 此範例會產生下列結果：  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>範例  
 此範例顯示 XML 在命名空間中的建立，以及編碼正確的查詢。  
  
 此方案是為了宣告及初始化 <xref:System.Xml.Linq.XNamespace> 物件，然後在指定 <xref:System.Xml.Linq.XName> 物件時使用此物件。 在本例中，<xref:System.Xml.Linq.XElement.Elements%2A> 的引數是 <xref:System.Xml.Linq.XName> 物件。  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 此範例會產生下列結果：  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>另請參閱  
 [基本查詢 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
