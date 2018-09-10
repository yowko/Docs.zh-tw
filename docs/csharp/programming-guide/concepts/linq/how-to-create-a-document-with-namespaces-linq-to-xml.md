---
title: 如何：建立包含命名空間的文件 (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 5937639fc48b82ee155450a3eaa1c7715ee3f9b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43478022"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>如何：建立包含命名空間的文件 (C#) (LINQ to XML)
本主題顯示如何利用命名空間建立文件。  
  
## <a name="example"></a>範例  
 若要建立位於命名空間中的項目或屬性，您必須先宣告並初始化 <xref:System.Xml.Linq.XNamespace> 物件。 然後，您可以使用加法運算子多載來結合命名空間與本機名稱 (以字串表示)。  
  
 下列範例會使用一個命名空間建立文件。 根據預設，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會使用預設命名空間來序列化此文件。  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>範例  
 下列範例會使用一個命名空間建立文件。 該範例也會建立宣告具有命名空間前置詞之命名空間的屬性。 若要建立宣告具有前置詞之命名空間的屬性，您可以建立屬性，其中屬性的名稱是命名空間前置詞，而這個名稱位於 <xref:System.Xml.Linq.XNamespace.Xmlns%2A> 命名空間中。 這個屬性的值為命名空間的 URI。  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>範例  
 下列範例顯示如何建立包含兩個命名空間的文件。 一個是預設命名空間。 另一個是具有前置詞的命名空間。  
  
 藉由將命名空間屬性包含到根項目中，系統會序列化命名空間，讓 `http://www.adventure-works.com` 成為預設命名空間，而 `www.fourthcoffee.com` 則利用 "fc" 的前置詞序列化。 若要建立宣告預設命名空間的屬性，您可以建立名稱為 "xmlns"，而且沒有命名空間的屬性。 屬性的值為預設的命名空間 URI。  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
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
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a>範例  
 下列範例會建立包含兩個命名空間 (兩者皆擁有命名空間前置詞) 的文件。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
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
  
## <a name="example"></a>範例  
 達到相同結果的另一個方法是，使用擴充名稱來代替宣告和建立 <xref:System.Xml.Linq.XNamespace> 物件。  
  
 這個方法會有效能隱含作用。 每次您將包含展開名稱的字串傳遞到 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 時，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 就必須剖析名稱、尋找不可部分完成的命名空間，然後尋找不可部分完成的名稱。 這個程序會使用 CPU 時間。 如果效能對您很重要，您可能會想要明確宣告並使用 <xref:System.Xml.Linq.XNamespace> 物件。  
  
 如果效能是很重要的問題，請參閱[預先同質化 XName 物件 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) 以取得詳細資訊。  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>請參閱  
 [處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
