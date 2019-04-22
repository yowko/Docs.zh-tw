---
title: 函數式建構 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f677c0d0e204b5d12718701ab70b8a3c1bd3530c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816547"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a>函數式建構 (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 提供一種強大的方式來建立 XML 元素，稱為「函數式建構」。 功能結構是在單一陳述式中建立 XML 樹狀結構的能力。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 程式介面有數種主要功能可以使用功能結構：  
  
-   <xref:System.Xml.Linq.XElement> 建構函式會針對內容採用各種引數類型。 例如，您可以傳遞變成子項目的其他 <xref:System.Xml.Linq.XElement> 物件。 您可以傳遞變成項目屬性的 <xref:System.Xml.Linq.XAttribute> 物件。 或者，您可以傳遞轉換成字串的其他類物件型，然後變成項目的文字內容。  
  
-   <xref:System.Xml.Linq.XElement> 建構函式會採用 `params` 類型的 <xref:System.Object> 陣列，讓您可以將任何數目的物件傳遞到建構函式。 這可讓您建立包含複雜內容的項目。  
  
-   如果物件實作 <xref:System.Collections.Generic.IEnumerable%601>，系統列舉物件中的集合，並加入集合中的所有項目。 如果集合包含 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件，系統會個別加入集合中的每個項目。 這是非常重要的，因為這可讓您將 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的結果傳遞到建構函式中。  
  
 以下是一個範例：  
  
 這些功能可讓您撰寫程式碼使用 XML 常值，來建立 XML 樹狀結構，以及撰寫程式碼，會使用結果[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢當您建立 XML 樹狀結構：  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 這個範例會產生下列輸出：  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>另請參閱

- [建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
