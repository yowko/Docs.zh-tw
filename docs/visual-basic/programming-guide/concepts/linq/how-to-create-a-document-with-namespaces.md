---
title: 如何：建立包含命名空間的文件 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 204d8a9cbb6ce47c6334c7309d27910c75b90ae0
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754169"
---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>如何：建立包含命名空間的文件 (LINQ to XML) (Visual Basic)
本主題顯示如何在 Visual Basic 中建立具有命名空間 (Namespace) 的文件。  
  
 在 Visual Basic 中使用 XML 常值時，使用者可以定義一個預設的 XML 全域命名空間。 這個命名空間同時為 XML 常值和 XML 屬性的預設命名空間。 XML 預設命名空間可在專案層級或檔案層級定義。 如果是在檔案層級定義，該命名空間會覆寫專案層級的預設命名空間。  
  
 您也可以定義其他命名空間，並為這些命名空間指定命名空間前置詞。  
  
 您可以使用 `Imports` 關鍵字，同時定義預設命名空間與具有前置詞的命名空間。  
  
 如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的 XML 常值簡介](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md)。  
  
 請注意，XML 預設命名空間僅適用於項目，而不適用於屬性。 根據預設，屬性一定會在沒有命名空間中。 不過，您可以使用命名空間前置詞，將屬性放到命名空間中。  
  
## <a name="example"></a>範例  
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
  
## <a name="example"></a>範例  
 此範例會建立包含兩個命名空間 (其中一個為預設命名空間) 的文件。  
  
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
  
## <a name="example"></a>範例  
 下列範例會建立包含多個命名空間 (兩者皆擁有命名空間前置詞) 的文件。  
  
 序列化 XML 樹狀結構時，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會在必要時發出命名空間宣告，讓每個項目都位於其指定的命名空間中。  
  
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
 [處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
