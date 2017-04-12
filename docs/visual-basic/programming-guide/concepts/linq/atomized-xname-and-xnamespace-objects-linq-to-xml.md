---
title: "不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b08f3116f5acb404cf2c33072ec31fbaada4e7cb
ms.lasthandoff: 03/13/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>不可部分完成的 XName 和 XNamespace 物件 (LINQ to XML) (Visual Basic)
<xref:System.Xml.Linq.XName>和<xref:System.Xml.Linq.XNamespace>物件*不可部分完成*; 也就是說，如果它們包含相同的限定的名稱時，它們參考相同的物件。</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName> 這會針對查詢產生效能優勢：當您比較兩個不可部分完成的名稱是否相等時，基礎中繼語言 (Intermediate Language) 只需要判斷這兩個參考是否指向相同的物件即可。 基礎程式碼不需要進行耗時的字串比較。  
  
## <a name="atomization-semantics"></a>不可部分完成語意  
 不可部分完成是表示，如果兩個<xref:System.Xml.Linq.XName>物件具有相同的本機名稱，而且它們位於相同的命名空間，它們共用相同的執行個體。</xref:System.Xml.Linq.XName> 相同地，如果兩個<xref:System.Xml.Linq.XNamespace>物件具有相同的命名空間 URI，它們會共用相同的執行個體。</xref:System.Xml.Linq.XNamespace>  
  
 若要讓某個類別 (Class) 啟用不可部分完成的物件，此類別的建構函式 (Constructor) 必須是私用 (Private) 而非公用 (Public)。 這是因為如果建構函式為公用，您就可以建立非不可部分完成的物件。 <xref:System.Xml.Linq.XName>和<xref:System.Xml.Linq.XNamespace>類別會實作隱含轉換運算子，將成為<xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>.</xref:System.Xml.Linq.XNamespace>或</xref:System.Xml.Linq.XName>字串轉換</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName> 這就是您取得這些物件之執行個體的方式。 您無法使用建構函式來取得執行個體，因為無法存取建構函式。  
  
 <xref:System.Xml.Linq.XName>和<xref:System.Xml.Linq.XNamespace>也會實作等號和不等比較運算子，以判斷兩個物件是否要比較相同的執行個體的參考。</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>  
  
## <a name="example"></a>範例  
 下列程式碼會建立一些<xref:System.Xml.Linq.XElement>物件，並且示範相同的名稱會共用相同的執行個體。</xref:System.Xml.Linq.XElement>  
  
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
  
 如先前所述，不可部分完成之物件的優點是，當您使用需要的座標軸方法的其中一個<xref:System.Xml.Linq.XName>做為參數，此座標軸方法只需要判斷兩個名稱參考相同的執行個體，來選取所需的項目。</xref:System.Xml.Linq.XName>  
  
 下列範例會傳遞<xref:System.Xml.Linq.XName>至<xref:System.Xml.Linq.XContainer.Descendants%2A>方法呼叫，則會由於不可部分完成模式有更佳的效能。</xref:System.Xml.Linq.XContainer.Descendants%2A> </xref:System.Xml.Linq.XName>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 這個範例會產生下列輸出：  
  
```  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>另請參閱  
 [效能 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
