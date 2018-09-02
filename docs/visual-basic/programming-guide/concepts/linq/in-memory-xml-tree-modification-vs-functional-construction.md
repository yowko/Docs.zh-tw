---
title: 記憶體中 XML 樹狀修改與函數式建構 (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 71b8799d4da2f8f4fb10bdec6ca7cfcec76e036a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452777"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a>記憶體中 XML 樹狀修改與函數式建構 (LINQ to XML) (Visual Basic)
就地修改 XML 樹狀結構是變更 XML 文件組織結構的傳統方式。 一般應用程式會將文件載入到資料存放區，例如 DOM 或 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]；使用程式設計介面插入節點、刪除節點或變更節點的內容；然後將 XML 儲存到檔案或透過網路傳輸。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可啟用在許多案例中有用的其他方法：「函數式建構」。 功能結構會將修改資料視為轉換的問題，而不是資料存放區的詳細管理。 如果您可以表示資料，並將其有效地從一個表單轉換到另一個表單，結果會與您取得一個資料存放區，然後以相同的方式管理該資料存放區取得其他組織結構相同。 功能結構方法的關鍵在於將查詢結果傳遞到 <xref:System.Xml.Linq.XDocument> 和 <xref:System.Xml.Linq.XElement> 建構函式。  
  
 在許多情況下，您可以用管理資料存放區的少數時間撰寫轉換程式碼，而且該程式碼更穩定、更容易維護。 在這些情況下，即使轉換方法可以取得更大的處理能力，這都是更有效的修改資料方式。 在許多情況下，如果開發人員熟悉功能性方法，產生的程式碼較容易了解。 尋找修改樹狀結構每個部分的程式碼非常容易。  
  
 您就地修改 XML 樹狀結構的方法對於許多 DOM 程式設計人員而言更為熟悉，而使用功能性方法撰寫的程式碼對於還不了解該方法的開發人員而言，似乎比較不熟悉。 如果您必須針對大型 XML 樹狀結構進行小小的修改，您就地修改樹狀結構的方法在大部分的情況下，將會需要較少的 CPU 時間。  
  
 本主題提供利用兩種方法實作的範例。  
  
## <a name="transforming-attributes-into-elements"></a>將屬性轉換為項目  
 針對這個範例，假設您想要修改下列簡單的 XML 文件，讓屬性變成項目。 這個主題會先呈現傳統的就地修改方法。 然後它會顯示功能結構方法。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>修改 XML 樹狀結構  
 您可以撰寫特定的程序性程式碼以便從屬性建立項目，然後刪除該屬性，如下所示：  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 此程式碼會產生下列輸出：  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>功能結構方法  
 相較之下，功能性方法會從來源樹狀結構挑選並選擇項目和屬性，然後在加入到新的樹狀結構時，適當地加以轉換，藉以包含形成新樹狀結構的程式碼。 功能性方法的外觀如下所示：  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 這個範例會與第一個範例輸出相同的 XML。 但是請注意，您實際上可以用功能性方法查看所產生的新 XML 結構。 您可以查看 `Root` 項目的建立、從來源樹狀結構提取 `Child1` 項目的程式碼，以及將屬性從來源樹狀結構轉換到新樹狀結構中的項目之程式碼。  
  
 在這個情況下，比起第一個範例，功能性範例更短而且更簡單。 不過，如果您有針對 XML 樹狀結構進行許多變更，非功能性方法將會變成相當複雜，而且有些遲鈍。 相反地，使用功能性方法時，您仍然可以在適當地內嵌查詢和運算式，只形成所需的 XML，以便在所需的內容中提取。 功能性方法會產生容易維護的程式碼。  
  
 請注意，在這個情況下，功能性方法可能不會實際與樹狀結構管理方法一起執行。 主要的問題在於功能性方法會建立更多短期存在的物件。 不過，如果使用功能性方法能讓程式設計人員的產能更大，進行取捨是有效的方法。  
  
 這是非常簡單的範例，但是它有助於顯示兩種方法間的觀點差異。 功能性方法在轉換大型 XML 文件時，會產生較大的產能。  
  
## <a name="see-also"></a>另請參閱  
 [修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
