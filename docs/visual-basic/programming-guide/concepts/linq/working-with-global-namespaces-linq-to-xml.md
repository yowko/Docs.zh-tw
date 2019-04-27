---
title: 處理全域命名空間 (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: d8e74e949815d36f06f522460cc31ca6c3ccabb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908007"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a>處理全域命名空間 (Visual Basic) (LINQ to XML)
在 Visual Basic 中的 XML 常值的主要功能之一是能夠使用宣告 XML 命名空間`Imports`陳述式。 利用這個功能，您可以宣告使用前置詞的 XML 命名空間，或者，您可以宣告預設的 XML 命名空間。  
  
 這項功能在兩種情況下很有用。 第一，在 XML 常值中宣告的命名空間不會延續到內嵌的運算式中。 宣告全域命名空間會減少您必須做的工作量，以便搭配命名空間使用內嵌的運算式。 第二，您必須宣告全域命名空間，才能搭配 XML 使用命名空間。  
  
 您可以在專案層級宣告全域命名空間。 您也可以在複寫專案層級全域命名空間的模組層級宣告全域命名空間。 最後，您可以在 XML 常值中複寫全域命名空間。  
  
 使用位於全域宣告之命名空間中的 XML 常值或 XML 屬性時，您可以在 Visual Studio 中，將滑鼠停留在 XML 常值或屬性的擴充名稱上，藉以查看它們。 您將會在工具提示中看到擴充名稱。  
  
 您可以使用 <xref:System.Xml.Linq.XNamespace> 方法，取得對應到全域命名空間的 `GetXmlNamespace` 物件。  
  
## <a name="examples-of-global-namespaces"></a>全域命名空間的範例  
 下列範例會使用 `Imports` 陳述式宣告預設的全域命名空間，然後使用 XML 常值來初始化該命名空間中的 <xref:System.Xml.Linq.XElement> 物件：  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 下列範例會宣告具有前置詞的全域命名空間，然後使用 XML 常值來初始化項目：  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a>全域命名空間與內嵌的運算式  
 在 XML 常值中宣告的命名空間不會延續到內嵌的運算式中。 下列範例會宣告預設的命名空間。 接著，它會使用 `Child` 項目的內嵌運算式。  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 如同您所見，所產生的 XML 包括預設命名空間的宣告，因此 `Child` 項目不在任何命名空間中。  
  
 您可以在內嵌的運算式中重新宣告命名空間，如下所示：  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 不過，這種方法在使用上較為麻煩，所以全域預設命名空間仍然是較佳的方法。 透過全域預設命名空間，您可以使用 XML 常值，而不需宣告命名空間。 所產生的 XML 將會位於全域宣告的預設命名空間中。  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a>搭配 XML 屬性使用命名空間  
 如果您使用命名空間中的 XML 樹狀，而且您使用 XML 屬性，則您必須使用全域命名空間，XML 屬性才會也在正確的命名空間中。 下列範例會在命名空間中宣告 XML 樹狀。 接著，它會列印 `Child` 項目的計數。  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 這個範例表示沒有 `Child` 項目。 它會產生下列輸出：  
  
```  
0  
```  
  
 但是，如果您要宣告預設的全域命名空間，則 XML 常值和 XML 屬性都會位於預設的全域命名空間中：  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 這個範例表示有一個 `Child` 項目， 它會產生下列輸出：  
  
```  
1  
```  
  
 如果您要宣告具有前置詞的全域命名空間，可以將前置詞同時用於 XML 常值和 XML 屬性：  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a>XNamespace 和全域命名空間  
 您可以使用 <xref:System.Xml.Linq.XNamespace> 方法，取得 `GetXmlNamespace` 物件：  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a>另請參閱

- [處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
