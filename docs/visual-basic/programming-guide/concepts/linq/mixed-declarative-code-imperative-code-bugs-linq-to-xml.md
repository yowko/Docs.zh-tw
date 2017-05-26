---
title: "混合的宣告式程式碼命令式程式碼 Bug (LINQ to XML) (Visual Basic) |Microsoft 文件"
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
ms.assetid: f12b1ab4-bb92-4b92-a648-0525e45b3ce7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 08edcabc3f0238c499f87c713f205ee5a517a1ea
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-visual-basic"></a>宣告式程式碼/命令式混合程式碼 Bug (LINQ to XML) (Visual Basic)
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 包含各種方法，可讓您直接修改 XML 樹狀結構。 您可以加入項目、刪除項目、變更項目的內容、加入屬性等等。 這個程式發展介面述[修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)。 如果您要逐一查看其中一個座標軸，例如<xref:System.Xml.Linq.XContainer.Elements%2A>，並逐一查看軸，您要修改 XML 樹狀結構，您可以得到一些奇怪的 bug。</xref:System.Xml.Linq.XContainer.Elements%2A>  
  
 這種問題有時候稱為「幽靈問題」。  
  
## <a name="definition-of-the-problem"></a>問題的定義  
 當您使用可逐一查看集合的 LINQ 撰寫特定程式碼時，您要以宣告式方法撰寫程式碼。 它會比較類似於描述*什麼*您，而不是要*如何*您想要完成工作。 如果您撰寫的程式碼可 1) 取得第一個項目、2) 針對某些條件進行測試、3) 加以修改，以及 4) 將其放回清單中，則這會是命令性程式碼。 您在告訴電腦*如何*做要完成的動作。  
  
 在相同的運算中混用這些程式碼樣式就是導致問題發生的原因。 請考慮下列事項：  
  
 假設您有一個連結的清單，其中包含三個項目 (a、b 和 c)：  
  
 `a -> b -> c`  
  
 現在，假設您要移動連結的清單，以加入三個新項目 (a'、b' 和 c')。 您希望所產生的連結清單如下所示：  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 因此，您可以撰寫逐一查看清單的程式碼，然後針對每個項目，將新項目加入到清單的後面。 結果是，您的程式碼將會先看到 `a` 項目，然後在其後插入 `a'`。 現在，您的程式碼將會移到清單中的下一個節點，而這個節點現在是 `a'`！ 它會將新項目適當地加入到清單 `a''` 中。  
  
 您在現實世界會如何解決這個問題？ 您可以複製原始的連結清單，然後建立一個全新的清單。 或者，如果您要撰寫純命令性程式碼，您可能會找到第一個項目、加入新項目，然後在連結的清單中往前兩次，超過您剛才加入的項目。  
  
## <a name="adding-while-iterating"></a>反覆運算時加入  
 例如，假設您要針對樹狀結構中的每個項目撰寫特定的程式碼，您會想要建立重複的項目：  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
```  
  
 這個程式碼會進入無限的迴圈。 `foreach` 陳述式會逐一查看 `Elements()` 座標軸，並將新的項目加入到 `doc` 項目。 它也會透過剛才加入的項目結束反覆運算。 而且它會利用迴圈的每次反覆運算配置新物件，因此最終會消耗所有可用的記憶體。  
  
 您可以修正此問題將集合配置到記憶體使用<xref:System.Linq.Enumerable.ToList%2A>標準查詢運算子，如下所示︰</xref:System.Linq.Enumerable.ToList%2A>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    root.Add(New XElement(e.Name, e.Value))  
Next  
Console.WriteLine(root)  
```  
  
 現在，這個程式碼可以運作了。 所產生的 XML 樹狀結構如下所示：  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a>反覆運算時刪除  
 如果您要在特定的層級刪除所有節點，您可能想要撰寫如下的程式碼：  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 不過，這不會執行您想要的動作。 在這個情況下，當您移除第一個項目 A 後，該項目就會從根目錄中所包含的 XML 樹狀結構移除，而負責進行反覆運算之 Elements 方法中的程式碼則找不到下一個項目。  
  
 前一個程式碼會產生下列輸出：  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 解決方案為呼叫<xref:System.Linq.Enumerable.ToList%2A>來具體化集合，如下︰</xref:System.Linq.Enumerable.ToList%2A>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
For Each e As XElement In root.Elements().ToList()  
    e.Remove()  
Next  
Console.WriteLine(root)  
```  
  
 這會產生下列輸出：  
  
```xml  
<Root />  
```  
  
 或者，您可以一起排除反覆運算呼叫<xref:System.Xml.Linq.XElement.RemoveAll%2A>父項目上︰</xref:System.Xml.Linq.XElement.RemoveAll%2A>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
root.RemoveAll()  
Console.WriteLine(root)  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>為什麼 LINQ 無法自動處理這個情況？  
 其中一個方法是，一律將所有項目放入記憶體，而不是進行延遲評估。 不過，關於效能和記憶體使用率，這將會高度耗費資源。 事實上，如果 LINQ 和 (LINQ to XML) 要採取這個方法，在實際的情況下將會失敗。  
  
 另一個可能的方法是將特定類型的交易語法放入 LINQ 中，然後讓編譯器嘗試分析程式碼，並判斷是否需要將任何特定集合具體化。 不過，嘗試判斷具有副作用的所有程式碼相當複雜。 請考慮下列程式碼：  
  
```vb  
Dim z = _  
    From e In root.Elements() _  
    Where (TestSomeCondition(e)) _  
    Select DoMyProjection(e)  
```  
  
 此類分析程式碼必須分析 TestSomeCondition 和 DoMyProjection 方法，而且這些方法呼叫的所有方法都必須判斷任何程式碼是否有副作用。 但是，分析程式碼無法只尋找具有副作用的任何程式碼。 在此情況下，此分析程式碼必須僅針對 `root` 的子項目上，具有副作用的程式碼進行選取。  
  
 LINQ to XML 不會嘗試執行此類分析。  
  
 您可以選擇避免這些問題。  
  
## <a name="guidance"></a>指引  
 首先，請勿混用宣告式與命令性程式碼。  
  
 即使您完全了解集合的語意以及修改 XML 樹狀結構之方法的語意，如果您要撰寫可避免這些類別之問題的聰明程式碼，您的程式碼未來將需要由其他開發人員維護，而且他們對於這些問題可能不是那麼清楚。 如果您混用宣告式與命令性編碼方式，您的程式碼將更不可靠。  
  
 如果您撰寫可具體化集合的程式碼，讓這些問題得以避免，請在程式碼中，以適當的註解方式記錄下來，負責維護的程式設計人員就可以了解這個問題。  
  
 接著，如果效能和其他考量允許，請只使用宣告式程式碼。 請勿修改您現有的 XML 樹狀結構。 產生一個新的 XML 樹狀結構。  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <A>1</A>  
        <B>2</B>  
        <C>3</C>  
    </Root>  
Dim newRoot As XElement = New XElement("Root", _  
    root.Elements(), root.Elements())  
Console.WriteLine(newRoot)  
```  
  
## <a name="see-also"></a>另請參閱  
 [進階的 LINQ to XML 程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

