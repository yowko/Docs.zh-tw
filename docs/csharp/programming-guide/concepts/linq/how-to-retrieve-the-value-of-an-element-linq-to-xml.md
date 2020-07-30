---
title: '如何取出元素的值（LINQ to XML）（c #）'
description: 瞭解如何取得元素的值。 請參閱使用字串轉換、整數轉換和 Value 屬性的範例。
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301537"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>如何取出元素的值（LINQ to XML）（c #）

本文說明如何取得元素的值。 有兩種主要方式可取得此值：

- 將 <xref:System.Xml.Linq.XElement> 或轉換 <xref:System.Xml.Linq.XAttribute> 成所需的類型。 然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別，並將其指派給您的變數。

- 使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 或 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> 屬性。 您也可以使用這些屬性來設定值。

使用 c #，轉換通常是較好的方法。 如果您將專案或屬性轉換成可為 null 的實值型別，則在抓取可能或可能不存在的專案（或屬性）值時，程式碼會比較容易寫入。 本文中的[最後一個範例](#element-might-not-exist-example)示範當元素可能不存在時，轉換會比較簡單。 不過，您無法像透過 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性般，透過轉型設定項目的內容。  
  
## <a name="string-cast-example"></a>字串轉換範例  
 若要取出元素的值，請將 <xref:System.Xml.Linq.XElement> 物件轉換成您想要的類型。 您可以將元素轉換成字串，如下所示：  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a>整數轉換範例  
 您也可以將項目轉型為非字串的型別。 例如，如果您有包含整數的項目，您可以將其轉型為 `int`，如下列程式碼所示：  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會針對下列資料類型提供明確轉換運算子：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會提供 <xref:System.Xml.Linq.XAttribute> 物件相同的轉換運算子。  
  
## <a name="value-property-example"></a>Value 屬性範例  
 您可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來擷取項目的內容：  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 這個範例會產生下列輸出：  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a>元素可能不存在範例
 有時候您會嘗試抓取元素的值，即使您不確定它是否存在。 在此情況下，當您將轉換專案指派給可為 null 的參考型別或可為 null 的實值型別時，如果專案不存在，則指派的變數會設定為 `null` 。 下列程式碼顯示，項目可能存在或可能不存在時，使用轉型比使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性更為容易。  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 此程式碼會產生下列輸出：  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 一般而言，使用轉換擷取元素及屬性內容時，您可以撰寫較簡易的程式碼。  
  
## <a name="see-also"></a>另請參閱

- [LINQ to XML 座標軸 (C#)](./linq-to-xml-axes-overview.md)
