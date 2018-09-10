---
title: 如何：擷取項目的值 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 7537c111e7d869f8a3e2458706864960820f9764
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185385"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>如何：擷取項目的值 (LINQ to XML) (C#)
本主題顯示如何取得項目的值。 以下有兩種主要的方式可達成此目標。 其中一種方式為，將 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別。 然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別，並將其指派給您的變數。 或者，您可以使用 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性或 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> 屬性。  
  
 不過，使用 C# 時，轉型 (Casting) 通常是較好的方法。 如果您要將項目或屬性轉型為可為 Null 的型別 (Nullable Type)，擷取可能存在或可能不存在之項目 (或屬性) 的值時，較容易撰寫程式碼。 本主題中的最後一個範例會示範這個情況。 不過，您無法像透過 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 屬性般，透過轉型設定項目的內容。  
  
## <a name="example"></a>範例  
 若要擷取項目的值，您只要將 <xref:System.Xml.Linq.XElement> 物件轉型為所需的型別即可。 您永遠可以將項目轉型為字串，如下所示：  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 這個範例會產生下列輸出：  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>範例  
 您也可以將項目轉型為非字串的型別。 例如，如果您有包含整數的項目，您可以將其轉型為 `int`，如下列程式碼所示：  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 這個範例會產生下列輸出：  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會針對下列資料類型提供明確轉換運算子：`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID` 和 `GUID?`。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會提供 <xref:System.Xml.Linq.XAttribute> 物件相同的轉換運算子。  
  
## <a name="example"></a>範例  
 您可以使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性來擷取項目的內容：  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 這個範例會產生下列輸出：  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>範例  
 即使您不確定項目是否存在，您有時候還是會嘗試擷取項目的值。 在這個情況下，當您將轉換的項目指派給可為 Null 的型別 (`string` 或 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中其中一個可為 Null 的型別) 時，如果項目不存在，被指派的變數只會設定為 `null`。 下列程式碼顯示，項目可能存在或可能不存在時，使用轉型比使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性更為容易。  
  
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
  
```  
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
  
## <a name="see-also"></a>請參閱

- [LINQ to XML 座標軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
