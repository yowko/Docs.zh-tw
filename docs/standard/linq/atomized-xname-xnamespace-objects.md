---
title: 不可部分完成的 XName 和 XNamespace 物件-LINQ to XML
description: 瞭解相同名稱的不可部分完成的 XName 和 XNamespace 物件如何共用實例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc2be4d408385936598d94d34f9b452d950516d3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552284"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml"></a> (LINQ to XML) 的不可部分完成的 XName 和 XNamespace 物件

<xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 物件是「不可部分完成」** 的物件。也就是說，如果它們包含相同的限定名稱，它們就會參考相同的物件。 這會產生查詢的效能優勢：當您比較兩個不可部分完成的名稱是否相等時，基礎中繼語言只需要判斷兩個參考是否指向相同的物件。 基礎程式碼不需要執行字串比較，這需要較長的時間。

## <a name="atomization-semantics"></a>不可部分完成語義

不可部分完成表示如果兩個 <xref:System.Xml.Linq.XName> 物件具有相同的本機名稱，而且它們在相同的命名空間中，它們就會共用相同的實例。 同樣地，如果兩個 <xref:System.Xml.Linq.XNamespace> 物件具有相同的命名空間 URI，它們就會共用相同的執行個體。

若要讓某個類別 (Class) 啟用不可部分完成的物件，此類別的建構函式 (Constructor) 必須是私用 (Private) 而非公用 (Public)。 這是因為如果建構函式為公用，您就可以建立非不可部分完成的物件。 <xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 類別會實作隱含轉換運算子，將字串轉換成 <xref:System.Xml.Linq.XName> 或 <xref:System.Xml.Linq.XNamespace>。 這就是您取得這些物件之執行個體的方式。 因為無法存取函式，所以您無法使用函式來取得實例。

<xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>此外，也會執行相等和不等比較運算子，以判斷要比較的兩個物件是否為相同實例的參考。

## <a name="example-create-objects-and-show-that-identical-names-share-an-instance"></a>範例：建立物件，並顯示相同的名稱共用實例

下列程式碼會建立一些 <xref:System.Xml.Linq.XElement> 物件，並且示範相同的名稱會共用相同的執行個體。

```csharp
XElement r1 = new XElement("Root", "data1");
XElement r2 = XElement.Parse("<Root>data2</Root>");

if ((object)r1.Name == (object)r2.Name)
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");
else
    Console.WriteLine("Different");

XName n = "Root";

if ((object)n == (object)r1.Name)
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");
else
    Console.WriteLine("Different");
```

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

```output
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

如先前所述，不可部分完成之物件的優點在於，當您使用其中一個採取 <xref:System.Xml.Linq.XName> 當做參數的座標軸方法時，此座標軸方法只需要判斷兩個名稱是否參考相同的執行個體，即可選取所需的項目。

下列範例會將 <xref:System.Xml.Linq.XName> 傳遞至 <xref:System.Xml.Linq.XContainer.Descendants%2A> 方法呼叫，而且這樣做會由於不可部分完成模式而具有較佳的效能。

```csharp
XElement root = new XElement("Root",
    new XElement("C1", 1),
    new XElement("Z1",
        new XElement("C1", 2),
        new XElement("C1", 1)
    )
);

var query = from e in root.Descendants("C1")
            where (int)e == 1
            select e;

foreach (var z in query)
    Console.WriteLine(z);
```

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
