---
title: 如何：控制命名空間前置字元 (Visual Basic) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: f60f90ef6742dfd725f51ff7e760436117346e85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>如何：控制命名空間前置字元 (Visual Basic) (LINQ to XML)
這個主題描述如何控制命名空間前置詞。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 這個範例會宣告兩個命名空間。 它會指定`http://www.adventure-works.com`命名空間具有前置詞`aw`，而且`www.fourthcoffee.com`命名空間具有的前置詞`fc`。  
  
### <a name="code"></a>程式碼  
  
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
  
### <a name="comments"></a>註解  
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
 [處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
