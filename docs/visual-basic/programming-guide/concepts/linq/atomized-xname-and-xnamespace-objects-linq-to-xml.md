---
title: 不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: fe0c4429c89e0028b3b012c87684bd14048de27a
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843438"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)

<xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 物件是「不可部分完成」的物件。也就是說，如果它們包含相同的限定名稱，它們就會參考相同的物件。 這會針對查詢產生效能優勢：當您比較兩個不可部分完成的名稱是否相等時，基礎中繼語言只需要判斷這兩個參考是否指向相同的物件即可。 基礎程式碼不需要進行耗時的字串比較。

## <a name="atomization-semantics"></a>不可部分完成語意

不可部分完成是表示，如果兩個 <xref:System.Xml.Linq.XName> 物件具有相同的本機名稱，而且位於相同的命名空間 (Namespace) 中，它們就會共用相同的執行個體 (Instance)。 同樣地，如果兩個 <xref:System.Xml.Linq.XNamespace> 物件具有相同的命名空間 URI，它們就會共用相同的執行個體。

若要讓某個類別 (Class) 啟用不可部分完成的物件，此類別的建構函式 (Constructor) 必須是私用 (Private) 而非公用 (Public)。 這是因為如果建構函式為公用，您就可以建立非不可部分完成的物件。 <xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 類別會實作隱含轉換運算子，將字串轉換成 <xref:System.Xml.Linq.XName> 或 <xref:System.Xml.Linq.XNamespace>。 這就是您取得這些物件之執行個體的方式。 您無法使用建構函式來取得執行個體，因為無法存取建構函式。

<xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 也會實作等號比較運算子和不等比較運算子，以便判斷所比較的兩個物件是否為相同執行個體的參考。

## <a name="example"></a>範例

下列程式碼會建立一些 <xref:System.Xml.Linq.XElement> 物件，並且示範相同的名稱會共用相同的執行個體。

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

這個範例會產生下列輸出：

```
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

如先前所述，不可部分完成之物件的優點在於，當您使用其中一個採取 <xref:System.Xml.Linq.XName> 當做參數的座標軸方法時，此座標軸方法只需要判斷兩個名稱是否參考相同的執行個體，即可選取所需的項目。

下列範例會將 <xref:System.Xml.Linq.XName> 傳遞至 <xref:System.Xml.Linq.XContainer.Descendants%2A> 方法呼叫，而且這樣做會由於不可部分完成模式而具有較佳的效能。

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

這個範例會產生下列輸出：

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a>另請參閱

- [效能 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
