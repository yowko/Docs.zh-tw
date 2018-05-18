---
title: 如何：控制命名空間前置字元 (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: af864139d56bd3ebb22cca6369b82539b9d007da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>如何：控制命名空間前置字元 (C#) (LINQ to XML)
這個主題描述如何在序列化 XML 樹狀時控制命名空間前置詞。  
  
 在許多情況下，不需要控制命名空間前置詞。  
  
 不過，某些 XML 程式設計工具需要命名空間前置詞的特定控制權。 例如，您所操作的 XSLT 樣式表或 XAML 文件可能包含參考特定命名空間前置詞的內嵌 XPath 運算式。在此情況下，請務必使用這些特定前置詞來序列化文件。  
  
 這就是控制命名空間前置詞的最常見原因。  
  
 控制命名空間前置詞的另一個常見原因是，您要讓使用者手動編輯 XML 文件，而且您要建立使用者便於輸入的命名空間前置詞。 例如，您可能要產生 XSD 文件。 若要轉換結構描述，建議您使用 `xs` 或 `xsd` 做為結構描述命名空間的前置詞。  
  
 若要控制命名空間前置詞，您可插入宣告命名空間的屬性。 如果您宣告具有特定前置詞的命名空間，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 將會在序列化時，嘗試允許命名空間前置詞。  
  
 若要建立宣告具有特定前置詞之命名空間的屬性，您可以建立屬性，其中之屬性名稱的命名空間為 <xref:System.Xml.Linq.XNamespace.Xmlns%2A>，而屬性的名稱為命名空間前置詞。 屬性的值為命名空間的 URI。  
  
## <a name="example"></a>範例  
 這個範例會宣告兩個命名空間。 它會指定 `http://www.adventure-works.com` 命名空間的前置詞為 `aw`，而 `www.fourthcoffee.com` 命名空間的前置詞為 `fc`。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>請參閱  
 [處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
