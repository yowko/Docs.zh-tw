---
title: '如何在 c # 中建立具有命名空間的檔-LINQ to XML'
description: '使用 c # 中的 XNamespace 物件來建立檔，其具有具有前置詞的預設命名空間或命名空間。'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 3ec9624bcc599a73a6872e5c4c79504a1a4b4380
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552278"
---
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a>如何在 c # 中建立具有命名空間的檔 (LINQ to XML) 

本文說明如何在 c # 中建立具有命名空間的檔。

## <a name="example-declare-and-initialize-a-default-namespace"></a>範例：宣告和初始化預設命名空間

若要建立位於命名空間中的元素或屬性，您必須先宣告和初始化 <xref:System.Xml.Linq.XNamespace> 物件。 然後，您可以使用加法運算子多載來結合命名空間與本機名稱 (以字串表示)。

下列範例會使用一個命名空間建立文件。 根據預設，LINQ to XML 會將此檔序列化為預設命名空間。

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

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a>範例：建立具有命名空間和屬性的檔

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

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>範例：建立具有兩個命名空間的檔，一個具有前置詞

下列範例顯示如何建立包含兩個命名空間的文件。 其中一個是預設命名空間，另一個是具有前置詞的命名空間。

藉由將命名空間屬性包含在根項目中，就會將命名空間序列化為 `http://www.adventure-works.com` 預設命名空間，並 `www.fourthcoffee.com` 使用的前置詞進行序列化 `fc` 。 若要建立宣告預設命名空間的屬性，您可以建立名稱 `xmlns` 不含命名空間的屬性。 屬性的值為預設的命名空間 URI。

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

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>範例：建立具有兩個命名空間的檔，兩者都有首碼

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

## <a name="example-create-a-namespace-using-expanded-names"></a>範例：使用展開的名稱建立命名空間

達到相同結果的另一個方法是，使用擴充名稱來代替宣告和建立 <xref:System.Xml.Linq.XNamespace> 物件。

這個方法會有效能隱含作用。 每次您將包含擴充名稱的字串傳遞至 LINQ to XML 時，LINQ to XML 必須剖析名稱、尋找不可部分完成的命名空間，然後尋找不可部分完成的名稱。 這個程序會使用 CPU 時間。 如果效能對您很重要，您可能會想要明確宣告並使用 <xref:System.Xml.Linq.XNamespace> 物件。

如果效能是很重要的問題，請參閱 [預先不可部分完成的 XName 物件](pre-atomization-xname-objects.md) ，以取得詳細資訊。

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

## <a name="see-also"></a>另請參閱

- [命名空間總覽](namespaces-overview.md)
