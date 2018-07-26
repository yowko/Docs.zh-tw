---
title: 如何：使用 XPath 查詢 LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: a02149719afa19350a9baf15c41bd3548daa1344
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959851"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>如何：使用 XPath 查詢 LINQ to XML (C#)
本主題說明可讓您使用 XPath 查詢 XML 樹狀結構的擴充方法。 如需有關使用這些擴充方法的詳細資訊，請參閱 <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。  
  
 除非您已經有非常特定的理由要使用 XPath 查詢 (例如，廣泛使用舊版程式碼)，否則，不建議搭配 LINQ to XML 使用 XPath。 XPath 查詢將不會與 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢一起執行。  
  
## <a name="example"></a>範例  
 下列範例會建立小型 XML 樹狀結構，並使用 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 來選取一組項目。  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>請參閱  
 [進階查詢技術 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
