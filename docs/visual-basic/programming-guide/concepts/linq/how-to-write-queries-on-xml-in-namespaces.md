---
title: HOW TO：命名空間 (Visual Basic) 中的 XML 撰寫查詢
ms.date: 07/20/2015
ms.assetid: 7d4131b5-3288-414f-b77c-b2edc2a1f465
ms.openlocfilehash: 4efa1de254a0264752514c5ae6e601a66fa56f95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833434"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-visual-basic"></a>HOW TO：命名空間 (Visual Basic) 中的 XML 撰寫查詢
若要撰寫命名空間 (Namespace) 中的 XML 查詢，您必須使用具有正確命名空間的 <xref:System.Xml.Linq.XName> 物件。  
  
 在 Visual Basic 中，最常見的方法是定義全域命名空間，然後使用利用全域命名空間的 XML 常值和 XML 屬性。 您可以定義預設的全域命名空間，在此情況下，XML 常值中的項目預設會在命名空間中。 或者，您可以利用前置詞定義全域命名空間，然後在 XML 常值和 XML 屬性中使用前置詞 (如有需要)。 如同 XML 的其他格式，這些屬性預設永遠在沒有命名空間中。  
  
 本主題中的第一組範例會示範如何在預設命名空間中建立 XML 樹狀結構。 第二組範例則示範如何在具有前置詞的命名空間中建立 XML 樹狀結構。  
  
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
 不過，在 Visual Basic 中，針對使用具有前置詞之命名空間的 XML 樹狀結構撰寫查詢與查詢預設命名空間中的 XML 樹狀結構相當不同。 一般而言，您會使用 `Imports` 陳述式來匯入具有前置詞的命名空間。 然後，當您建構 XML 樹狀時，就會將此前置詞用於項目和屬性名稱中。 此外，在使用 XML 屬性來查詢 XML 樹狀時，您也會使用此前置詞。  
  
 下列範例會建立位於命名空間中，具有前置詞的 XML 樹狀。 接著，它會擷取項目的集合。  
  
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

- [處理 XML 命名空間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
