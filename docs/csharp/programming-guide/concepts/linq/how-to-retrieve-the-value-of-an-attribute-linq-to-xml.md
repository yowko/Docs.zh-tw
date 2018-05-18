---
title: 如何：擷取屬性的值 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 224ba9ba47d68afd7c29d0f33fe20d290d0b5ef5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>如何：擷取屬性的值 (LINQ to XML) (C#)
這個主題顯示如何取得屬性的值。 有兩個主要方式：您可以將 <xref:System.Xml.Linq.XAttribute> 轉型為所需的型別；然後，明確的轉換運算子會將項目或屬性的內容轉換為指定的型別。 或者，您可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性。 不過，轉型通常是較好的方法。 如果您要將屬性轉型為可為 Null 的型別 (Nullable Type)，擷取可能存在或可能不存在之屬性的值時，程式碼比較容易撰寫。 如需這項技術的範例，請參閱[如何：擷取項目的值 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。  
  
## <a name="example"></a>範例  
 若要擷取屬性的值，只要將 <xref:System.Xml.Linq.XAttribute> 物件轉型為您所需的型別即可。  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 這個範例會產生下列輸出：  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>範例  
 下列範例顯示如何擷取屬性位於命名空間之屬性的值。 如需詳細資訊，請參閱[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 這個範例會產生下列輸出：  
  
```  
abcde  
```  
  
## <a name="see-also"></a>請參閱  
 [LINQ to XML 座標軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
