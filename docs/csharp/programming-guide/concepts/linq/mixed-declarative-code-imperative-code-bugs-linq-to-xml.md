---
title: 混合的宣告式程式碼-命令式程式碼 Bug (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 651b1eddb54f0588ddd3a64927fe79f95671d085
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484244"
---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a>混合的宣告式程式碼/命令式程式碼 Bug (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 包含各種方法，可讓您直接修改 XML 樹狀結構。 您可以加入項目、刪除項目、變更項目的內容、加入屬性等等。 [修改 XML 樹狀結構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md) 會說明這個程式發展介面。 如果您要逐一查看其中一個座標軸 (例如，<xref:System.Xml.Linq.XContainer.Elements%2A>)，而且您要在逐一查看座標軸時修改 XML 樹狀結構，您可以解決一些奇怪的 Bug。  
  
 這種問題有時候稱為「幽靈問題」。  
  
## <a name="definition-of-the-problem"></a>問題的定義  
 當您使用可逐一查看集合的 LINQ 撰寫特定程式碼時，您要以宣告式方法撰寫程式碼。 這比較類似於描述您要的是「什麼」  ，而不是您要「如何」  完成。 如果您撰寫的程式碼可 1) 取得第一個項目、2) 針對某些條件進行測試、3) 加以修改，以及 4) 將其放回清單中，則這會是命令性程式碼。 您是在告訴電腦「如何」  進行您要完成的動作。  
  
 在相同的運算中混用這些程式碼樣式就是導致問題發生的原因。 請考慮下列事項：  
  
 假設您有一個連結的清單，其中包含三個項目 (a、b 和 c)：  
  
 `a -> b -> c`  
  
 現在，假設您要移動連結的清單，以加入三個新項目 (a'、b' 和 c')。 您希望所產生的連結清單如下所示：  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 因此，您可以撰寫逐一查看清單的程式碼，然後針對每個項目，將新項目加入到清單的後面。 結果是，您的程式碼將會先看到 `a` 項目，然後在其後插入 `a'`。 現在，您的程式碼將會移到清單中的下一個節點，而這個節點現在是 `a'`！ 它會將新項目適當地加入到清單 `a''` 中。  
  
 您在現實世界會如何解決這個問題？ 您可以複製原始的連結清單，然後建立一個全新的清單。 或者，如果您要撰寫純命令性程式碼，您可能會找到第一個項目、加入新項目，然後在連結的清單中往前兩次，超過您剛才加入的項目。  
  
## <a name="adding-while-iterating"></a>反覆運算時加入  
 例如，假設您要針對樹狀結構中的每個項目撰寫特定的程式碼，您會想要建立重複的項目：  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 這個程式碼會進入無限的迴圈。 `foreach` 陳述式會逐一查看 `Elements()` 座標軸，並將新的項目加入到 `doc` 項目。 它也會透過剛才加入的項目結束反覆運算。 而且它會利用迴圈的每次反覆運算配置新物件，因此最終會消耗所有可用的記憶體。  
  
 您可以使用 <xref:System.Linq.Enumerable.ToList%2A> 標準查詢運算子將集合配置到記憶體，藉以修正這個問題，如下所示：  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
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
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 不過，這不會執行您想要的動作。 在這個情況下，當您移除第一個項目 A 後，該項目就會從根目錄中所包含的 XML 樹狀結構移除，而負責進行反覆運算之 Elements 方法中的程式碼則找不到下一個項目。  
  
 前一個程式碼會產生下列輸出：  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 解決方案為呼叫 <xref:System.Linq.Enumerable.ToList%2A> 來具體化集合，如下所示：  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 這會產生下列輸出：  
  
```xml  
<Root />  
```  
  
 或者，您可以在父項目上呼叫 <xref:System.Xml.Linq.XElement.RemoveAll%2A>，一起排除反覆運算：  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a>為什麼 LINQ 無法自動處理這個情況？  
 其中一個方法是，一律將所有項目放入記憶體，而不是進行延遲評估。 不過，關於效能和記憶體使用率，這將會高度耗費資源。 事實上，如果 LINQ 和 (LINQ to XML) 要採取這個方法，在實際的情況下將會失敗。  
  
 另一個可能的方法是將特定類型的交易語法放入 LINQ 中，然後讓編譯器嘗試分析程式碼，並判斷是否需要將任何特定集合具體化。 不過，嘗試判斷具有副作用的所有程式碼相當複雜。 請考慮下列程式碼：  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 此類分析程式碼必須分析 TestSomeCondition 和 DoMyProjection 方法，而且這些方法呼叫的所有方法都必須判斷任何程式碼是否有副作用。 但是，分析程式碼無法只尋找具有副作用的任何程式碼。 在此情況下，此分析程式碼必須僅針對 `root` 的子項目上，具有副作用的程式碼進行選取。  
  
 LINQ to XML 不會嘗試執行此類分析。  
  
 您可以選擇避免這些問題。  
  
## <a name="guidance"></a>指引  
 首先，請勿混用宣告式與命令性程式碼。  
  
 即使您完全了解集合的語意以及修改 XML 樹狀結構之方法的語意，如果您要撰寫可避免這些類別之問題的聰明程式碼，您的程式碼未來將需要由其他開發人員維護，而且他們對於這些問題可能不是那麼清楚。 如果您混用宣告式與命令性編碼方式，您的程式碼將更不可靠。  
  
 如果您撰寫可具體化集合的程式碼，讓這些問題得以避免，請在程式碼中，以適當的註解方式記錄下來，負責維護的程式設計人員就可以了解這個問題。  
  
 接著，如果效能和其他考量允許，請只使用宣告式程式碼。 請勿修改您現有的 XML 樹狀結構。 產生一個新的 XML 樹狀結構。  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
 