---
title: "如何︰ 在命名空間 (Visual Basic) 中的 XML 上撰寫查詢 |Microsoft 文件"
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
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5af26b7ec0a2ab465917cd0ee62f65a97f5f0e40
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>如何︰ 在命名空間 (Visual Basic) 中的 XML 上撰寫查詢
若要撰寫查詢的 XML 命名空間中，您必須使用<xref:System.Xml.Linq.XName>具有正確的命名空間的物件。</xref:System.Xml.Linq.XName>  
  
 在 Visual Basic 中，最常見的方法是定義全域命名空間，然後使用利用全域命名空間的 XML 常值和 XML 屬性。 您可以定義預設的全域命名空間，在此情況下，XML 常值中的項目預設會在命名空間中。 或者，您可以利用前置詞定義全域命名空間，然後在 XML 常值和 XML 屬性中使用前置詞 (如有需要)。 如同 XML 的其他格式，這些屬性預設永遠在沒有命名空間中。  
  
 第一個集合，此主題中的範例示範如何在預設的命名空間中建立 XML 樹狀結構。 第二個集合會顯示如何在具有前置詞的命名空間中建立 XML 樹狀結構。  
  
## <a name="example"></a>範例  
 下列範例會建立位於預設命名空間中的 XML 樹狀。 接著，它會擷取項目的集合。  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>範例  
 不過，在 Visual Basic 中，針對使用具有前置詞之命名空間的 XML 樹狀結構撰寫查詢與查詢預設命名空間中的 XML 樹狀結構相當不同。 一般而言，您會使用 `Imports` 陳述式來匯入具有前置詞的命名空間。 然後，當您建構 XML 樹狀結構時，就會將此前置詞用於項目和屬性名稱中。 此外，在使用 XML 屬性來查詢 XML 樹狀結構時，您也會使用此前置詞。  
  
 下列範例會建立位於命名空間中，具有前置詞的 XML 樹狀結構。 接著，它會擷取項目的集合。  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>1</aw:Child>  
                <aw:Child>2</aw:Child>  
                <aw:Child>3</aw:Child>  
                <aw:AnotherChild>4</aw:AnotherChild>  
                <aw:AnotherChild>5</aw:AnotherChild>  
                <aw:AnotherChild>6</aw:AnotherChild>  
            </aw:Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
            From el In root.<aw:Child> _  
            Select el  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
    End Sub  
End Module  
```  
  
 這個範例會產生下列輸出：  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>另請參閱  
 [處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
