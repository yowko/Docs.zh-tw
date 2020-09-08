---
title: 如何在 Visual Basic LINQ to XML 中建立具有命名空間的檔
description: 在 Visual Basic 中使用 XML 常值，以建立具有前置詞的預設命名空間或命名空間的檔。
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552275"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a>如何在 Visual Basic (LINQ to XML) 中建立具有命名空間的檔

本文說明如何在 Visual Basic 中建立包含命名空間的檔。

在 Visual Basic 中使用 XML 常值時，使用者可以定義一個預設的 XML 全域命名空間。 這個命名空間同時為 XML 常值和 XML 屬性的預設命名空間。 XML 預設命名空間可在專案層級或檔案層級定義。 如果是在檔案層級定義的，它會覆寫專案層級的預設命名空間。

您也可以定義其他命名空間，並為這些命名空間指定命名空間前置詞。 您可以使用 `Imports` 關鍵字來定義這兩種類型的命名空間。

如需詳細資訊，請參閱 [Visual Basic 中的 XML 常](xml-literals.md)值。

請注意，XML 預設命名空間僅適用於項目，而不適用於屬性。 預設命名空間中的屬性預設為。 不過，您可以使用命名空間前置詞，將屬性放到命名空間中。

## <a name="example-create-a-document-that-has-a-namespace"></a>範例：建立具有命名空間的檔

此範例會建立包含命名空間的文件。

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

這個範例會產生下列輸出：

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>範例：建立具有兩個命名空間的檔，一個具有前置詞

此範例會建立包含兩個命名空間的檔。 其中一個是預設命名空間，另一個則有前置詞。

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

這個範例會產生下列輸出：

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>範例：建立具有兩個命名空間的檔，兩者都有首碼

下列範例會建立包含兩個命名空間的檔，這兩個命名空間都具有命名空間前置詞。

當序列化 XML 樹狀結構時，LINQ to XML 會發出必要的命名空間宣告，讓每個專案都在其指定的命名空間中。

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

End Module
```

這個範例會產生下列輸出：

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a>另請參閱

- [命名空間總覽](namespaces-overview.md)
